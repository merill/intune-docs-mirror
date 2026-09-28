---
layout: Conceptual
title: ICIINFO::GetEvalState - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method
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
description: The ICIINFO::GetEvalState method, in Configuration Manager, gets the current evaluation state of the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 94ffbc67-c030-86ae-d65e-94c6dc51a742
document_version_independent_id: b9b4df70-0541-163a-36e9-349753ac0c6d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method.md
cmProducts: []
platformId: 5653c60e-995e-d4bb-d18b-34db13a3294d
---

# ICIINFO::GetEvalState - Configuration Manager | Microsoft Learn

The `ICIINFO::GetEvalState` method, in Configuration Manager, gets the current evaluation state of the configuration item.

## Syntax

```
[IDL]
HRESULT GetEvalState(
     CIEvalState* pCIEvalState
);
```

#### Parameters

`pCIEvalState` Data type: `CIEvalState`

Qualifiers: [out]

Pointer to a [CIEvalState Enumeration](cievalstate-enumeration) value indicating the evaluation state.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).