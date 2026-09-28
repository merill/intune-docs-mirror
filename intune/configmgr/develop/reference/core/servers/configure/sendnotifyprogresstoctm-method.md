---
layout: Conceptual
title: SendNotifyProgressToCTM Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifyprogresstoctm-method
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
description: The SendNotifyProgressToCTM method notifies Content Transfer Manager of the progress of a job.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 686df85f-8f66-a27f-ce7b-3ec51ef0e7af
document_version_independent_id: 3c990011-bb9d-d188-e445-b2a52b78458e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sendnotifyprogresstoctm-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sendnotifyprogresstoctm-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sendnotifyprogresstoctm-method.md
cmProducts: []
platformId: 720f2ee0-3143-6666-3ee8-d45e45c2b25f
---

# SendNotifyProgressToCTM Method - Configuration Manager | Microsoft Learn

The **SendNotifyProgressToCTM** method notifies Content Transfer Manager of the progress of a job.

## Syntax

```
HRESULT stdcall SendNotifyProgressToCTM(
    LPCWSTR szProgressType,
    LPCWSTR szEndpoint,
    LPCWSTR szID,
    LPCWSTR szClientData,
    LPCWSTR szBytesTotal,
    LPCWSTR szBytesTransferred,
    ULONG ulFilesTotal,
    ULONG ulFilesTransferred
);

```

#### Parameters

`szProgressType` Data type: LPCWSTR

Qualifiers: [in]

Either one of the S\_DTS\_\* constants for status changes or NULL/empty string for a bytes progress only.

`szEndpoint` Data type: LPCWSTR

Qualifiers: [in]

The notification endpoint. This was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** (szNotifyEndpoint).

`szID` Data type: UInt32

Qualifiers: [in]

The job to which the notification corresponds. This is the GUID originally returned by **ICcmAlternateDownloadProvider::DownloadContent**.

`szClientData` Data type: LPCWSTR

Qualifiers: [in]

The client-specific data that was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** (szNotifyData).

`szBytesTotal` Data type: LPCWSTR

Qualifiers: [in]

The total number of bytes in the job.

`szBytesTransferred` Data type: LPCWSTR

Qualifiers: [in]

The number of bytes transferred so far.

`ulFilesTotal` Data type: ULONG

Qualifiers: [in]

The total number of files in the job.

`ulFilesTransferred` Data type: ULONG

Qualifiers: [in]

The number of files transferred so far.

## Remarks

If the totals aren't yet known, pass 0 for the values. Once the provider has determined the total byte and file count, those values should be used.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).