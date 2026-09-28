---
layout: Conceptual
title: SMS_DriverModel Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_drivermodel-server-wmi-class
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
description: Learn how to represent driver model information for the specified driver in Configuration Manager using SMS_DriverModel class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f1e1091c-09a5-8aa7-6ec7-3ede67179271
document_version_independent_id: 7f48a097-34d2-4655-8a09-d60993b5b97e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_drivermodel-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_drivermodel-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_drivermodel-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 25463693-99bb-e4fd-e0b2-9947dfdc94db
---

# SMS_DriverModel Class - Configuration Manager | Microsoft Learn

The `SMS_DriverModel` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents driver model information for the specified driver.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DriverModel : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    String ModelManufacture;
    String ModelName;
};
```

## Methods

The `SMS_DriverModel` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Driver configuration item local unique ID.

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Driver configuration item global unique ID.

`ModelManufacture` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Driver configuration item Model manufacturer.

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Driver configuration item Model name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).