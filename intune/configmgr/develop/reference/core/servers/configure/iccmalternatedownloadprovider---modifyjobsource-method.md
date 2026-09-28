---
layout: Conceptual
title: 'ICcmAlternateDownloadProvider: ModifyJobSource - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method
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
description: Learn how to instruct the provider to modify the source location for a given job in Configuration Manager.
ms.date: 2017-07-25T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 12b5a32d-6b6c-1a04-00dd-e258e8622b1b
document_version_independent_id: b6841cec-422f-ae18-f064-e49ad53e0361
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method.md
cmProducts: []
platformId: ecc008cb-1fe0-5ee8-a871-cdf00abcdeea
---

# ICcmAlternateDownloadProvider: ModifyJobSource - Configuration Manager | Microsoft Learn

The **ICcmAlternateDownloadProvider::ModifyJobSource** method, in Configuration Manager, instructs the provider to modify the source location for a given job.

## Syntax

```
HRESULT ModifyJobSource(
            REFGUID JobID,
            LPCWSTR szSourceURL,
            DWORD dwFlags
    );

```

#### Parameters

`JobID` Data type: `REFGUID`

Qualifiers: [in]

The job on which to take action.

`szSourceURL` Data type: `LPCWSTR`

Qualifiers: [in]

The new source location.

`dwFlags` Data type: `DWORD`

Qualifiers: [in]

The new job flags. This can be ignored by alternate providers.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Remarks

Note

An error should be returned if the job is not found or if modification of the source location failed or if the provider is using the old location and cannot handle the new location.

If the provider is not using the source location provided in the call to **ICcmAlternateDownloadProvider::DownloadContent** method, it can safely ignore this call, but it should not report an error.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).