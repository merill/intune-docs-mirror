---
layout: Conceptual
title: ClearContextHandle Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods
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
description: The ClearContextHandle method clears cached context data associated with the specified context handle.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 070cbacc-426f-f48f-58da-80cf3fb6c431
document_version_independent_id: 186f25dd-f248-92c2-0e8d-392fad3a5607
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods.md
cmProducts: []
platformId: 27ecbe4c-36df-f32c-3397-4c4acb23659e
---

# ClearContextHandle Method - Configuration Manager | Microsoft Learn

The `ClearContextHandle` method, in Configuration Manager, clears cached context data that is associated with the specified context handle.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ClearContextHandle(
   String ContextHandle
);
```

## Parameter

`ContextHandle` Data type: `String`

Qualifiers: [in]

Context handle resulting from a call to the [GetContextHandle Method in Class SMS_ContextMethods](getcontexthandle-method-in-class-sms_contextmethods).

## Return Values

An `SInt32` data type that indicates 0 for success, or non-zero for failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).