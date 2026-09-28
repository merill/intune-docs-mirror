---
layout: Conceptual
title: Create a MOF File for a Custom Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-mof-file-for-a-configuration-manager-custom-action
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
description: A custom task sequence action, its properties and its user interface controls are defined by creating a managed object format (MOF) file to describe the class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 47795f0b-0834-4a83-19d9-52162582abb3
document_version_independent_id: 2d746731-5f0c-5750-84bc-83cc8003b3e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-a-mof-file-for-a-configuration-manager-custom-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-a-mof-file-for-a-configuration-manager-custom-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-a-mof-file-for-a-configuration-manager-custom-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 76951f0f-3660-fb5d-169f-e4c5479d16fc
---

# Create a MOF File for a Custom Action - Configuration Manager | Microsoft Learn

You define a custom task sequence action, its properties and its user interface controls by creating a managed object format (MOF) file to describe the class. The MOF file is then compiled by using Mofcomp.exe.

For more information about custom action MOF files, see [About the Configuration Manager Custom Action MOF File](about-configuration-manager-custom-action-mof-files).

The following procedure adds a class declaration for the custom action that you created in [How to Create a Configuration Manager Custom Action Control](how-to-create-a-configuration-manager-custom-action-control).

For information about using the custom action, see [About Configuration Manager Custom Action Client Applications](about-configuration-manager-custom-action-client-applications).

### To create a MOF file for a custom action

1. In Notepad, create a new file.
2. Add the following MOF code to the file.

    ```
    
    #pragma autorecover
    
    #pragma namespace("\\\\.\\root")
    
    // SMS Root Storage
    instance of __Namespace
    {
        Name = "SMS";
    };
    
    #pragma namespace("\\\\.\\root\\SMS")
    
    // Configuration Manager database name for this computer.
    instance of __Namespace
    {
        Name = "site_REPLACESITECODE";
    };
    
    #pragma namespace("\\\\.\\root\\SMS\\site_REPLACESITECODE")
    
    #pragma classflags("forceupdate")
    
    [   CommandLine("smsswd.exe /run:%1 Application.exe /user:%2"),
        VariablePrefix("MyCustomActionPrefix"),
        ActionCategory("My Custom Action Category,7,1"),
        ActionName{"ConfigMgrTSAction.dll", "ConfigMgrTSAction.Properties.Resources", "ConfigMgrTSAction"},
        ActionUI{"ConfigMgrTSAction.dll", "ConfigMgrTSAction","ConfigMgrTSActionControl",
    "ConfigureTSActionOptions"}
        ]
    class ConfigMgrTSActionControl : SMS_TaskSequence_Action
    {
        [TaskSequencePackage, CommandLineArg(1)]
        string          PackageIDForApplicationExe;
    
        [Not_Null, CommandLineArg(2)]
        string          User;
    
        [VariableName("CustomLocation")]
        string          Location;
    
    };
    ```
3. Replace `REPLACESITECODE` with the site code for your Configuration Manager site.
4. Choose a folder, and save the file as type `All Files` with the name CustomAction.mof.
5. Open a Command Prompt window, navigate to the folder that you saved CustomAction.mof in, and enter the following:

    ```
    mofcomp CustomAction.mof
    ```
6. Press ENTER to compile the CustomAction.mof.
7. Confirm that the class has been added in CIM Studio. The class should be listed as a child class of [SMS_TaskSequence_Action](../reference/osd/sms_tasksequence_action-server-wmi-class).
8. Complete [How to Use a Configuration Manager Custom Action Control](how-to-use-a-configuration-manager-custom-action-control).