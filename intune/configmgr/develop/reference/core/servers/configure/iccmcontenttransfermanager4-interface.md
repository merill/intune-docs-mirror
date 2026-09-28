---
layout: Conceptual
title: ICcmContentTransferManager4 Interface - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmcontenttransfermanager4-interface
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
description: Learn how to invoke the Content Transfer Manager using the ICcmContentTransferManager4 interface and the associated parameters.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 60f1a8c0-51cd-5b99-febe-37394e0e364e
document_version_independent_id: 7f5273a2-a57a-00ba-4ec7-dd717ed91540
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/iccmcontenttransfermanager4-interface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/iccmcontenttransfermanager4-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/iccmcontenttransfermanager4-interface.md
cmProducts: []
platformId: 44415098-58c6-98b8-943a-e2c18f75a33f
---

# ICcmContentTransferManager4 Interface - Configuration Manager | Microsoft Learn

The **ICcmContentTransferManager4** interface is used by clients to invoke the Content Transfer Manager.

## Syntax

```
[
    uuid(4712C69C-F3A1-4DC0-B894-AFFA08738CD2),
    object,
    pointer_default(unique)
]
interface ICcmContentTransferManager4 : IUnknown
{
    HRESULT DownloadContentEx3(
             LPCWSTR szContentId,
             LPCWSTR szContentVersion,
             CCM_CONTENTTYPE eContentType,
             CCM_CONTENTPRIORITY Priority,
             DWORD dwDTSFlags,
             DWORD dwFlags,
             LPCWSTR szOriginalPath,
             LPCWSTR szTempPath
             LPCWSTR szDestPath,
             LPCWSTR szMetaDestPath,
             REFGUID NotifyClsId,
             DWORD dwNotifyKBytes,
             LPCWSTR szOwnerSID,
             DWORD dwLocationTimeout,
             DWORD dwDownloadTimeout,
             DWORD dwPerDPInactivityTimeout,
             DWORD dwTotalInactivityTimeout,
             LPCWSTR szSignatureHash,
             DWORD dwMaxChunkBatchSize,
             LPCWSTR szAltProvSettings,
             GUID *pJobID
        );
}

```

#### Parameters

`szContentId` Data type: LPCWSTR

Qualifiers: [in]

The content/package ID to download.

`szContentVersion` Data type: LPCWSTR

Qualifiers: [in]

The content/package version to download.

`eContentType` Data type: CCM\_CONTENTTYPE

Qualifiers: [in]

The type of content.

`Priority` Data type: CCM\_CONTENTPRIORITY

Qualifiers: [in]

The content priority.

`dwDTSFlags` Data type: DWORD

Qualifiers: [in]

See the CCM\_DTS\_FLAG enumeration.

`dwFlags` Data type: DWORD

Qualifiers: [in]

See the CCM\_CONTENTFLAG enumeration.

`szOriginalPath` Data type: LPCWSTR

Qualifiers: [in, unique]

The previous source directory, may be NULL.

`szTempPath` Data type: LPCWSTR

Qualifiers: [in, unique]

The temporary work directory, may be NULL.

`szDestPath` Data type: LPCWSTR

Qualifiers: [in]

The destination directory.

`szMetaDestPath` Data type: LPCWSTR

Qualifiers: [in, unique]

The destination directory for metadata.

`NotifyClsId` Data type: REFGUID

Qualifiers: [in]

The notification handler CLSID.

`dwNotifyKBytes` Data type: DWORD

Qualifiers: [in]

dwNotifyKBytes

`szOwnerSID` Data type: LPCWSTR

Qualifiers: [in]

The user context in which the download should be performed.

`dwLocationTimeout` Data type: DWORD

Qualifiers: [in]

The location request timeout in seconds.

`dwDownloadTimeout` Data type: DWORD

Qualifiers: [in]

The download request timeout in seconds.

`dwPerDPInactivityTimeout` Data type: DWORD

Qualifiers: [in]

The download inactivity timeout per distribution point in seconds.

`dwTotalInactivityTimeout` Data type: DWORD

Qualifiers: [in]

The total download inactivity timeout in seconds.

`szSignatureHash` Data type: LPCWSTR

Qualifiers: [in, unique]

The hexadecimal encoded hash of signature file for delta download, may be NULL.

`dwMaxChunkBatchSize` Data type: DWORD

Qualifiers: [in]

The maximum number of chunks to download at once.

`szAltProvSettings` Data type: LPCWSTR

Qualifiers: [in, unique]

The XML used to describe allowed alternate download providers and settings for each, may be NULL.

```
<AlternateDownloadSettings SchemaVersion="1.0">
    <Provider Name="logical name here">        <Data>provider specific data here</Data>
    </Provider>
    <Provider Name="logical name here">
        <Data>provider specific data here</Data>
    </Provider>
</AlternateDownloadSettings>

```

`*pJobID` Data type: GUID

Qualifiers: [in]

The job ID which should be used for reference on subsequent calls.

## Return Values

None.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).