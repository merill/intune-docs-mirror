---
layout: Conceptual
title: SMS_Driver_Details Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver_details-server-wmi-class
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
description: Learn how to describe the list of drivers that have been added to the boot image with SMS_Driver_Details embedded class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8078a025-9020-2858-cb4d-77c1f3155c7b
document_version_independent_id: 13e7c728-6d1a-03d4-a95c-88c38946342e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_driver_details-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_driver_details-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_driver_details-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f3777f60-0d3c-e4db-aac2-e9fb9400527f
---

# SMS_Driver_Details Class - Configuration Manager | Microsoft Learn

The `SMS_Driver_Details` Windows Management Instrumentation (WMI) class is an embedded class, in Configuration Manager, used by the [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class) class to describe the list of drivers that have been added to the boot image.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Driver_Details
{
      UInt32 ID;
      String SourcePath;
};
```

## Methods

The `SMS_Driver_Details` class does not define any methods.

## Properties

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the driver.

`SourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

The Universal Naming Convention (UNC) path of driver files.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses this class to create objects that are embedded by [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class). For example, the application can add a driver to a boot image package by adding a reference to the required driver in the `ReferencedDrivers` property of an `SMS_BootImagePackage` object. For more information, see How to add a Windows Driver to a Configuration Manager Boot Image Package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).