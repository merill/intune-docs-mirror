---
layout: Conceptual
title: IDCMSDK::SetEvaluationCallback - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method
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
description: In Configuration Manager, the IDCMSDK::SetEvaluationCallback method associates a callback object with an existing evaluation job specified by job ID.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8f4ede0d-d508-2546-7e56-a44076367fa4
document_version_independent_id: 7d8e604d-565a-5f20-c254-fcd83e231d52
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--setevaluationcallback-method.md
cmProducts: []
platformId: 0ee487ac-eb38-6c6a-c1b7-3f38ebf6c6f0
---

# IDCMSDK::SetEvaluationCallback - Configuration Manager | Microsoft Learn

The `IDCMSDK::SetEvaluationCallback` method, in Configuration Manager, associates a callback object with an existing evaluation job, specified by job ID.

## Syntax

```
[IDL]
HRESULT SetEvaluationCallback(
     JobIdRef  jobId,
     IDCMAgentCallback*  pCallback
);
```

#### Parameters

`jobId` Data type: `JobIdRef`

Qualifiers: [in]

ID of the evaluation job to retrieve.

`pCallback` Data type: `IDCMAgentCallback`

Qualifiers: [in]

Pointer to an [IDCMAgentCallback Interface](idcmagentcallback-interface) object. This parameter can be set to `null` if no callback is available.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Remarks

The typical way to use this method is to pass `null` for the `pCallback` parameter.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).