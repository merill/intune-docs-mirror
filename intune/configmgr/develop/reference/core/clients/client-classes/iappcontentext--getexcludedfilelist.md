---
layout: Conceptual
title: IAppContentExt::GetExcludedFileList - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappcontentext--getexcludedfilelist
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
description: Learn how to get the excluded file list for application content used to support selective file download with IAppContentExt::GetExcludedFileList method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: af4865bf-eb96-290d-e4f7-1380e1e4e0cd
document_version_independent_id: d64dcc30-5d33-cb45-a6fc-f09e64a8aaec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/iappcontentext--getexcludedfilelist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/iappcontentext--getexcludedfilelist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/iappcontentext--getexcludedfilelist.md
cmProducts: []
platformId: 48e6ba39-93dd-5a27-87f4-97d7bd912cdc
---

# IAppContentExt::GetExcludedFileList - Configuration Manager | Microsoft Learn

The `IAppContentExt::GetExcludedFileList` method, in Configuration Manager, gets the excluded file list for application content. This is used to support selective file download.

## Syntax

```
[IDL]
HRESULT GetExcludedFileList(
     IWbemClassObject* pHandlerSynclet,
     LPWSTR* pwszExcludedFileList,
     BOOL* pbForceFileExclusion
);
```

#### Parameters

`*pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: [in]

.

`pwszExcludedFileList` Data type: `LPWSTR`

Qualifiers: [out]

The exclude file list is a single string separated by the ':' character. For example, "File1.txt:File2.exe."

`pbForceFileExclusion` Data type: `BOOL`

Qualifiers: [out]

`True` to force exclusion of files. If `False`, content framework decides whether or not excluding them based on network condition and content configuration.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).