---
layout: Conceptual
title: InsertMultipleResourceIds Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers
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
description: WMI class method, in Configuration Manager, inserts multiple resource IDs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1d702475-a0d6-3183-f452-a05e52442087
document_version_independent_id: 7a1fa9a1-fbc4-9db2-dfc5-3d834a5c3800
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/insertmultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0af668e9-5286-ff15-d5cc-44e290570482
---

# InsertMultipleResourceIds Method - Configuration Manager | Microsoft Learn

The `InsertMultipleResourceIds` Windows Management Instrumentation (WMI) class method, in Configuration Manager, inserts multiple resource IDs.

## Syntax

```
 sint32 InsertMultipleResourceIds(
     UInt32 ResourceIds
);

```

#### Parameters

`ResourceIds` Data type: `UInt32` Array

Qualifiers: [in]

Resource IDs.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).