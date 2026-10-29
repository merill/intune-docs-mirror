---
layout: Conceptual
title: SMS_InventoryReportClass Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreportclass-server-wmi-class
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
description: The SMS_InventoryReportClass WMI class is an SMS Provider server class embedded in SMS_InventoryReport that represents the classes that are enabled to be collected in this inventory report.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8327ce1b-43ac-33a6-da37-198c2ae453c3
document_version_independent_id: 7356868e-553e-7e37-fbe0-d1ac1f213929
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreportclass-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_inventoryreportclass-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreportclass-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 55e41b85-1493-c42f-90fe-474fdcf55009
---

# SMS_InventoryReportClass Class - Configuration Manager | Microsoft Learn

The `SMS_InventoryReportClass` Windows Management Instrumentation (WMI) class is an SMS Provider server class embedded in `SMS_InventoryReport` that represents the classes that are enabled to be collected in this inventory report.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryReportClass :
{
    String Filter;
    String ReportProperties[];
    String SMSClassID;
    UInt32 Timeout;
};
```

## Methods

The `SMS_InventoryReportClass` class doesn't define any methods.

## Properties

`Filter` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`ReportProperties` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The property name in this class to collect.

`SMSClassID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The class ID that uniquely identifies this class.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The timeout for the query.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).