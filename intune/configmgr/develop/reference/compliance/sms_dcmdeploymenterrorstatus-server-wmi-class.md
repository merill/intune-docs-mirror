---
layout: Conceptual
title: SMS_DCMDeploymentErrorStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorstatus-server-wmi-class
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
description: The SMS_DCMDeploymentErrorStatus WMI class is an SMS Provider server class that represents error status for a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 650d2603-023f-8171-8122-4e591d70e1f9
document_version_independent_id: 47261f4e-91bf-d9b9-6424-fc84d41aea2f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_dcmdeploymenterrorstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrorstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cceab1e4-492b-309f-c347-cd285f8e3932
---

# SMS_DCMDeploymentErrorStatus Class - Configuration Manager | Microsoft Learn

The `SMS_DCMDeploymentErrorStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents error status for a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentErrorStatus : SMS_BaseClass
{
    UInt32 Assets;
    UInt32 AssignmentID;
    String AssignmentUniqueID;
    UInt32 BL_ID;
    String BLName;
    UInt32 BLRevision;
    UInt32 CI_ID;
    String CIName;
    DateTime DeploymentTime;
    UInt32 ErrorCode;
    String ErrorDescription;
    UInt32 ErrorType;
    String ErrorTypeDisplay;
    String ObjectDescription;
    UInt32 ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String ObjectTypeName;
    UInt32 Revision;
    String RuleStateDisplay;
    UInt32 StatusType;
    DateTime SummarizationTime;
    UInt32 SummaryType;
    String TargetCollectionID;
};
```

## Methods

The `SMS_DCMDeploymentErrorStatus` class does not define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Count of assets related to the status.

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`BLRevision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`CIName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`DeploymentTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Time of the deployment.

`ErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Error code.

`ErrorDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the error.

`ErrorType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, key, not\_null, read]

Type of error. Possible value are:

| Value | Error type |
| --- | --- |
| 1 | INFRASTRUCTURAL |
| 2 | DISCOVERY |
| 3 | CONFLICT |
| 4 | ENFORCEMENT |

`ErrorTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The description of the error type.

`ObjectDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the object.

`ObjectID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

ID of the object.

`ObjectName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of the object.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, key, not\_null, read]

Object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | CI |
| 2 | SETTING |
| 3 | RULE |

`ObjectTypeName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of the object type.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, key, not\_null, read]

Object type. Possible values are:

| Value | Object type |
| --- | --- |
| 1 | CI |
| 2 | SETTING |
| 3 | RULE |

`Revision` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`RuleStateDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`StatusType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`SummarizationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Time of summarization.

`SummaryType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Type of summary.

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).