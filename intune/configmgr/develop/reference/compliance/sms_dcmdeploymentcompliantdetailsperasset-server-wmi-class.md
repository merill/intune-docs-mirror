---
layout: Conceptual
title: SMS_DCMDeploymentCompliantDetailsPerAsset Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class
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
description: Learn how to use the SMS_DCMDeploymentCompliantDetailsPerAsset class in Configuration Manager set compliant asset details for a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3c576e9a-706a-2ede-f61c-5910c5a7eb23
document_version_independent_id: 803176b2-bd93-6036-2877-165912af8a91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e1c9433a-fe9c-bf56-f550-89822ec46ff7
---

# SMS_DCMDeploymentCompliantDetailsPerAsset Class - Configuration Manager | Microsoft Learn

The `SMS_DCMDeploymentCompliantDetailsPerAsset` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentCompliantDetailsPerAsset : SMS_BaseClass
{
    String ADUserName;
    UInt32 AssetID;
    UInt32 AssetType;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    UInt32 ClientType;
    String ClientTypeDisplay;
    String DeviceName;
    String DiscoveredValue;
    String InstanceData;
    Boolean IsBaselineRule;
    UInt32 ItemKey;
    String PreviousValue;
    UInt32 Revision;
    UInt32 Rule_ID;
    String RuleDescription;
    String RuleName;
    String RuleStateDisplay;
    String RuleSubStateDisplay;
    UInt32 Setting_ID;
    String SettingDescription;
    String SettingName;
    UInt32 StatusType;
    UInt32 SubStatusType;
    String TargetCollectionID;
    String ValidationRule;
};
```

## Methods

The `SMS_DCMDeploymentCompliantDetailsPerAsset` class does not define any methods.

## Properties

`ADUserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Active Directory user name.

`AssetID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the asset.

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

The assignment ID.

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the configuration item assignment. This ID is unique only for the site.

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Baseline database identifier that is deployed using this assignment.

`BLName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Baseline name that is deployed using this assignment.

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

Qualifiers: [enumeration, not\_null, read]

Type of client. Possible values are:

| Value | Client type |
| --- | --- |
| 1 | WINDOWS\_CLIENT |
| 2 | WINDOWS\_MOBILE |

`ClientTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the client type in the console.

`DeviceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the device of the targeted asset.

`DiscoveredValue` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Value of the setting that was discovered and reported when the rule is non-compliant.

`InstanceData` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Discovered path of the instance of the setting being referenced by the non-compliant rule.

`IsBaselineRule` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if this is a baseline rule.

`ItemKey` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Database identifier of the asset being reported for.

`PreviousValue` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Value of the setting discovered during the prior evaluation of the baseline.

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Version of the baseline deployed using this assignment.

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The database identifier of a rule defined in a configuration item.

`RuleDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Descriptive name that identifies the rule.

`RuleName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the rule.

`RuleStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Represents the state of the rule reported by the asset. Possible values are:

| Value |
| --- |
| Compliant |
| Non-compliant |
| Error |
| Conflict |

`RuleSubStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Represents the sub state of the rule reported by the asset. Possible values are:

| Value |
| --- |
| Not-Applicable |
| Not-Detected |

`Setting_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Database identifier of a setting in the configuration item.

`SettingDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of a setting in the configuration item.

`SettingName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of a setting in the configuration item.

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Status of the deployment to the targeted asset. Possible values are:

| Value | Deployment status |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 4 | Unknown |

`SubStatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Substatus type. Possible values are:

| Value | Substatus type |
| --- | --- |
| 0 | Compliant |
| 1 | Not-Applicable |
| 2 | Not-Detected |
| 3 | Enforced |

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the collection to which the assignment is targeted.

`ValidationRule` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The validation criteria defined for the rule in the configuration item.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).