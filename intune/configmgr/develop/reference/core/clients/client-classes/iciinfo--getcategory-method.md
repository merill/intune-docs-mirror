---
layout: Conceptual
title: ICIINFO::GetCategory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method
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
description: The ICIINFO::GetCategory method gets a localized category name by index and the group name of the category.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 17258ad7-20c3-0625-252a-14f98d0cdab6
document_version_independent_id: 68ebc23a-5fb0-5585-5dda-416eff2d10ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 10bebac0-eac3-a481-e3f5-68f27f9ef8f1
---

# ICIINFO::GetCategory - Configuration Manager | Microsoft Learn

The `ICIINFO::GetCategory` method, in Configuration Manager, gets a localized category name by index and the group name of the category.

## Syntax

```
[IDL]
HRESULT GetCategory(
     ULONG ulIndex,
     LanguageId* pLanguageId,
     LPWSTR* ppszCategoryGroup,
     LPWSTR* ppszCategoryName
);
```

#### Parameters

`ulIndex` Data type: `ULONG`

Qualifiers: [in]

Index of the category to retrieve.

`pLanguageId` Data type: `LanguageId`

Qualifiers: [in, out]

Pointer to a language ID used to obtain the localized category name. If there is no localized name for this ID, the method attempts to obtain the language-independent string. If this does not exist, the method returns an error. On successful return from the method, this parameter indicates the language ID for the localized category name.

`ppszCategoryGroup` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to the category group.

`ppszCategoryName` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to the localized name of the category.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).