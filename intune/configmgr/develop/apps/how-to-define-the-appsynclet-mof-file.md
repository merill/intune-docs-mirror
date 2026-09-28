---
layout: Conceptual
title: How to Define the AppSynclet MOF File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-appsynclet-mof-file
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
description: To define a custom synclet MOF file, create an instance of the CCM_AppHandlers class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0a7fbe52-b644-99f2-1075-ffad6795b424
document_version_independent_id: 397f6fc6-3917-9d2b-4c3d-a9a092d3207b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-appsynclet-mof-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-appsynclet-mof-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-appsynclet-mof-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
platformId: 4ed3ad25-c2ea-44fa-79c6-99da31252b17
---

# How to Define the AppSynclet MOF File - Configuration Manager | Microsoft Learn

To define a custom synclet MOF file, create an instance of the CCM\_AppHandlers class. The new class instance identifies the custom client-side handler. Also, create instances of the CCM\_HandlerSynclet class to store, detect, install and uninstall property values.

The client extension maps closely to the Installer object, defined as part of the DeploymentType. Property values are stored in WMI and the public COM methods in the client-side handler map to detection, installation and uninstallation.

In this example, a new custom synclet MOF file is required for Remote Desktop Protocol (RDP) files. Support for RDP files isn't built in to Configuration Manager, so a custom synclet MOF file is required.

### To define a custom synclet MOF file

1. Create an instance of the `CCM_AppHandlers` class. This class associates the synclet with the custom client-side handler. The HandlerCLSID value is the globally unique identifier that identifies the custom client-side handler's COM object. This, and the other class instances are stored in WMI under root\ccm\cimodels.

    The following example from the RDP sample project demonstrates how to define a custom synclet MOF file.

    ```
    //******************************************************************************
    //
    // The following are the registrations of the Rdp handler
    //
    //******************************************************************************
    instance of CCM_AppHandlers
    {
        HandlerName     = "Rdp";
        HandlerCLSID    = "{4A1FFE05-FEF1-41E3-8DE1-732474E5983D}";
    };
    ```
2. Creates custom instance of the `CCM_HandlerSynclet` class to store the Detect action property values.

    The following example from the RDP sample project demonstrates how to define a custom synclet MOF file.

    ```
    //******************************************************************************
    //
    // Rdp_Detect_Synclet
    //
    //******************************************************************************
    class Rdp_Detect_Synclet : CCM_HandlerSynclet
    {
        [ Not_Null ]
        string      FileName;
    
        [ Not_Null ]
        string      InstallFolder;
    
        [ Not_Null ]
        string      FullAddress;
    
        string      RemoteApplication;
        boolean     RemoteApplicationMode;
    };
    ```
3. Create a custom instance of the `CCM_HandlerSynclet` class to store the Install action property values.

    The following example from the RDP sample project demonstrates how to define a custom synclet MOF file.

    ```
    //******************************************************************************
    //
    // Rdp_Install_Synclet
    //
    //******************************************************************************
    class Rdp_Install_Synclet : CCM_HandlerSynclet
    {
        [ Not_Null ]
        string  Filename;
    
        [ Not_Null ]
        string  InstallFolder;
        sint32  FullScreen;
        sint32  DesktopWidth;
        sint32  DesktopHeight;
        sint32  AudioMode;
        string  FullAddress;
        string  RemoteServerName;
        sint32  RemoteServerPort;
        string  RemoteApplication;
        boolean RemoteApplicationMode;
        boolean ConstructRdpOnClient;
        sint32  KeyboardMode;
        sint32  RedirectPrinters;
        sint32  RedirectSmartCards;
        string  Username;
        string  ContentFilename;
    };
    ```
4. Create a custom instance of the `CCM_HandlerSynclet` class to store the Uninstall action property values.

    The following example from the RDP sample project demonstrates how to define a custom synclet MOF file.

    ```
    //******************************************************************************
    //
    // Rdp_Uninstall_Synclet
    //
    //******************************************************************************
    class Rdp_Uninstall_Synclet : CCM_HandlerSynclet
    {
        [ Not_Null ]
        string  FileName;
    
        [ Not_Null ]
        string  InstallFolder;
    };
    ```