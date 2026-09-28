---
layout: Conceptual
title: SMS_ClientOperationStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_clientoperationstatus-server-wmi-class
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
description: In Configuration Manager, the SMS_ClientOperationStatus WMI class is an SMS Provider server class that summarizes the client operation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0d40acce-2e0d-6d73-3e11-655024a03dcf
document_version_independent_id: 715f072b-522e-5432-c944-839c8c90269a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_clientoperationstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_clientoperationstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_clientoperationstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1bd8577a-fb2b-bf8e-f3a6-99a4799dafec
---

# SMS_ClientOperationStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ClientOperationStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that summarizes the client operation.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientOperationStatus : SMS_BaseClass
{
    String CollectionID;
    UInt32 CompletedClients;
    String CreatedBy;
    UInt32 FailedClients;
    UInt32 ID;
    UInt32 IsExpired;
    DateTime LastSummaryTime;
    UInt32 OfflineClients;
    String PrimaryActionTargetObjectID;
    String PrimaryActionTargetObjectName;
    UInt32 PrimaryActionTargetObjectType;
    UInt32 PrimaryActionType;
    UInt32 Priority;
    DateTime RequestedTime;
    UInt32 State;
    String TargetCollectionName;
    DateTime TimeLastUpdated;
    UInt32 TotalClients;
    UInt32 Type;
    String UniqueID;
    UInt32 UnknownClients;
};
```

## Methods

The `SMS_ClientOperationStatus` class does not define any methods.

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Target collection identifier of this operation.

`CompletedClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients that returned a completed result.

`CreatedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User who created this operation.

`FailedClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients that returned a failed result.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier for the client operation.

`IsExpired` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Whether the client operation is expired.

`LastSummaryTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last summary time of the client operation.

`OfflineClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients which are always offline when the client operation is performed.

`PrimaryActionTargetObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Object ID of the target object of the primary action.

`PrimaryActionTargetObjectName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the target object of the primary action.

`PrimaryActionTargetObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Target object type of the primary action. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | Threat |
| 8 | RequestPolicyNow |

`PrimaryActionType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

"Action type of the primary action. Possible values are:

| Value | Action type |
| --- | --- |
| 1 | Full Scan |
| 2 | Quick Scan |
| 3 | Download Definition |
| 4 | Evaluate Software Update |
| 5 | Exclude Scan Path |
| 6 | Override Default Action |
| 7 | Restore Quarantine Items |

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Operation priority (1 highest, 10 lowest).

`RequestedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Creation time of this operation.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

State of this EndPoint Protection client operation. Possible values are:

| Value | State |
| --- | --- |
| 0 | Action Unknown |
| 1 | Action Not Applicable |
| 2 | Action Failed |
| 3 | Action Succeeded |

`TargetCollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Target collection name of this operation.

`TimeLastUpdated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Latest update time of this client operation.

`TotalClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of all clients targeted with this client action.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Operation type.

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for this client operation.

`UnknownClients` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients that have not yet reported any result.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).