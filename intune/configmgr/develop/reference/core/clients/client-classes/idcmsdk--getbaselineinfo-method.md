---
layout: Conceptual
title: IDCMSDK::GetBaselineInfo - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselineinfo-method
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
description: Learn how to retrieve the baseline info for the specified configuration item using IDCMSDK::GetBaselineInfo method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 74b610be-d335-d428-be13-7e103b2ba623
document_version_independent_id: 75723abe-821a-a3f2-9d67-c81bee02896d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselineinfo-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselineinfo-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselineinfo-method.md
cmProducts: []
platformId: 9d65e542-283b-f6d2-434f-b1120d84c014
---

# IDCMSDK::GetBaselineInfo - Configuration Manager | Microsoft Learn

The `IDCMSDK::GetBaselineInfo` method, in Configuration Manager, retrieves information for the specified configuration item baseline.

## Syntax

```
[IDL]
HRESULT GetBaselineInfo(
     LPCWSTR  pszId,
     LPCWSTR  pszVersion,
     DWORD  dwFlags,
     ICIInfo**  ppCIInfo
);
```

#### Parameters

`pszId` Data type: `LPCWSTR`

Qualifiers: [in]

Pointer to a null-terminated string specifying the baseline configuration item ID. An example ID is "ScopeId\_6CD81FFE-63C4-4AF6-B50A-0847707628A0/Baseline\_780a1633-ba4d-4172-b2b1-583cc733ef56".

`pszVersion` Data type: `LPCWSTR`

Qualifiers: [in, unique]

Pointer to a null-terminated string specifying the baseline configuration item version. If this parameter is set to NULL, the method retrieves the latest version of the configuration item that exists in the store. Examples of version strings are "1.00" and "27.00".

`dwFlags` Data type: `DWORD`

Qualifiers: [in]

Flags identifying the configuration item. Possible values are:

| Value | dwFlags type and descriptions |
| --- | --- |
| 0 | ciinfoAll. Retrieve all properties. Requires administrator privileges. |
| 1 | ciinfoPublic. Retrieve only public properties. The detailed compliance report isn't a public property. |

`ppCIInfo` Data type: `ICIInfo`

Qualifiers: [out]

Pointer to a pointer to an [ICIINFO Interface](iciinfo-interface) object that represents configuration item information.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).