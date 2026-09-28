---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider : Resume - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method
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
description: The ICcmAlternateDownloadProvider::Resume method instructs the provider to resume a given job.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b41bca22-ccb2-a801-0d8f-3d52d253fbd2
document_version_independent_id: 69cbc195-57d4-1f99-df11-4f8cc7171ce4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method.md
cmProducts: []
platformId: 96271ecd-a4f6-ec0b-4e7b-13a1b9ccd594
---

# ICcmAlternateDownloadProvider : Resume - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::Resume** method, in Configuration Manager, instructs the provider to resume a given job.

## Syntax

```
HRESULT Resume(
            REFGUID JobID
    );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job on which to take action.

## Remarks

Note

The provider must support Resume being called on a job that is not suspended. In that case, it should simply do nothing and not report an error. An error should be returned if the job is not found or if resuming failed.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).