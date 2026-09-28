---
layout: Conceptual
title: ExportDefaultBootImage Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage
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
description: The ExportDefaultBootImage WMI class method finalizes a boot image and then exports the image from the specified source to the specified location.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cedaee6b-a756-199b-5f11-7e3ffbd6f956
document_version_independent_id: 3ed87873-8904-c494-c8ff-64f46bd71a3e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ed875f40-7f47-98e5-95e1-27ac13fe17a7
---

# ExportDefaultBootImage Method - Configuration Manager | Microsoft Learn

The `ExportDefaultBootImage` Windows Management Instrumentation (WMI) class method, in Configuration Manager, finalizes a boot image and then exports the image from the specified source to the specified location.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ExportDefaultBootImage(
     String Architecture,
     UInt32 ImageIndex,
     String ExportImagePath
);
```

#### Parameters

`Architecture` Data type: `String`

Qualifiers: [in]

Operating system architecture of the boot image. Possible values are:

| Value | Architecture |
| --- | --- |
| x86 | I386 32-bit microprocessor |
| ia64 | Itanium 64-bit microprocessor |
| x64 | X86-64 64-bit microprocessor |

`ImageIndex` Data type: `UInt32`

Qualifiers: [in]

The index of the boot image in the Windows Assessment and Deployment Kit source that is used by Configuration Manager setup.

`ExportImagePath` Data type: `String`

Qualifiers: [in]

The destination path of the boot image to export, for example, c:\winPE\boot.wim.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Remarks

Note

Because Configuration Manager uses this method in importing the operating system, be sure to use secure programming techniques in your application or script.

The `ExportDefaultBootImage` method is not thread-safe.

This method finalizes a boot image by adding components or deleting old components to reduce the image size. Each .wim file can contain multiple images, but the export occurs only for the boot image.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).