---
layout: Conceptual
title: How to Define the Content Importer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-content-importer
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: To define the application management deployment technology content importer, use an instance of the Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 34941e5f-c369-af90-2a6e-f6862943a0fb
document_version_independent_id: d9425708-82f7-3621-5f66-db48713722bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-content-importer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-content-importer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-content-importer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
platformId: 31b1f521-03bf-d7ff-1d15-152cc8625229
---

# How to Define the Content Importer - Configuration Manager | Microsoft Learn

To define the application management deployment technology content importer, use an instance of the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter` class. The new class instance will define the content importer used by the installer.

The ContentImporter class provides an interface level design where custom technologies can instantiate and populate DeploymentType objects for a specific technology. The concept for this class is that the given technology importer is able read a specific content file and create the corresponding DeploymentType object (with installer) using information obtained from the content. For example, the Windows Installer technology reads \*.msi files and is able to populate Title, Description properties of the DeploymentType object and create the Detect, Install and Uninstall actions for the installer.

In the Remote Desktop Protocol (RDP) sample project, a new content importer is required for Remote Desktop Protocol (RDP) files. Content import support for RDP files is not built-in to Configuration Manager, so a custom content importer is required.

Basic Overview of Defining a Custom Importer

1. Create a custom instance of the ContentImporter class.
2. Override the FileTypes property and return the file types/extensions specific to the technology.
3. Override the CreateDeploymentType method to create a custom deployment type by importing the required properties from a content file.
4. Override the UpdateDeploymentType method to update a custom installer type with the settings from a content file.
5. Helper functions: Include for completeness and to code readability are two helper functions. ProcessFileLine is a helper function called from the UpdateDeploymentType method to process each line of a content file and load the values to custom installer type. ParseType is a helper function called from the ProcessFileLine helper function. The ParseType helper function parses an .rdp file type designation and converts it into a .NET Type.

### To define a custom content importer

1. Create an instance of the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter` class using the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter` constructor.

    The following example from the RDP sample project demonstrates how to define an Content importer.

    ```
    //   Content importer for .rdp files used by the RDP installer.
    public class RdpContentImporter : ContentImporter
    ```
2. Override the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter.FileTypes` property and define the file types supported by the content importer.

    The following example from the RDP sample project demonstrates how to override the FileTypes property.

    ```
    // File types supported by the content importer.
    public override IList<FileType> FileTypes
    {
        get
        {
             return Common.RdpFileTypes;
        }
    }
    ```

    In the RDP sample project, the FileTypes value is defined in the Common class of the project.

    ```
    //   This defines the file extensions supported by this content importer.
    internal static readonly FileType[] RdpFileTypes = new[] { new FileType { Name = "RDP", Description = "Remote Desktop Configuration profile", Extensions = new[] { "rdp" } } };
    ```
