---
layout: Conceptual
title: ApproveClients Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/approveclients-method-in-class-sms_collection
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
description: In Configuration Manager, the ApproveClients WMI class method approves specified client computers to join the site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2c0d25ac-fd63-a621-3635-01f88a8e88bb
document_version_independent_id: e0d9289d-3c51-1d1e-e6eb-c6ef0b1cdcf5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/approveclients-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/approveclients-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/approveclients-method-in-class-sms_collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 51532803-36d1-ce11-d32c-c3bca59ed15b
---

# ApproveClients Method - Configuration Manager | Microsoft Learn

The `ApproveClients` Windows Management Instrumentation (WMI) class method, in Configuration Manager, approves specified client computers to join the site.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ApproveClients(
     UInt32 ResourceIDs[],
     Boolean Approved
);
```

#### Parameters

`ResourceIDs` Data type: `UInt32` Array

Qualifiers: [in]

IDs of member resources.

`Approved` Data type: `Boolean`

Qualifiers: [in, optional]

`true` if resources are approved for the site. The default value is true.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).