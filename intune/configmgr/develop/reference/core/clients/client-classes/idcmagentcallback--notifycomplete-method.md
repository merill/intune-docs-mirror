---
layout: Conceptual
title: IDCMAgentCallback::NotifyComplete - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method
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
description: The IDCMAgentCallback::NotifyComplete method, in Configuration Manager, notifies the caller that a Desired Configuration Management Agent job has completed.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: de0b4a6b-6df3-8960-1404-4e3f89134ca0
document_version_independent_id: 56e62225-bf10-c151-cf42-a769cc8fdf40
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method.md
cmProducts: []
platformId: fbe51007-3672-1e8a-5705-a3981c1533fc
---

# IDCMAgentCallback::NotifyComplete - Configuration Manager | Microsoft Learn

The `IDCMAgentCallback::NotifyComplete` method, in Configuration Manager, notifies the caller that a Desired Configuration Management Agent job has completed.

## Syntax

```
[IDL]
HRESULT NotifyComplete(
     IDCMAgentJob* pJob
);
```

#### Parameters

`pJob` Data type: `IDCMAgentJob`

Qualifiers: [in]

Pointer to the `IDCMAgentJob` object representing the configuration items and their progress.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).