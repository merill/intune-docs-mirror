---
layout: Conceptual
title: SMS_DCMDeploymentCompliantAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantassetdetails-server-wmi-class
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
description: Learn how to represent compliant asset details for a deployment using SMS_DCMDeploymentCompliantAssetDetails class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e4d82ef1-6061-3188-3073-3084fd9bee17
document_version_independent_id: a43bdde5-80d3-f145-5549-4714fe4d246a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 141e6d5b-65fe-56ef-cdaf-3a864d492717
---

# SMS_DCMDeploymentCompliantAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_DCMDeploymentCompliantAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentCompliantAssetDetails : SMS_BaseClass
{
    UInt32 AssetID;
    String AssetName;
    UInt32 AssetType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    UInt32 ClientType;
    Boolean IsMachineAssignedToUser;
    Boolean IsMachineChangesPersisted;
    Boolean IsVM;
    UInt32 Revision;
    UInt32 StatusType;
    String TargetCollectionID;
    String VMHostName;
};
```

## Methods

The `SMS_DCMDeploymentCompliantAssetDetails` class does not define any methods.

## Properties

`AssetID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the asset.

`AssetName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Name of the asset.

`AssetType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

Type of the asset. Possible values are:

| Value | Asset type |
| --- | --- |
| 0 | USER |
| 1 | MACHINE |

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The ID of the configuration item assignment. This ID is unique only for the site.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The unique ID of the configuration item assignment. This ID is unique across sites.

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Identifier of the baseline deployed using this assignment.

`BLName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the baseline deployed using this assignment.

`BLRevision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Baseline version that is deployed using this assignment.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The unique ID of the configuration item. This ID is unique only for the site.

`CIName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the configuration item.

`ClientType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Type of client. Possible values are:

| Value | Client type |
| --- | --- |
| 1 | WINDOWS\_CLIENT |
| 2 | WINDOWS\_MOBILE |

`IsMachineAssignedToUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the computer is assigned to a user.

`IsMachineChangesPersisted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the virtual machine changes are persisted.

`IsVM` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this is a virtual machine.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Revision number for the configuration item.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Status of the deployment to the targeted asset. Possible values are:

| Value | Deployment status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the collection to which the assignment is targeted.

`VMHostName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Virtual machine host name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).