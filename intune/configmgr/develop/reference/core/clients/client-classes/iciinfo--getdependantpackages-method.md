---
layout: Conceptual
title: ICIINFO::GetDependantPackages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method
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
description: The ICIINFO::GetDependantPackages method, in Configuration Manager, gets the dependent package information for the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 36e2ab37-e3c6-fc17-01d3-ab7f1347f0e1
document_version_independent_id: d9893054-77cd-7722-7051-a9c1cb386741
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method.md
cmProducts: []
platformId: 2ddd0aa5-0953-0678-177e-b7052a26818f
---

# ICIINFO::GetDependantPackages - Configuration Manager | Microsoft Learn

The `ICIINFO::GetDependantPackages` method, in Configuration Manager, gets the dependent package information for the configuration item.

## Syntax

```
[IDL]
HRESULT GetDependantPackages(
     ULONG* pulNumDependants,
     struct CIPackageInfo** ppInfo
);
```

#### Parameters

`pulNumDependants` Data type: `ULONG`

Qualifiers: [out]

Pointer to the number of dependent packages.

`ppInfo` Data type: `CIPackageInfo`

Qualifiers: [out]

Pointer to a pointer to one [CIPackageInfo Structure](cipackageinfo-structure) for each dependent package.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).