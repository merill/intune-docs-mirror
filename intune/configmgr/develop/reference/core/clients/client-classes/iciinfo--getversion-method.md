---
layout: Conceptual
title: ICIINFO::GetVersion - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getversion-method
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
description: Learn how to use the ICIIINFO::GetVersion method to get the version of the configuration item in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c78fec69-1f76-25f2-5533-6c38d3c9eee2
document_version_independent_id: becfe3fd-3cd9-eaf1-c684-8dd795fabb79
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getversion-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getversion-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getversion-method.md
cmProducts: []
platformId: 16c30888-53d4-42e4-972c-c404242e752d
---

# ICIINFO::GetVersion - Configuration Manager | Microsoft Learn

The `ICIINFO::GetVersion` method, in Configuration Manager, gets the version of the configuration item.

## Syntax

```
[IDL]
HRESULT GetVersion(
     LPWSTR* ppszVersion
);
```

#### Parameters

`ppszVersion` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to the version of the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).