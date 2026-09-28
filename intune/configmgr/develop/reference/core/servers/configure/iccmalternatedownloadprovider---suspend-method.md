---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider : Suspend - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---suspend-method
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
description: The ICcmAlternateDownloadProvider::Suspend method, in Configuration Manager, instructs the provider to suspend a given job.
ms.date: 2016-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 87e9227f-bd2e-f475-b886-9b41f5fdd4b8
document_version_independent_id: 33300ce3-463b-3bdf-e7c6-3814c9e55979
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---suspend-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---suspend-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---suspend-method.md
cmProducts: []
platformId: 714f5c35-2aa1-a6da-0c4a-6158a2351651
---

# ICcmAlternateDownloadProvider : Suspend - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::Suspend** method, in Configuration Manager, instructs the provider to suspend a given job.

## Syntax

```
HRESULT Suspend(
            REFGUID JobID
    );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job on which to take action.

## Remarks

Note

The provider must support Suspend being called on a job that is suspended. In that case, it should simply do nothing and not report an error. An error should be returned if the job is not found or if suspension failed.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).