3. Override the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter.CreateDeploymentType` method to manage the creation of a custom deployment type by importing the required properties from a content file.

    The following example from the RDP sample project demonstrates how to override the CreateDeploymentType method.

    ```
    // Creates a new deployment type from a content file.
    public override DeploymentType CreateDeploymentType(string contentFile, object context)
    {
        Validator.CheckForNull(contentFile, "contentFile");
        DeploymentType deploymentType = new DeploymentType(Common.TechnologyId) { Title = Path.GetFileNameWithoutExtension(contentFile) };
        UpdateDeploymentType(deploymentType, contentFile);
        return deploymentType;
    }
    ```

    In the RDP sample project, the string parameter for DeploymentType is defined in the Common class of the local project.

    ```
    // Internal ID of the technology.
    public const string TechnologyId = "Rdp";
    ```
4. Override the `Microsoft.ConfigurationManagement.ApplicationManagement.ContentImporter.UpdateDeploymentType` method to update a deployment type with the settings from a content file.

    The following example from the RDP sample project demonstrates how to override the UpdateDeploymentType method.

    ```
    // Updates an existing deployment type installer with settings from content file.
    public override void UpdateDeploymentType(DeploymentType dt, string contentFile, object context)
    {
        Validator.CheckForNull(dt, "dt");
        Validator.CheckForNull(contentFile, "contentFile");
                    RdpInstaller installer = dt.Installer as RdpInstaller;
        if (null == installer)
        {
            throw new ArgumentOutOfRangeException("dt", dt.Installer, @"Installer type is not supported by this content importer.");
        }
        if (false == File.Exists(contentFile))
        {
            throw new FileNotFoundException("Content file was not found: " + contentFile, contentFile);
        }
        string[] fileText = File.ReadAllLines(contentFile);
        fileText.ForEach(l => ProcessFileLine(l, installer));
        installer.Filename = Path.GetFileName(contentFile);
        installer.Contents.Clear();
        installer.Contents.Add(new Content());
        installer.Contents[0].Files.Add(new ContentFile());
        installer.Contents[0].Location = Path.GetDirectoryName(contentFile);
        installer.Contents[0].Files[0].Name = Path.GetFileName(contentFile);
        return;
    }
    ```
5. ProcessFileLine is a helper function called from the UpdateDeploymentType method to process each line of a content file and load the values to custom installer type.

    ```
    //   Processes a line in an .rdp file to set corresponding RdpInstaller properties.
    private static void ProcessFileLine(string line, RdpInstaller installer)
    {
    if (string.IsNullOrEmpty(line))
        {
            Trace.TraceInformation("Skipping line, it is empty.");
            return;
        }
        string[] elements = line.Split(':');
        if (elements.Length < 2)
        {
            Trace.TraceError("Unexpected elements length: {0}. Skipping.", elements.Length);
            return;
        }
        string elementName = elements[0];
        Type elementType = ParseType(elements[1]);
        string elementValueAsString = (elements.Length == 3) ? elements[2] : string.Empty;
        object elementValue = (false == string.IsNullOrEmpty(elementValueAsString)) ? Convert.ChangeType(elementValueAsString, elementType) : null;
        Trace.TraceInformation("Name: {0} Type: {1} Value: {2} ({3})", elementName, elementType, elementValue, elementValueAsString);
        if (string.IsNullOrEmpty(elementValueAsString) || null == elementValue)
        {
            Trace.TraceWarning("Could not parse element value. Skipping.");
            return;
        }
        switch (elementName.ToLowerInvariant())
        {
            case "username":
                installer.Username = elementValueAsString;
                break;
            case "redirectprinters":
                installer.RedirectPrinters = (1 == (int)elementValue);
                break;
            case "redirectsmartcards":
                installer.RedirectSmartCards = (1 == (int)elementValue);
                break;
            case "alternate shell":
                installer.RemoteApplication = elementValueAsString;
                break;
            case "keyboardhook":
                installer.KeyboardMode = (RdpKeyboardMode)(int)elementValue;
                break;
            case "audiomode":
                installer.AudioMode = (RdpAudioMode)(int)elementValue;
                break;
            case "desktopheight":
                installer.DesktopHeight = (int)elementValue;
                break;
            case "desktopwidth":
                installer.DesktopWidth = (int)elementValue;
                break;
            case "full address":
                installer.FullAddress = elementValueAsString;
                string[] tokens = elementValueAsString.Split(':');
                ushort port = 0;
                if (tokens.Length > 1)
                {
                    bool canParse = ushort.TryParse(tokens[1], out port);
                    if (false == canParse)
                    {
                        Trace.TraceError("Improperly formatted port. Skipping.");
                    }
                    installer.RemoteServerPort = port;
                }
                installer.RemoteServerName = tokens[0];
                break;
            case "screen mode id":
                int screenMode = (int)elementValue;
                if (screenMode == 1 || screenMode == 2)
                {
                    installer.FullScreen = (1 == screenMode) ? false : true;
                }
                else
                {
                    Trace.TraceError("Invalid screen mode: {0}. Skipping.", screenMode);
                }
                break;
            default:
                Trace.TraceWarning("Unrecognized property: {0}. Skipping", elementName);
                break;
        }
    }
    ```

    ParseType is a helper function called from the ProcessFileLine helper function. The ParseType helper function parses an .rdp file type designation and converts it into a .NET Type.

    ```
    //   Helper Function: Parses a .rdp file type designation and converts into a .NET Type.
    private static Type ParseType(string type)
    {
    switch (type.ToLowerInvariant())
        {
            case "s":
                return typeof(string);
            case "i":
                return typeof(int);
            case "b":
                return typeof(string);
            default:
                Trace.TraceInformation("Unrecognized type: {0}.", type);
                return typeof(string);
        }
    }
    ```

#### Namespaces

Microsoft.ConfigurationManagement.ApplicationManagement

Microsoft.ConfigurationManagement.ApplicationManagement.Serialization

#### Assemblies

Microsoft.ConfigurationManagement.ApplicationManagement.dll