---
layout: Conceptual
title: SMS_G_SYSTEM_DCMDeploymentErrorAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymenterrorassetdetails-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that represents the asset details for a deployment error.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1ed67181-0455-04ec-95bf-94b6063b8d55
document_version_independent_id: 5a5bf332-3506-8064-8c14-6d865a0943fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymenterrorassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_g_system_dcmdeploymenterrorassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymenterrorassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 58a61eb3-26cf-2d9c-dc3d-2c92f5900e8c
---

# SMS_G_SYSTEM_DCMDeploymentErrorAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_G_SYSTEM_DCMDeploymentErrorAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the asset details for a deployment error.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_SYSTEM_DCMDeploymentErrorAssetDetails : SMS_G_System
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

The `SMS_G_SYSTEM_DCMDeploymentErrorAssetDetails` class does not define any methods.

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

Unique ID, supplied by Configuration Manager, that identifies a client resource. This ID is not unique across sites.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).