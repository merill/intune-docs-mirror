---
layout: Conceptual
title: How to Create the Windows Installer File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-create-the-windows-installer-file-msi
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
description: After the Deployment Type Extension file (*.cmdtx) is created, you're expected to generate a Windows Installer file (\*.msi) which contains the \*.cmdtx file and the UX files.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f82aec4a-7ad3-df83-d687-e6c0743a9959
document_version_independent_id: dc07c1a8-e399-7fe3-ea44-0aefc922d8cb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-create-the-windows-installer-file-msi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-create-the-windows-installer-file-msi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-create-the-windows-installer-file-msi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8e61674d-f160-a388-8433-92603d751e3e
---

# How to Create the Windows Installer File - Configuration Manager | Microsoft Learn

After the Deployment Type Extension file (\*.cmdtx) is created, you're expected to generate a Windows Installer file (\*.msi) which contains the \*.cmdtx file and the UX files. The Windows Installer needs to copy the files into the correct locations and register the custom extension with the site server.

The basic contents of the Windows Installer file are shown below:

![Windows Installer package with embedded files](media/appmanwindowsinstallerpackage.gif)

### To Create the Windows Installer File (\*.msi)

1. Generate a Windows Installer file which contains the \*.cmdtx file, and UX files. The Windows Installer file is responsible for installing the UX files in the correct locations, using the standards defined by the Admin Console team. Basically, this will involve including the following files:

    1. UX Assembly, for example, AdminUI.DeploymentType.&lt;*AssemblySuffix*&gt;.dll

        This file is required and contains the UX implementation, which is then bound to the Configuration Manager console using the below XML files.

        The Installer should copy this file to sms\AdminConsole\bin.
    2. CreateApp\_&lt;*TechnologyID*&gt;.xml

        This file is required and provides the console extension for the Create Application Wizard.

        The Installer should copy this file to sms\AdminConsole\XmlStorage\Extensions\Forms.
    3. CreateDeploymentWizard\_&lt;*TechnologyID*&gt;.xml

        This file is required and provides the console extension for the Create Deployment Type Wizard.

        The Installer should copy this file to sms\AdminConsole\XmlStorage\Extensions\Forms.
    4. &lt;*TechnologyID*&gt;DeploymentTypePropertySheet.xml

        This file is required and provides the Deployment Type property page.

        The Installer should copy this file to sms\AdminConsole\XmlStorage\Forms.
2. The Windows Installer file should contain code to invoke the DeploymentTypeExtender.Extend method, which is located in the Microsoft.ConfigurationManagement.ApplicationManagement namespace. This will then register the extension files for a given site server computer. For an administrator console computer, this initializes the cache for that user. The Extend method call requires the \*.cmdtx file created earlier.

    1. Make a standard WqlConnectionManager connection to the site server.
    2. Call the Extend method, passing the \*cmdtx file, the ConnectionManagerBase object through an instance of ConsoleDcmConnection for the method connection parameter, and the connection path (example below).

    Warning

    In order to use ConsoleDcmConnection, you will need to add an assembly reference to AdminUI.DcmObjectWrapper.dll.

    ```
    using DCM = Microsoft.ConfigurationManagement.AdminConsole.DesiredConfigurationManagement;
    
    [...]
    
        ConnectionManagerBase connectionManager = new WqlConnectionManager();
        connectionManager.Connect("SiteServerName");
    
        DeploymentTypeExtender.Extend(@"C:\RdpTechnology.cmdtx", new  DCM.ConsoleDcmConnection(connectionManager, null), @"\\SiteServerName\root\sms\site_ABC");
    ```
3. Client Installation (HandlerApplication.zip)

    To install the client extension files, either as part of the HandlerApplication or as a separate installation:

    1. Compile the AppSynclet MOF file. On the client, compile the custom synclet MOF file to create the necessary instance of the CCM\_AppHandler class and the corresponding instances of the CCM\_HandlerSynclet classes.

        ```
        C:\> mofcomp appsynclet_<technologyid>
        ```
    2. Copy the handler .dll to the Configuration Manager client directory and register the .dll on the system.

        ```
        C:\> regsvr32 <technologyid>handler.dll
        ```

    Note

    The handler .dll must be compiled to match the operating system – either 32-bit or 64-bit.

#### Namespaces

Microsoft.ConfigurationManagement.ApplicationManagement

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

#### Assemblies

AdminUI.DcmObjectWrapper.dll

AdminUI.WqlQueryEngine.dll

DcmObjectModel.dll

Microsoft.ConfigurationManagement.ApplicationManagement.dll

Microsoft.ConfigurationManagement.ApplicationManagement.Extender.dll

Microsoft.ConfigurationManagement.ManagementProvider.dll