---
layout: Conceptual
title: SMS_DriverContainer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_drivercontainer-server-wmi-class
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
description: In Configuration Manager, the SMS_DriverContainer Windows Management Instrumentation class is an SMS Provider server class that represents boot image or driver package information that refers to the specified driver.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ec993700-e2a7-1f2f-44ef-b53053192731
document_version_independent_id: 90554814-8010-29ce-17ec-1c58c5c78ffa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_drivercontainer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_drivercontainer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_drivercontainer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4a3c4d63-00c9-95d6-03e6-e5041edc86d8
---

# SMS_DriverContainer Class - Configuration Manager | Microsoft Learn

The `SMS_DriverContainer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents boot image or driver package information that refers to the specified driver.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DriverContainer : SMS_BaseClass
{
    UInt32 CI_ID;
    String Name;
    String PackageID;
    UInt32 PackageType;
};
```

## Methods

The `SMS_DriverContainer` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, not\_null, read]

The unique ID of the driver configuration item.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Driver package or boot image name.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Driver package or boot image ID.

`PackageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).