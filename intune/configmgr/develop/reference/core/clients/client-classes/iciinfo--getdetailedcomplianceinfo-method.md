---
layout: Conceptual
title: ICIINFO::GetDetailedComplianceInfo - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method
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
description: Learn how the ICIINFO::GetDetailedComplianceInfo method, in Configuration Manager, gets detailed compliance information from the last compliance evaluation run for the configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f5a64939-c109-b2b2-22fd-ba8ad5ab792b
document_version_independent_id: c4f95eb3-70dc-21d4-2a7a-3fb80843b3c0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method.md
cmProducts: []
platformId: 9a686eed-2cde-976d-518b-7bc621fa48a4
---

# ICIINFO::GetDetailedComplianceInfo - Configuration Manager | Microsoft Learn

The `ICIINFO::GetDetailedComplianceInfo` method, in Configuration Manager, gets detailed compliance information from the last compliance evaluation run for the configuration item. The string returned by the method contains an XML report from the last evaluation of the configuration item.

## Syntax

```
[IDL]
HRESULT GetDetailedComplianceInfo(
     LPWSTR* ppszComplianceInfo
);
```

#### Parameters

`ppszComplianceInfo` Data type: `LPWSTR`

Qualifiers: [out]

Pointer to the detailed compliance information.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).