---
layout: Conceptual
title: DDRWrite - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrwrite
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
description: The`DDRWrite function, in Configuration Manager, writes the data discovery records (DDRs) to a file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6357bba4-6cad-ef43-ce2e-b42a8dbd37d0
document_version_independent_id: e044168a-1fb9-751f-dee5-f825f083b861
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddrwrite.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddrwrite
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddrwrite.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: cd3c9ebb-1142-4890-7f5f-5726cb993e83
---

# DDRWrite - Configuration Manager | Microsoft Learn

The `DDRWrite` function, in Configuration Manager, writes the data discovery records (DDRs) to a file.

## Syntax

```
[IDL]
HRESULT DDRWrite();
```

#### Parameters

`FileName` Valid Universal Naming Convention (UNC) file name. Use the .ddr file name extension when you specify the file name.

## Return Values

If the function succeeds, the return value is S\_OK.

If the [DDRNew](ddrnew) function hasn't been called or a file error occurs, the return value is S\_FALSE.

## Remarks

Calling `DDRWrite` completes the DDR and writes the record to a binary file. The DDR must be copied to the Data Discovery Manager (DDM) inbox on the site server at a later time (SMS\Inboxes\Auth\Ddm.box).

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).