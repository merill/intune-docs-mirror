---
layout: Conceptual
title: LoadIconForPDF Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package
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
description: In Configuration Manager, the LoadIconForPDF Windows Management Instrumentation class method imports a required icon for a package definition file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 68cfce53-717a-edaa-f0a4-1e8acf6ed3f7
document_version_independent_id: a7b74025-c624-c6b8-741f-984e90ab2b5b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3ee12389-ac3c-b03d-0ab0-2afb8dfaff24
---

# LoadIconForPDF Method - Configuration Manager | Microsoft Learn

The `LoadIconForPDF` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports a required icon for a package definition file.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 LoadIconForPDF(
    UInt32 PDFID,
     String IconFileName,
     UInt8 Icon[]
);
```

#### Parameters

`PDFID` Data type: `UInt32`

Qualifiers: [in]

ID of the package definition file to which to add icons. Get this value from the `PDFID` parameter of the [LoadPDF Method in Class SMS_PDF_Package](loadpdf-method-in-class-sms_pdf_package) method.

`IconFileName` Data type: `String`

Qualifiers: [in, SizeLimit("100")]

Full path and file name of a required package definition file icon. Get the icon name from the `RequriedIconNames` parameter of the `LoadPDF` method. Include the path if necessary.

`Icon` Data type: `UInt8` Array

Qualifiers: [in]

Icon to associate with the package.

## Return Values

An `SInt32` data type.

## Remarks

Package definition files can reference icons to be used with the package. These icons are not part of the file and must be loaded separately.

Your application must call `LoadIconForPDF` for every icon that [LoadPDF Method in Class SMS_PDF_Package](loadpdf-method-in-class-sms_pdf_package) loads.

## Example Code

For an example that uses the `LoadIconForPDF` method, see [LoadPDF Method in Class SMS_PDF_Package](loadpdf-method-in-class-sms_pdf_package).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).