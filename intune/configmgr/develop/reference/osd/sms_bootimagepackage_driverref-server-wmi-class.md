---
layout: Conceptual
title: SMS_BootImagePackage_DriverRef Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage_driverref-server-wmi-class
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
description: An SMS Provider server class that represents the association between a boot image package and a referenced driver.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 047deff9-0b16-4e88-9802-ecab9ed9a71a
document_version_independent_id: ee510b93-b7e0-507d-4d3f-17f74793f344
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_bootimagepackage_driverref-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_bootimagepackage_driverref-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_bootimagepackage_driverref-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 25a46963-78b8-ea8c-6bf3-8f6847abb080
---

# SMS_BootImagePackage_DriverRef Class - Configuration Manager | Microsoft Learn

The `SMS_BootImagePackage_DriverRef` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the association between a boot image package and a referenced driver.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BootImagePackage_DriverRef : SMS_BaseClass
{
     SInt32 CI_ID;
     String PkgID;
     String SourcePath;
};
```

## Methods

The `SMS_BootImagePackage_DriverRef` class doesn't define any methods.

## Properties

`CI_ID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

The unique ID of the configuration item associated with the [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object. This ID is unique only for the site. The default value is 0.

`PkgID` Data type: `String`

Access type: Read-only

Qualifiers: [read, key]

ID of the boot image package. The default value is "".

`SourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Location of the driver content. The default value is "".

The value of this property is typically the same as the `ContentSourcePath` property for the associated [SMS_Driver Server WMI Class](sms_driver-server-wmi-class) object. However, the value can be different if the original content location isn't available.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    The boot image package is represented by an [SMS_BootImagePackage Server WMI Class](sms_bootimagepackage-server-wmi-class) object. The drivers contained in the package are indicated in the `ReferencedDrivers` property of this object.

    Your application uses this class to determine what drivers are maintained with the boot image.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).