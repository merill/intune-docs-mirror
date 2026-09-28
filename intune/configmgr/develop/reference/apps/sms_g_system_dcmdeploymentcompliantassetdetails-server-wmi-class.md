---
layout: Conceptual
title: SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymentcompliantassetdetails-server-wmi-class
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
description: The SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents compliant asset details for a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9d0d0efa-e5dd-b403-8a52-2e5f9f8b470e
document_version_independent_id: 69c2166c-6439-299b-d2c0-90af660962b1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymentcompliantassetdetails-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_g_system_dcmdeploymentcompliantassetdetails-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_g_system_dcmdeploymentcompliantassetdetails-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9e45c12a-86e0-24ae-c7f5-d32222ee7266
---

# SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails Class - Configuration Manager | Microsoft Learn

The `SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents compliant asset details for a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails : SMS_G_System
{
    UInt32 AssignmentID;
    UInt32 BL_ID;
    UInt32 CI_ID;
    UInt32 ResourceID;
    UInt32 Rule_ID;
};
```

## Methods

The `SMS_G_SYSTEM_DCMDeploymentCompliantAssetDetails` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

ID of the configuration item assignment. This ID is unique only for the site.

`BL_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Baseline ID.

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Unique ID of the configuration item. This ID is unique only for the site.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Unique ID, supplied by Configuration Manager, that identifies a client resource. This ID is not unique across sites.

`Rule_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Description of the rule ID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).