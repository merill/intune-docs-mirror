---
layout: Conceptual
title: GetContextHandle Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods
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
description: The GetContextHandle method, in Configuration Manager, stores context objects on the server.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 30ad1b45-7b3a-1998-a247-2cda44a2c333
document_version_independent_id: e4def6cc-bfc6-b9b7-64cf-9a576badff1b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods.md
cmProducts: []
platformId: f50128ad-4e9a-1d35-1fa1-c509768f644a
---

# GetContextHandle Method - Configuration Manager | Microsoft Learn

The `GetContextHandle` method, in Configuration Manager, stores context objects on the server.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetContextHandle(
      String ContextHandle
);
```

#### Parameters

`ContextHandle` Data type: `String`

Qualifiers: [out]

Context handle that identifies the cached context object on the server.

## Return Values

An `SInt32` data type that indicates 0 for success or non-zero for failure.

## Remarks

Use this method to replace the contents of your context object with the object indicated by the retrieved context handle. Storing context object data on the server saves network bandwidth for client applications that repeatedly call the SMS Provider using a large number of context qualifiers or a large amount of qualifier data.

For a complete description of the steps required to use this optimization technique, see the ContextHandle qualifier in [Configuration Manager Context Qualifiers](../../core/understand/context-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).