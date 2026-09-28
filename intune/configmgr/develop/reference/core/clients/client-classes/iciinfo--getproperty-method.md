---
layout: Conceptual
title: ICIINFO::GetProperty - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getproperty-method
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
description: Learn how the ICIINFO::GetProperty method, in Configuration Manager, gets a named property value from the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: de5da0fc-f21d-abf0-74d5-1990749e8dc8
document_version_independent_id: 817b0584-bebc-8db2-786b-b2c7f7b615f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getproperty-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getproperty-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getproperty-method.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: bba1aaa2-50dc-19f4-b1bf-c5c9b3f7eaca
---

# ICIINFO::GetProperty - Configuration Manager | Microsoft Learn

The `ICIINFO::GetProperty` method, in Configuration Manager, gets a named property value from the configuration item.

## Syntax

```
[IDL]
HRESULT GetProperty(
     LanguageId* pLanguageId,
     LPCWSTR pszPropName,
     LPWSTR* ppszPropValue
);
```

#### Parameters

`pLanguageId` Data type: `LanguageId`

Qualifiers: [in, out]

Pointer to the language ID that is used to obtain the property. If there's no localized name for this ID, the method attempts to obtain the language-independent version of the property. If this doesn't exist, the method returns an error. On successful return from the method, this parameter indicates the language ID for the property retrieved.

`pszPropName` Data type: `LPCWSTR`

Qualifiers: [in]

Pointer to a null-terminated string specifying the name of the property.

`ppszPropValue` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to a null-terminated string specifying the property value.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).