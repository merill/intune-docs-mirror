---
layout: Conceptual
title: IDCMAgentCallback::NotifyProgress - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method
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
description: Learn how to notify the caller of progress made on a Desired Configuration Management Agent job using IDCMAgentCallback::NotifyProgress.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0abd1305-e37c-0c12-7853-ccf17265c279
document_version_independent_id: 307e3f28-09ec-1657-8aa2-864d6e71f2f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method.md
cmProducts: []
platformId: 1a40b185-651c-7969-59f5-25d2f24b92c5
---

# IDCMAgentCallback::NotifyProgress - Configuration Manager | Microsoft Learn

The `IDCMAgentCallback::NotifyProgress` method, in Configuration Manager, notifies the caller of progress made on a Desired Configuration Management Agent job.

## Syntax

```
[IDL]
HRESULT NotifyProgress(
     IDCMAgentJob* pJob,
     MessageId msgId
);
```

#### Parameters

`pJob` Data type: `IDCMAgentJob`

Qualifiers: [in]

Pointer to the `IDCMAgentJob` object representing the configuration items and their progress.

`msgId` Data type: `MessageId`

Qualifiers: [in]

Nothing is returned for this parameter.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).