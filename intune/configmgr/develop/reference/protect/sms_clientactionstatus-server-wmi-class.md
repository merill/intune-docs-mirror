---
layout: Conceptual
title: SMS_ClientActionStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_clientactionstatus-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that summarize the status of a client action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: feb74b8d-6c0f-21e6-1da8-2bc1c5001d1b
document_version_independent_id: 3d705517-1fc2-9dec-b963-570d43f1709d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_clientactionstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_clientactionstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_clientactionstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e39f6ec3-8861-7f17-673b-cbb61f761c47
---

# SMS_ClientActionStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ClientActionStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that summarize the status of a client action.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientActionStatus : SMS_BaseClass
{
    UInt32 ActionID;
    UInt32 ActionState;
    UInt32 ActionType;
    String ActionUniqueID;
    UInt32 CompletedClients;
    UInt32 FailedClients;
    UInt32 OfflineClients;
    UInt32 OperationID;
    String OperationUniqueID;
    UInt32 State;
    DateTime TimeLastUpdated;
    UInt32 TotalClients;
    UInt32 UnknownClients;
};
```

## Methods

The `SMS_ClientActionStatus` class does not define any methods.

## Properties

`ActionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier for the client action.

`ActionState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

State of the client action. Possible values are:

| Value | Action state |
| --- | --- |
| 0 | Inactive |
| 1 | Active |
| 2 | Decommission |

`ActionType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Action type. Possible values are:

| Value | Action type |
| --- | --- |
| 1 | Full Scan |
| 2 | Quick Scan |
| 3 | Download Definition |
| 4 | Evaluate Software Update |
| 5 | Exclude Scan Path |
| 6 | Override Default Action |
| 7 | Restore Quarantine Items |
| 8 | Request Policy Now |

`ActionUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for the client action.

`CompletedClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients returned completed result.

`FailedClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients returned failed result.

`OfflineClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients which are always offline when the client operation is performed.

`OperationID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the client operation.

`OperationUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier of the client operation.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client operation state.

`TimeLastUpdated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last update time of the client operation.

`TotalClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of all clients targeted with this client action.

`UnknownClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients that have not yet reported any result.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).