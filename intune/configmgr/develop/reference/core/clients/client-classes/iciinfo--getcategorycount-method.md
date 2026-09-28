---
layout: Conceptual
title: ICIINFO::GetCategoryCount - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method
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
description: Learn how to use the ICIINFO::GetCategoryCount method to get the count of categories that are associated with the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4680faf7-530e-475f-3f43-35d34695962a
document_version_independent_id: e3ae6aae-77b1-d97d-03cb-c9301d56de2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method.md
cmProducts: []
platformId: 1454ea25-bc08-14ac-a6ba-57cf0a370ff2
---

# ICIINFO::GetCategoryCount - Configuration Manager | Microsoft Learn

The `ICIINFO::GetCategoryCount` method, in Configuration Manager, gets the count of categories that are associated with the configuration item.

## Syntax

```
[IDL]
HRESULT GetCategoryCount(
     ULONG* pulCount
);
```

#### Parameters

`pulCount` Data type: `ULONG`

Qualifiers: [out]

Pointer to the count of categories applied to the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).