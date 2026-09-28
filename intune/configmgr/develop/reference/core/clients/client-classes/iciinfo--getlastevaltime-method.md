---
layout: Conceptual
title: ICIINFO::GetLastEvalTime - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method
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
description: In Configuration Manager, the ICIINFO::GetLastEvalTime method gets the last evaluation time for the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b0008622-6e09-146a-4b08-ce087e23b5f0
document_version_independent_id: 4c6daba0-4c9a-acee-43de-ebdae6e3df50
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method.md
cmProducts: []
platformId: 6af6d094-2065-01bb-c6eb-a9c09352887b
---

# ICIINFO::GetLastEvalTime - Configuration Manager | Microsoft Learn

The `ICIINFO::GetLastEvalTime` method, in Configuration Manager, gets the last evaluation time for the configuration item.

## Syntax

```
[IDL]
HRESULT GetLastEvalTime(
     SYSTEMTIME* pstEvalTime
);
```

#### Parameters

`pstEvalTime` Data type: `SYSTEMTIME`

Qualifiers: [out]

Pointer to a `SYSTEMTIME` object indicating the last evaluation time.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).