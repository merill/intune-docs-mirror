---
layout: Conceptual
title: DDRAddInteger - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddinteger
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
description: Learn how to add an integer property to the data discovery record (DDR) using DDRAddInteger function.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a334b8c5-a980-1343-5635-debc8a148eef
document_version_independent_id: 6331dfc0-774c-7b26-f030-4d5c0dcf7cdd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddraddinteger.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddraddinteger
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddraddinteger.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: d6b326ce-ae0b-0784-7f8b-8c0965d99f8d
---

# DDRAddInteger - Configuration Manager | Microsoft Learn

The `DDRAddInteger` function, in Configuration Manager, adds an integer property to the data discovery record (DDR).

## Syntax

```
[IDL]
HRESULT DDRAddInteger();
```

#### Parameters

`Name` Name of the class property.

`Value` Value assigned to the property.

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