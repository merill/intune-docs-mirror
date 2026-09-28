---
layout: Conceptual
title: SMS_DCMDeploymentErrorDetailsPerAsset Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrordetailsperasset-server-wmi-class
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
description: The SMS_DCMDeploymentErrorDetailsPerAsset WMI class is an SMS Provider server class that represents asset details per asset for a deployment error.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a1adfe16-c548-450d-fe7b-73317cbb7103
document_version_independent_id: 7d894aff-2c22-9eee-4b00-7b60d1b09a6a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrordetailsperasset-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_dcmdeploymenterrordetailsperasset-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_dcmdeploymenterrordetailsperasset-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bc44aa88-a6a6-a507-5268-765bf87c29f8
---

# SMS_DCMDeploymentErrorDetailsPerAsset Class - Configuration Manager | Microsoft Learn

The `SMS_DCMDeploymentErrorDetailsPerAsset` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents asset details per asset for a deployment error.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMDeploymentErrorDetailsPerAsset : SMS_BaseClass
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
    UInt32 ErrorCode;
    String ErrorDescription;
    UInt32 ErrorType;
    String ErrorTypeDisplay;
    UInt32 ItemKey;
    String ObjectDescription;
    UInt32 ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String ObjectTypeName;
    UInt32 Revision;
    String RuleStateDisplay;
    UInt32 StatusType;
    String TargetCollectionID;
    String ValidationRule;
};
```

## Methods

The `SMS_DCMDeploymentErrorDetailsPerAsset` class does not define any methods.

## Properties

`ADUserName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`AssetID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

The ID of the asset.

`AssetType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

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

`ClientType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ClientTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`DeviceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Error code.

`ErrorDescription` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the error.

`ErrorType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Error type. Possible values are:

| Value | Error type |
| --- | --- |
| 1 | INFRASTRUCTURAL |
| 2 | DISCOVERY |
| 3 | CONFLICT |
| 4 | ENFORCEMENT |

`ErrorTypeDisplay` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the error type in the console.

`ItemKey` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

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

Qualifiers: [not\_null, read]

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

`TargetCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

`ValidationRule` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_DCMDeploymentCompliantDetailsPerAsset Server WMI Class](sms_dcmdeploymentcompliantdetailsperasset-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).