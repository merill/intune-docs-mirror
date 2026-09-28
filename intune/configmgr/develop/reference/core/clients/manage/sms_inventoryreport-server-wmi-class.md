---
layout: Conceptual
title: SMS_InventoryReport Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreport-server-wmi-class
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
description: The SMS_InventoryReport WMI class is an SMS Provider server class that represents the classes and properties that are enabled to be collected.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0578583d-1db4-711f-d59a-7e317cef6d1a
document_version_independent_id: a26d5a31-4716-9098-87dc-0e1bdb68a6e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreport-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_inventoryreport-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreport-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 222a856e-0ffd-e607-36da-9ed5f0466f34
---

# SMS_InventoryReport Class - Configuration Manager | Microsoft Learn

The `SMS_InventoryReport` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the classes and properties that are enabled to be collected.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryReport : SMS_BaseClass
{
    UInt32 DefaultTimeout;
    String Description;
    String InventoryReportID;
    SMS_InventoryReportClass ReportClasses[];
    UInt32 ReportTimeout;
};
```

## Methods

The following table lists the methods in the `SMS_InventoryReport` class.

| Method | Description |
| --- | --- |
| [ImportInventoryReport Method in Class SMS_InventoryReport](importinventoryreport-method-in-class-sms_inventoryreport) | Imports new inventory classes and enables the collection of existing classes. |

## Properties

`DefaultTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The default timeout of the inventory collection cycle on the client.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The description of the inventory report.

`InventoryReportID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

A GUID that represents the inventory report type.

`ReportClasses` Data type: `Object Array`

Access type: Read/Write

Qualifiers: none

The classes that are enabled for collection in this report.

`ReportTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The timeout of the inventory collection cycle on the client.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).