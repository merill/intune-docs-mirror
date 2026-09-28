---
layout: Conceptual
title: GetFileBinary Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getfilebinary-method-in-class-sms_identification
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
description: Learn how to use the GetFileBinary Method to get the binary user interface for a feature.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0a83c62b-1c0c-e5e4-dec6-851d2e8135ea
document_version_independent_id: 9c93f9ed-4ae0-8a2e-9e48-df752796960f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/getfilebinary-method-in-class-sms_identification.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/getfilebinary-method-in-class-sms_identification
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/getfilebinary-method-in-class-sms_identification.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eb657d70-93f3-22aa-70ec-0556e47022a5
---

# GetFileBinary Method - Configuration Manager | Microsoft Learn

The `GetFileBinary` Windows Management Instrumentation (WMI) class method, in Configuration Manager, gets the binary user interface for a feature. The binary can be separated into multiple blocks starting with number 1. If `isTheLastBlock` equals `False`, then you need call the method again with blockNumber+1 to get the next block.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 GetFileBinary (
    String FileName,
    UInt32 blockNumber,
    String binary64Encoded,
    Boolean isTheLastBlock
);

```

#### Parameters

`FileName` Data type: `String`

Qualifiers: [in]

The name of the file.

`blockNumber` Data type: `UInt32`

Qualifiers: [in]

The block number. To get the next block, call the method again with blockNumber+1, as long as isTheLastBlock equals `False`.

`binary64Encoded` Data type: `String`

Qualifiers: [out]

The binary 64-encoded file.

`isTheLastBlock` Data type: `Boolean`

Qualifiers: [out]

`True` if the current block is the last block; otherwise, `False`. While `False`, you can get the next block by calling the method again with blockNumber+1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).