---
layout: Conceptual
title: ImportInventoryReport Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport
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
description: Learn how to import an inventory class from the MOF file content using ImportInventoryReport class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 24be458c-d68b-b5ee-76d9-45ebc5dd64ff
document_version_independent_id: 1d52d949-092a-d312-5330-fa24d931e153
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 25128b40-a138-d621-f629-3f08a790dca2
---

# ImportInventoryReport Method - Configuration Manager | Microsoft Learn

The `ImportInventoryReport` Windows Management Instrumentation (WMI) class method, in Configuration Manager, imports an inventory class from the MOF file content.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
sint32 ImportInventoryReport(
     string InventoryReportID,
     uint32 ImportType,
     string MofBuffer
);
```

#### Parameters

`InventoryReportID` Data type: `String`

Qualifiers: [in]

Inventory report ID.

`ImportType` Data type: `UInt32`

Qualifiers: [in]

Import type. Possible values are:

| Value | Description |
| --- | --- |
| 1 | ClassOnly: Imports only the inventory class. This option is only available at the central site or a standalone primary site. |
| 2 | ReportOnly: Imports only the inventory report. |
| 3 | BothClassAndReport: Imports both inventory class definition and inventory report information. |

`MofBuffer` Data type: `String`

Qualifiers: [in]

The MOF content that contains the inventory class or report to import. This is the same format as the Configuration Manager 2007 sms\_def.mof file, or the file format that you export from inventory client settings.

## Return Values

An `SInt32`data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).