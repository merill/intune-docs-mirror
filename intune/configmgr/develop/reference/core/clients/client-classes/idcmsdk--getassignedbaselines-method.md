---
layout: Conceptual
title: IDCMSDK::GetAssignedBaselines - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method
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
description: In Configuration Manager, the IDCMSDK::GetAssignedBaselines method enumerates assigned baseline configuration items.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 85ad9633-8957-f7ee-376d-43e0fbb87996
document_version_independent_id: f6e0767a-ff19-3605-aa1a-159156e6acb1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method.md
cmProducts: []
platformId: 02d3a8b4-d3a7-09f0-8c2e-1c5aa28494ef
---

# IDCMSDK::GetAssignedBaselines - Configuration Manager | Microsoft Learn

The `IDCMSDK::GetAssignedBaselines` method, in Configuration Manager, enumerates assigned baseline configuration items.

## Syntax

```
[IDL]
HRESULT GetAssignedBaselines(
     IEnumUnknown**  ppEnum,
     ULONG*  pulNumCIs,
     struct CIDetectInfo**  ppInfo
);
```

#### Parameters

`ppEnum` Data type: `IEnumUnknown`

Qualifiers: [out]

Pointer to a pointer to an enumeration object containing an [ICIINFO Interface](iciinfo-interface) for each baseline configuration item currently assigned and downloaded to the client.

`pulNumCIs` Data type: `ULONG`

Qualifiers: [out]

Pointer to the number of baseline configuration items. On successful return from the method, this parameter also indicates the number of other configuration items currently assigned to the client.

`ppInfo` Data type: `struct`

Qualifiers: [out, size\_is(,\*pulNumCIs)]

Pointer to a pointer to a [CIDetectInfo Structure](cidetectinfo-structure) containing information for each baseline configuration item that is assigned but not downloaded.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).