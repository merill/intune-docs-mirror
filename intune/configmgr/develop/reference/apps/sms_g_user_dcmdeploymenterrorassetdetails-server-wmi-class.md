---
layout: Conceptual
title: SMS_G_USER_DCMDeploymentErrorAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_user_dcmdeploymenterrorassetdetails-server-wmi-class
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
description: Learn how to use the SMS_G_USER_DCMDeploymentErrorAssetDetails class in Configuration Manager to set the asset details for deployment errors.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c86ec892-b26e-bbb9-d29a-ad4e5ee933ee
document_version_independent_id: e261a566-729d-951c-a2ef-6042df5dc20d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_g_user_dcmdeploymenterrorassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_g_user_dcmdeploymenterrorassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_g_user_dcmdeploymenterrorassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ad7fd300-24cd-ac3b-1ccf-34232dc86052
---

# SMS_G_USER_DCMDeploymentErrorAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_G_USER_DCMDeploymentErrorAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the asset details for deployment error.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_USER_DCMDeploymentErrorAssetDetails : SMS_G_User
{
    UInt32 AssignmentID;
    UInt32 BL_ID;
    UInt32 CI_ID;
    UInt32 ErrorCode;
    UInt32 ErrorType;
    UInt32 ObjectID;
    UInt32 ObjectType;
    UInt32 ResourceID;
};
```

## Methods

The `SMS_G_USER_DCMDeploymentErrorAssetDetails` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`ErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`ErrorType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`ObjectID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_DCMDeploymentErrorAssetDetails Server WMI Class](../compliance/sms_dcmdeploymenterrorassetdetails-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).