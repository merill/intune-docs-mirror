---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider : CancelJob - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method
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
description: Learn how to cancel a job in Configuration Manager using ICcmAlternateDownloadProvider::CancelJob method.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1c1f6ed4-0318-cc8b-c131-b0fc9704e506
document_version_independent_id: 5bc16c4e-5130-c8a3-a7fd-26a60ff4cc63
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method.md
cmProducts: []
platformId: 8ff84fd5-b03f-bd69-299c-d2f0f4c1cc4e
---

# ICcmAlternateDownloadProvider : CancelJob - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::CancelJob** method, in Configuration Manager, cancels a job.

Note

An error should be returned if the job is not found or if cancellation failed.

## Syntax

```
HRESULT CancelJob(
            REFGUID JobID
    );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job upon which to take action.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).