---
layout: Conceptual
title: SMS_G_System_ExtHistory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_exthistory-server-wmi-class
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
description: Learn how to create an abstract base class representing operating system extended history for a client computer using SMS_G_System_ExtHistory.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b17b5651-5d93-3cf1-d2cf-fb3ea358d128
document_version_independent_id: 34fc4430-6de1-e62c-2985-86fb8f54d466
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_exthistory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_exthistory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_exthistory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c1ce4260-a51a-df28-1e7c-a45c645efa96
---

# SMS_G_System_ExtHistory Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_ExtHistory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class representing operating system extended history for a client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_ExtHistory : SMS_G_System
{
     UInt32 GroupID;
     UInt32 ResourceID;
     UInt32 RevisionID;
     DateTime TimeStamp;
};
```

## Methods

The `SMS_G_System_ExtHistory` class does not define any methods.

## Properties

`GroupID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

ID of the group that distinguishes one hardware inventory instance from another within one client resource. For example, each logical disk object for a client is assigned a unique `GroupID` value.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

`RevisionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

ID that increments if the object changes after the last time inventory was taken. The highest number indicates the most recent update. Objects with the same `ResourceID` and `GroupID` values are deltas. They differ from one another by the `RevisionID` number.

`TimeStamp` Data type: `DateTime`

Access type: Read-only

Qualifiers: None

Date and time of the inventory.

## Remarks

Your application uses this class to determine the state of a client at any given time. Names of derived extended history classes are prefixed with "SMS\_GEH\_System\_" followed by the inventoried object name. An example class name is `SMS_GEH_System_ACCOUNT`. Your application can use the derived classes to determine the state of a hardware component on a client at a given point in time.

The SMS Provider determines the state by using the information from classes derived from both [SMS_G_System_Current Server WMI Class](sms_g_system_current-server-wmi-class) and [SMS_G_System_History Server WMI Class](sms_g_system_history-server-wmi-class). However, the application cannot query `SMS_G_System_ExtHistory` to determine the state of all hardware components on a client at a given point in time.

Your query must include the `ResourceID` and `TimeStamp` values in the WHERE clause, as shown in the following example.

```
SELECT * FROM SMS_GEH_System_Logical_Disk
WHERE ResourceID = <resourceid>
AND Timestamp = "<timestamp>"
```

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).