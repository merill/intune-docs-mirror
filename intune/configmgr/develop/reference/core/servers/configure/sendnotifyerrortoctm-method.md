---
layout: Conceptual
title: SendNotifyErrorToCTM Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sendnotifyerrortoctm-method
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
description: Learn how to notify Content Transfer Manager of errors using the SendNotifyErrorToCTM method, in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f94a6119-2e6f-c1f8-853f-03c3b5babd0b
document_version_independent_id: 0f75be2c-b9f4-bbf0-c679-16afb0173b23
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sendnotifyerrortoctm-method.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sendnotifyerrortoctm-method
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sendnotifyerrortoctm-method.md
cmProducts: []
platformId: f3976a48-f550-2e7a-3ad1-c6175bd95fbb
---

# SendNotifyErrorToCTM Method - Configuration Manager | Microsoft Learn

The **SendNotifyErrorToCTM** method, in Configuration Manager, notifies Content Transfer Manager of errors.

## Syntax

```
HRESULT stdcall SendNotifyErrorToCTM(
    LPCWSTR szEndpoint,
    LPCWSTR szID,
    LPCWSTR szClientData,
    HRESULT hrErrorCode,
    LPCWSTR szErrorMessage
);

```

#### Parameters

`szEndpoint` Data type: LPCWSTR

Qualifiers: [in]

The notification endpoint. This was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** (szNotifyEndpoint).

`szID` Data type: LPCWSTR

Qualifiers: [in]

The job to which the notification corresponds. This is the GUID originally returned by **ICcmAlternateDownloadProvider::DownloadContent**.

`szClientData` Data type: LPCWSTR

Qualifiers: [in]

The client-specific data that was passed into the call to **ICcmAlternateDownloadProvider::DownloadContent** (szNotifyData.)

`hrErrorCode` Data type: HRESULT

Qualifiers: [in]

The failure code to report.

`szErrorMessage` Data type: LPCWSTR

Qualifiers: [in]

An extended status message. Must not be NULL.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).