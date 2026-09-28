---
layout: Conceptual
title: ICIINFO::GetId - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method
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
description: In Configuration Manager, the ICIINFO::GetId method gets the ID of the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 62137c9f-a9c9-e522-a605-5e7dc1aa8167
document_version_independent_id: cbfc118c-efaa-495a-a5e4-ed254eec0fd6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method.md
cmProducts: []
platformId: 905e77d2-f11d-3de7-7c8b-5f2dc307e0a3
---

# ICIINFO::GetId - Configuration Manager | Microsoft Learn

The `ICIINFO::GetId` method, in Configuration Manager, gets the ID of the configuration item.

## Syntax

```
[IDL]
HRESULT GetId(
    LPWSTR* ppszId
);
```

#### Parameters

`ppszId` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to the ID of the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).