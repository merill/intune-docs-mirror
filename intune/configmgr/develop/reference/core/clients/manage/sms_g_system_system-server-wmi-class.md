---
layout: Conceptual
title: SMS_G_System_SYSTEM Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_system-server-wmi-class
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
description: Learn how to represent information about hardware inventory related to a client computer operating system with SMS_G_System_SYSTEM.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7496910c-a164-7577-cd29-0228a1ac6321
document_version_independent_id: d6dd6462-f73f-dff2-c161-8abc5624242f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_system-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_system-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_system-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a18ccda-1c55-ac36-bd50-3bebb4817c4d
---

# SMS_G_System_SYSTEM Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_SYSTEM` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains information about hardware inventory related to a client computer operating system.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_SYSTEM : SMS_G_System_Current
{
     String Domain;
     UInt32 GroupID;
     String Name;
     UInt32 ResourceID;
     UInt32 RevisionID;
     String SMSID;
     String SystemRole;
     String SystemType;
     DateTime TimeStamp;
};
```

## Methods

The `SMS_G_System_SYSTEM` class does not define any methods.

## Properties

`Domain` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the Windows NT domain to which the operating system account belongs.

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the client computer.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`SMSID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Unique Configuration Manager ID of the client.

`SystemRole` Data type: `String`

Access type: Read/Write

Qualifiers: None

The system role played by the computer operating system. Possible values are:

- Workstation
- Server

    `SystemType` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Description of the operating system, for example, "X86-based PC".

    `TimeStamp` Data type: `DateTime`

    Access type: Read/Write

    Qualifiers: None

    See [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class).

    For this class, the default value of this property is `null`.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

This class was added in SMS 2.0 Service Pack 1. It does not have a Win32 class equivalent.