---
layout: Conceptual
title: MoveFolders Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/movefolders-method-in-class-sms_objectcontainernode
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
description: Learn how the MoveFolders Windows Management (WMI) class method, in Configuration Manager, moves folders to another folder location.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: df0412e6-4a21-e0d1-a652-b69314d517b2
document_version_independent_id: b2f6e4e2-8b7e-ae95-f32a-906a29ee1ba6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/movefolders-method-in-class-sms_objectcontainernode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/movefolders-method-in-class-sms_objectcontainernode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/movefolders-method-in-class-sms_objectcontainernode.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 00fddf19-57c4-4eb5-a7b6-cd5baf7e4116
---

# MoveFolders Method - Configuration Manager | Microsoft Learn

The `MoveFolders` Windows Management (WMI) class method, in Configuration Manager, moves folders to another folder location.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 MoveFolders(
      UInt32 ContainerNodeIDs[],
      UInt32 TargetContainerNodeID,
);
```

#### Parameters

`ContainerNodeIDs` Data type: `UInt32` Array

Qualifiers: [in]

IDs of the folders, or nodes, to move.

`TargetContainerNodeID` Data type: `UInt32`

Qualifiers: [in]

The ID for the destination folder, or node.

## Return Value

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).