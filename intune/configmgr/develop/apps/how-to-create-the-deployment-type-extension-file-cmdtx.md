---
layout: Conceptual
title: How to Create the Deployment Type Extension File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-create-the-deployment-type-extension-file-cmdtx
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Creating a Deployment Type Extension File is the first step in installing the application management extension files. The application management extension must be installed on each Configuration Manager administrator console computer that will create a custom deployment technology.
locale: en-us
document_id: 2d135534-8820-6ac3-c241-8b32680b7cf0
document_version_independent_id: 543580c4-0fde-c878-c6cd-e6e2b69c0d51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-create-the-deployment-type-extension-file-cmdtx.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-create-the-deployment-type-extension-file-cmdtx
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-create-the-deployment-type-extension-file-cmdtx.md
cmProducts: []
platformId: 7e9fb13b-edeb-03fe-d759-8ba8b821724c
---

# How to Create the Deployment Type Extension File - Configuration Manager | Microsoft Learn

The application management extension must be installed on each Configuration Manager administrator console computer that will create a custom deployment technology. The first step in installing the application management extension files is to create a deployment type extension file (\*.cmdtx).

### To Create the ConfigMgr Deployment Type Extension File (\*.cmdtx)

1. Create an empty directory to stage the contents.
2. Create and copy the following files previously created into the empty directory:

    1. DeploymentTechnology.xml

        Required. A digest of the Deployment Technology
    2. HostingTechnology.xml

        Required. A digest of the Hosting Technology
    3. InstallerTechnology.xml

        Required. A digest of the Installer Technology
    4. The custom SDK Assembly (Microsoft.ConfigurationManagement.ApplicationManagement.{AssemblySuffix}.dll)

        Required. Contains interface implementation of both the Hosting Technology and Installer Technology Note: the AssemblySuffix should correspond to whatever is specified for AssemblySuffix attribute in the DeploymentTechnology.xml file.
    5. HostingApplication.zip

        Optional. Importable application that represents the Hosting Application, which includes content (if any). This should be created using the Export feature on the Applications node, in the Admin Console.
    6. HandlerApplication.zip

        Optional. Importable application that represents the Handler Application for the client, which includes content (if any). This should be created using the Export feature on the Applications node, in the Admin Console.
3. Use the method DeploymentTypeExtender.CreateExtension, which is located in Microsoft.ConfigurationManagement.ApplicationManagement namespace, to create the Deployment Type Extension (\*.cmdtx) file based on the content in the staging directory.

    ```csharp
    // Summarizes progress from CreateExtension method to a log file or the console.
    // <param name="summaryText">Summary text to be presented</param>
    public void Summarize(string summaryText)
    {
          System.Console.WriteLine(summaryText);
          return;
    }
    // Creates a new Deployment Type Extension using the specified source path
    // <param name="sourcePath">Source path used to create the Deployment Type Extension</param>
    // <param name="deploymentTypeExtensionFilePath">Resulting Deployment Type Extension file</param>
    private void CreateDeploymentTypeExtensionFile(string sourcePath, string deploymentTypeExtensionFilePath)
    {
          DeploymentTypeExtender.CreateExtension(sourcePath, deploymentTypeExtensionFilePath, this.Summarize);
          return;
    }
    ```

#### Namespaces

Microsoft.ConfigurationManagement.ApplicationManagement

Microsoft.ConfigurationManagement.ApplicationManagement.Serialization

#### Assemblies

Microsoft.ConfigurationManagement.ApplicationManagement.dll

Microsoft.ConfigurationManagement.ApplicationManagement.Extender.dll