---
layout: Conceptual
title: SendNotifySuccessToCTM Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifysuccesstoctm-method
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
description: Learn how to notify the Content Transfer Manager of the success of a job with SentNotifySuccessToCTM method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fb2648fa-fba3-cc94-887c-86d607d198dc
document_version_independent_id: 6f7cd3e3-dcd6-65a2-c1f7-2141c1f2884b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sendnotifysuccesstoctm-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sendnotifysuccesstoctm-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sendnotifysuccesstoctm-method.md
cmProducts: []
platformId: e5b59bfa-4683-2e26-9f8a-51f957a78cbb
---

# SendNotifySuccessToCTM Method - Configuration Manager | Microsoft Learn

The **SendNotifySuccessToCTM** method notifies Content Transfer Manager of the success of a job.

Note

When calling this method, the number of bytes/files transferred (`szBytesTransferred`) should equal the total (`szBytesTotal`).

## Syntax

```
HRESULT stdcall SendNotifySuccessToCTM(
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

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).