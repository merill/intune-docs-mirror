---
layout: Conceptual
title: DDRAddIntegerArray - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray
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
description: The DDRAddIntegerArray function, in Configuration Manager, adds an integer array property to the data discovery record (DDR).
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b301c53c-cda2-6265-0141-8cd041c6f1bd
document_version_independent_id: 5d1fcb07-ffc7-3603-b380-40bac1f36bed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddraddintegerarray
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: ee52620c-1859-0acc-3906-fd474e828bf2
---

# DDRAddIntegerArray - Configuration Manager | Microsoft Learn

The `DDRAddIntegerArray` function, in Configuration Manager, adds an integer array property to the data discovery record (DDR).

## Syntax

```
[IDL]
HRESULT DDRAddIntegerArray();
```

#### Parameters

`Name` Name of the class property.

`Array` Array of integers assigned to the property.

`Flags` Characteristics of the property, such as identifying this property as a key field for comparisons. Enter the following flag or a zero.

| Flag | Description |
| --- | --- |
| ADDPROP\_KEY (Hexadecimal 8) | Identifies this property as a key field during a comparison of this DDR with class instances in the database. If an instance in the database matches the data of the DDR key properties, the instance is updated; otherwise, a new instance is created. |

## Return Values

If the function succeeds, the return value is S\_OK.

If the [DDRNew](ddrnew) function has not been called, the return value is S\_FALSE.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).