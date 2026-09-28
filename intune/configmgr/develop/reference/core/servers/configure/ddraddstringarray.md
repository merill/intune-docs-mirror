---
layout: Conceptual
title: DDRAddStringArray - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how the DDRAddStringArray function, in Configuration Manager, adds a string array property to the data discovery record.
locale: en-us
document_id: b8733e48-d0b9-877b-4558-b75e7dde5fee
document_version_independent_id: cacd1785-88e0-f5b3-801c-43abf00c9fb4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/ddraddstringarray
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: fbba57de-7791-b82a-6966-e5eaf94230e8
---

# DDRAddStringArray - Configuration Manager | Microsoft Learn

The `DDRAddStringArray` function, in Configuration Manager, adds a string array property to the data discovery record (DDR).

## Syntax

```
[IDL]
HRESULT DDRAddStringArray();
```

#### Parameters

`sName` Name of the class property.

`sArray` Array of strings assigned to the property. You can only enter string values from the single-byte character set.

`nArraySize` Number of elements in `sArray`.

`nSQLWidth` Maximum length of a string that can be assigned to this property. This value does not include the NULL character. For SMS 2003, this value cannot be greater than 900 characters. For SMS 2.0, this value cannot be greater than 255 characters.

`dwFlags` Characteristics of the property, such as a key field used for comparisons. Enter the following flag or a zero.

| Flag | Description |
| --- | --- |
| ADDPROP\_KEY (Hexadecimal 8) | Identifies this property as a key field during a comparison of this DDR with class instances in the database. If an instance in the database matches the data of the DDR key properties, the instance is updated; otherwise, a new instance is created. |

## Return Values

If the function succeeds, the return value is S\_OK.

If the [DDRNew](ddrnew) function has not been called, the return value is S\_FALSE.

## Remarks

Strings longer than the maximum length specified in `nSQLWidth` are truncated.

You can use underscores, concatenation, or spaces for property names that contain multiple words. For example, you can specify `sName` as `License_Number`, `LicenseNumber`, or `LicenseNumber`. If you specify `sName` as `LicenseNumber`, the Data Discovery Manager (DDM) concatenates the words, which results in `LicenseNumber`. However, the column name, which is created in the database, is `License_Number`. You must use the same convention when you add DDRs that create or update instances in an existing resource class.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).