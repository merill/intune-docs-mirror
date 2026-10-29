---
layout: Conceptual
title: RequestRefresh Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection
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
description: Learn how to trigger a re-evaluation of collection membership by the Configuration Manager collection evaluator component.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 331c2c34-756a-115e-6068-5d5852db01a1
document_version_independent_id: 841737d9-c095-6c03-ce27-a30e153ae1c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: caffdaf4-2a64-b1d3-8591-f0de57036ee8
---

# RequestRefresh Method - Configuration Manager | Microsoft Learn

The `RequestRefresh` Windows Management Instrumentation (WMI) class method, in Configuration Manager, triggers a re-evaluation of collection membership by the Configuration Manager collection evaluator component.

The following syntax is simplified from Managed Object Format (MOF) code and is intended to show the definition of the method.

## Syntax

```
SInt32 RequestRefresh();
```

#### Parameters

Note

The previously available parameter `includesubcollections` has been deprecated in Configuration Manager.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).