---
layout: Conceptual
title: SMS_ClientOperation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_clientoperation-server-wmi-class
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
description: An SMS Provider server class that represents a set of client actions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b5f5091f-9297-72b4-a152-4460f2d6a759
document_version_independent_id: 4035510a-2202-f57c-8592-52c9749efaff
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_clientoperation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_clientoperation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_clientoperation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: badbfee9-c46d-f804-bf36-3bccadf7e648
---

# SMS_ClientOperation Class - Configuration Manager | Microsoft Learn

The `SMS_ClientOperation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a set of client actions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientOperation : SMS_BaseClass
{
    SMS_ClientAction Actions[];
    String CollectionID;
    String CreatedBy;
    UInt32 DependentClientOperations[];
    String Filter;
    UInt32 FilterType;
    UInt32 ID;
    Boolean IsActionsDependent;
    String PrimaryActionTargetObjectID;
    String PrimaryActionTargetObjectName;
    UInt32 PrimaryActionTargetObjectType;
    UInt32 PrimaryActionType;
    UInt32 Priority;
    DateTime RequestedTime;
    String SourceSite;
    UInt32 State;
    String TargetCollectionName;
    UInt32 TargetResourceIDs[];
    UInt32 TargetType;
    String UniqueID;
};
```

## Methods

The following table lists the methods in the `SMS_ClientOperation` class.

| Method | Description |
| --- | --- |
| [AllowThreat Method in Class SMS_ClientOperation](allowthreat-method-in-class-sms_clientoperation) | Allow the specified threat (identified by ID) to all members in a specific collection. |
| [CancelClientOperation Method in Class SMS_ClientOperation](cancelclientoperation-method-in-class-sms_clientoperation) | Cancels a client operation. |
| [DeleteClientOperation Method in Class SMS_ClientOperation](deleteclientoperation-method-in-class-sms_clientoperation) | Deletes a client operation. |
| [ExcludeScanPaths Method in Class SMS_ClientOperation](excludescanpaths-method-in-class-sms_clientoperation) | Excludes scan paths from all members in specified collection. |
| [IsClientOperationAllowed Method in Class SMS_ClientOperation](isclientoperationallowed-method-in-class-sms_clientoperation) | Checks whether a user has permission to execute an operation. |
| [IsClientOperationUpdateAllowed Method in Class SMS_ClientOperation](isclientoperationupdateallowed-method-in-class-sms_clientoperation) | Checks whether a user has permission to update an operation. |
| [InitiateClientOperation Method in Class SMS_ClientOperation](initiateclientoperation-method-in-class-sms_clientoperation) | Initiates a client operation. |
| [RestoreQuarantinedItem Method in Class SMS_ClientOperation](restorequarantineditem-method-in-class-sms_clientoperation) | Restores quarantined items to all members in a collection infected by specified threat. |

## Properties

`Actions` Data type: `SMS_ClientAction` Array

Access type: Read/Write

Qualifiers: [lazy]

A set of embedded client actions to be executed on target clients.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Target collection identifier of this operation.

`CreatedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User who created this operation.

`DependentClientOperations` Data type: `UInt32 Array`

Access type: Read/Write

Qualifiers: [lazy]

Embedded IDs of dependent client operations.

`Filter` Data type: `String`

Access type: Read/Write

Qualifiers: none

Thread identifier filter.

`FilterType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Filter type of the target members, applicable only when the `TargetType` is 3. Possible values are:

| Value | Filter type |
| --- | --- |
| 0 | No filter. |
| 1 | Infected by given threat (Filter). |

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier for this instance.

`IsActionsDependent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the actions within this operation depend on a previous one.

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
| 8 | RequestPolicyNow |

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Operation priority (1 Highest, 50 Lowest).

`RequestedTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Creation time of this operation.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: none

Side code of the site from which the operation was initiated.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Operation state. Possible values are:

| Value | Operation state |
| --- | --- |
| 0 | Inactive |
| 1 | Active |
| 2 | Decommission |

`TargetCollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Target collection name of this operation.

`TargetResourceIDs` Data type: `UInt32 Array`

Access type: Read/Write

Qualifiers: none

The embedded Resource IDs of target clients.

`TargetType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Operation target type. Possible values are:

| Value | Target type |
| --- | --- |
| 0 | Current members of a specified collection. |
| 1 | Specific clients in a specified collection. |
| 2 | Members of a specified collection. |
| 3 | Members of a specific collection matching specified criteria. |

`UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for this instance.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).