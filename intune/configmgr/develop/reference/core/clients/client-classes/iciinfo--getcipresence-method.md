---
layout: Conceptual
title: ICIINFO::GetCIPresence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method
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
description: In Configuration Manager, the ICIINFO::GetCIPresence method gets the current presence for the configuration item, including the compliance state for the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 522fe185-37b1-30f1-fd21-5b1c0c8c4419
document_version_independent_id: 09a3bc18-0dc5-9f9d-d21e-2c67904bc915
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method.md
cmProducts: []
platformId: f967cf17-7532-ec0e-722a-fd9a63d1fe84
---

# ICIINFO::GetCIPresence - Configuration Manager | Microsoft Learn

The `ICIINFO::GetCIPresence` method, in Configuration Manager, gets the current presence for the configuration item. The presence data includes the compliance state for the configuration item.

## Syntax

```
[IDL]
HRESULT GetCIPresence(
     CIPresence* pCIPresence
);
```

#### Parameters

`pCIPresence` Data type: `CIPresence`

Qualifiers: [out]

Pointer to a [CIPresence Enumeration](cipresence-enumeration) value indicating the current presence for the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).