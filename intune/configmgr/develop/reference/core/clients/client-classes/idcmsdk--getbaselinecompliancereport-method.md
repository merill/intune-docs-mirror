---
layout: Conceptual
title: IDCMSDK::GetBaselineComplianceReport - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method
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
description: Learn how to use the IDCMSDK::GetBaselineComplianceReport method to retrieve the cached discovery report for the specified configuration item baseline.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 75e9b6df-de64-01b3-1cc2-b23fa1982dbf
document_version_independent_id: d1576149-6093-cec9-1161-83df717b9248
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method.md
cmProducts: []
platformId: 575b965d-fffb-658f-b492-603a2c270fc4
---

# IDCMSDK::GetBaselineComplianceReport - Configuration Manager | Microsoft Learn

The `IDCMSDK::GetBaselineComplianceReport` method, in Configuration Manager, retrieves the cached discovery report for the specified configuration item baseline.

## Syntax

```
[IDL]
HRESULT GetBaselineComplianceReport(
     LPCWSTR  pszId,
     LPCWSTR  pszVersion,
     LPWSTR*  ppszComplianceInfo
);
```

#### Parameters

`pszId` Data type: `LPCWSTR`

Qualifiers: [in]

Pointer to a null-terminated string specifying the ID of the baseline configuration item. An example ID is "ScopeId\_6CD81FFE-63C4-4AF6-B50A-0847707628A0/Baseline\_780a1633-ba4d-4172-b2b1-583cc733ef56".

`pszVersion` Data type: `LPCWSTR`

Qualifiers: [in, unique]

Pointer to a null-terminated string specifying the baseline configuration item version. If this parameter is set to `null`, the method retrieves the latest version of the baseline configuration item that exists in the client data store.

`ppszComplianceInfo` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to a null-terminated string specifying a report of compliance information for the baseline configuration item.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).