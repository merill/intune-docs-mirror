---
layout: Conceptual
title: IDCMAgentCallback::NotifyError - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyerror-method
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
description: Learn how to notify the caller that a Desired Configuration Management Agent job has failed to be completed using IDCMAgentCallback::NotifyError.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 14ea3078-cdb4-1d36-c68e-99be618964a9
document_version_independent_id: 40077af8-ff9b-7dc2-bb5b-96578d4c366a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyerror-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyerror-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyerror-method.md
cmProducts: []
platformId: 76ce1fdf-3db8-5611-d77a-8d78193ab322
---

# IDCMAgentCallback::NotifyError - Configuration Manager | Microsoft Learn

The `IDCMAgentCallback::NotifyError` method, in Configuration Manager, notifies the caller that a Desired Configuration Management Agent job has failed to be completed.

## Syntax

```
[IDL]
HRESULT NotifyError(
     IDCMAgentJob* pJob,
     HRESULT hrError,
     MessageId msgId
);
```

#### Parameters

`pJob` Data type: `IDCMAgentJob`

Qualifiers: [in]

Pointer to the `IDCMAgentJob` object representing the configuration items and their progress.

`hrError` Data type: `HRESULT`

Qualifiers: [in]

`HRESULT` code representing the error.

`msgId` Data type: `MessageId`

Qualifiers: [in]

Nothing is returned for this parameter.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).