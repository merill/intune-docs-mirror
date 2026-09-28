---
layout: Conceptual
title: Progress Types - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/progress-types
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
description: Progress states for a download. For a non-status change (for example, if there was just transfer of bytes), specify NULL for progress type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: baa6197a-6f0c-0f89-46d8-214bf6bb8b2f
document_version_independent_id: 7fa2237e-1c25-4359-fda6-ec9c949302d1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/progress-types.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/progress-types
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/progress-types.md
cmProducts: []
platformId: 2a320de4-536c-5d50-a497-388e3516e6ec
---

# Progress Types - Configuration Manager | Microsoft Learn

Progress states for a download.

Note

For a non-status change (for example, if there was just transfer of bytes), specify NULL for progress type.

## Syntax

```
//  Progress types:
//******************************************************************************
static const WCHAR S_DTS_PROGRESS_DOWNLOADING_MANIFEST[]    = L"DownloadingManifest";
static const WCHAR S_DTS_PROGRESS_PROCESSING_MANIFEST[]     = L"ProcessingManifest";
static const WCHAR S_DTS_PROGRESS_CREATING_DIRECTORIES[]    = L"CreatingDirectories";
static const WCHAR S_DTS_PROGRESS_PREPARING_DOWNLOAD[]      = L"PreparingDownload";
static const WCHAR S_DTS_PROGRESS_DOWNLOADING_DATA[]        = L"DownloadingData";

```

## Types

| Progress type | Description |
| --- | --- |
| S\_DTS\_PROGRESS\_DOWNLOADING\_MANIFEST | Determining list of files to download. |
| S\_DTS\_PROGRESS\_PROCESSING\_MANIFEST | Processing list of files. |
| S\_DTS\_PROGRESS\_CREATING\_DIRECTORIES | Creating subdirectories based on list of files. |
| S\_DTS\_PROGRESS\_PREPARING\_DOWNLOAD | Manifest processing complete, starting download. |
| S\_DTS\_PROGRESS\_DOWNLOADING\_DATA | Downloading files. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).