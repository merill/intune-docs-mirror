---
layout: Conceptual
title: ICIINFO::GetJobState - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method
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
description: Learn how to get the current operational state of the configuration item that is part of a job or task with ICIINFO::GetJobState.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 36ad4d23-1976-349c-8e18-d7394e5dab6c
document_version_independent_id: 4dc9aee7-3d08-bed9-9336-a8a1ba12bf06
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method.md
cmProducts: []
platformId: 9cdaa14f-9e60-79d3-23c7-4a0b03a40216
---

# ICIINFO::GetJobState - Configuration Manager | Microsoft Learn

The `ICIINFO::GetJobState` method, in Configuration Manager, gets the current operational state of the configuration item that is part of a job or task.

## Syntax

```
[IDL]
HRESULT GetJobState(
    CIJobState* pCIJobState,
     Percentage* ppctComplete,
     HRESULT* phrStatus
);
```

#### Parameters

`pCIJobState` Data type: `CIJobState`

Qualifiers: [out]

Pointer to a [CIJobState Enumeration](cijobstate-enumeration) value indicating the current operational state of the configuration item. This parameter retrieves ciStatusError if the state is not available.

`ppctComplete` Data type: `Percentage`

Qualifiers: [out]

Pointer to a `Percentage` object indicating the percentage of job completion.

`phrStatus` Data type: `HRESULT`

Qualifiers: [out]

Pointer to an `HRESULT` code representing the current status. This parameter indicates an error code if `pCIJobState` retrieves a value of ciStatusError.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).