---
layout: Conceptual
title: IDCMSDK::EvaluateBaseline - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method
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
description: The IDCMSDK::EvaluateBaseline method, in Configuration Manager, runs the discover operation for the specified baseline configuration item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: eeeebc0a-c05c-de32-2e51-93e9484c8bc5
document_version_independent_id: 3d248419-7bd8-22b3-62ea-5f9fcffda86b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--evaluatebaseline-method.md
cmProducts: []
platformId: 57b1592d-130e-516f-f097-e17f06fe4afc
---

# IDCMSDK::EvaluateBaseline - Configuration Manager | Microsoft Learn

The `IDCMSDK::EvaluateBaseline` method, in Configuration Manager, runs the discover operation for the specified baseline configuration item.

## Syntax

```
[IDL]
HRESULT EvaluateBaseline(
     const struct CIDetectInfo* pInfo,
     IDCMAgentCallback*  pCallback,
     BOOL  bForce,
     JobId*  pJobId
);
```

#### Parameters

`pInfo` Data type: `struct`

Qualifiers: [in]

Pointer to a [CIDetectInfo Structure](cidetectinfo-structure) containing information about the baseline configuration item.

`pCallback` Data type: `IDCMAgentCallback`

Qualifiers: [in]

Pointer to an [IDCMAgentCallback Interface](idcmagentcallback-interface) object that is used to notify the agent of the progress, completion, or failure of the operation.

`bForce` Data type: `BOOL`

Qualifiers: [in]

`true` if the method is to force the evaluation scan of the baseline configuration item. This value requires administrator privileges.

A setting of `false` for this parameter allows the scan to run, but it doesn't run if the last evaluation of the baseline met the Desired Configuration Management TimeToLive threshold.

`pJobId` Data type: `JobId`

Qualifiers: [out]

Pointer to the ID of the new Desired Configuration Management Agent job for the baseline configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).