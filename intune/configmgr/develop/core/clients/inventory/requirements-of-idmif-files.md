---
layout: Conceptual
title: Requirements of IDMIF files - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/requirements-of-idmif-files
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
description: Two delta header comments are required for an IDMIF file, the name of the architecture you want to create or modify and a unique ID for the instance.
ms.date: 2017-01-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 4ba49d22-af6f-9281-49d8-e5021f2ac708
document_version_independent_id: d8ff7a68-5da5-9b29-c29a-9270bdb9b50b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/inventory/requirements-of-idmif-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/inventory/requirements-of-idmif-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/inventory/requirements-of-idmif-files.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 71d7b13a-4626-8b2d-e945-e5ba7ea2798d
---

# Requirements of IDMIF files - Configuration Manager | Microsoft Learn

Two delta header comments are required for an IDMIF file. Other comments are optional. The comments you must include are:

- The name of the architecture you want to create or modify: //Architecture&lt;*ArchitectureName*&gt;
- A unique ID for this instance: //UniqueID&lt;*UniqueID*&gt;

The unique ID can be any unique ID. Each architecture has one or more instances within the SMS site database. The unique ID is the key for this specific instance.

Also, although it is not required, you should use the agent name, especially with a large or complicated custom MIF file that might be updated by more than one agent: //AgentID&lt;*AgentName*&gt;

If you do not include this attribute, hardware inventory might overwrite the information your IDMIF file places in the SMS site database.

The agent name enables you to independently create and modify the **System** architecture. Others who modify the architecture can use a different agent name. They can then remove or modify the parts of the architecture that are associated with that agent, independently of the modifications of other agents.

There is another requirement of any IDMIF file. Whenever you create an IDMIF file, you must include a group within the IDMIF file with the same class name as the architecture you are creating or modifying. This group is known as the top-level group.

Also, if you create any class that has more than one instance, you must include at least one key value within the class, to avoid having each instance overwrite previous instances.

Important

The formatting of the comments must be exactly the same as that given here. The only part that you can change is the part in italics. The &lt; and &gt; characters must be included.

IDMIF files must be stored in the following folder on Advanced Clients: *%Windir%\System32\CCM\Inventory\Idmifs*

IDMIF files must be stored in the following folder on Legacy Clients: *%Windir%\MS\SMS\Idmifs*

The safest method on both clients is to use the folder the following registry key points to:

**HKLM\Software\Microsoft\SMS\Client\Configuration\Client Properties\IDMIF Directory**

The following is an example of a simple IDMIF file:

```

//Architecture<System>
//UniqueID<3b93b13a-afb4-40cf-86d4-3ad1aaaa8414>

Start Component
    Name = "Workstation"
    Start Group
        Name = "System"
        ID = 1
        Class = "System"
        Key = 1,2,3
            Start Attribute
                Name = "Name"
                ID = 1
                Access = READ-ONLY
                Storage = Specific
                Type = String(255)
                Value = "MachineName8d16380a-3928-4ef1-b4f3-fdc557d4af9b"
            End Attribute
            Start Attribute
                Name = "SMSID"
                ID = 2
                Access = READ-ONLY
                Storage = Specific
                Type = String(255)
                Value = "8d16380a-3928-4ef1-b4f3-fdc557d4af9b"
            End Attribute
            Start Attribute
                Name = "SystemType"
                ID = 3
                Access = READ-ONLY
                Storage = Specific
                Type = String(255)
                Value = "Test Type"
            End Attribute
    End Group

```

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).