---
layout: Conceptual
title: ICIINFO::GetContextInfo - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcontextinfo-method
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
description: The ICIINFO::GetContextInfo method, in Configuration Manager, gets the context information by name from the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 19625b9c-83cd-d4eb-67ba-f524c24cc098
document_version_independent_id: f4672e24-0df2-bc07-e351-dc4030785377
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcontextinfo-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getcontextinfo-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcontextinfo-method.md
cmProducts: []
platformId: 957c7e1e-d11f-07fd-23b3-734153200d4a
---

# ICIINFO::GetContextInfo - Configuration Manager | Microsoft Learn

The `ICIINFO::GetContextInfo` method, in Configuration Manager, gets the context information by name from the configuration item.

## Syntax

```
[IDL]
HRESULT GetContextInfo(
     LPCWSTR pszName,
     LPWSTR* ppszContext
);
```

#### Parameters

`pszName` Data type: `LPCWSTR`

Qualifiers: [in]

Pointer to a null-terminated string specifying the name of the context information to retrieve.

`ppszContext` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to a null-terminated string specifying the retrieved context information.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Remarks

This method is used in setting information that is retrieved by certain class handlers in the System Definition Model (SDM) agent.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).