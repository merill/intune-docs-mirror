---
layout: Conceptual
title: SMS_DeviceSettingPackageItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class
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
description: Learn how the SMS_DeviceSettingPackageItem Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that associates a device setting configuration item with a device setting package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a42d2ea8-1152-4727-1681-8d7d1edd7705
document_version_independent_id: 11db93b8-a96d-2b2d-969c-19e48548b797
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_devicesettingpackageitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4830eaf6-81ff-cbdb-855b-11f0e1f4a959
---

# SMS_DeviceSettingPackageItem Class - Configuration Manager | Microsoft Learn

The `SMS_DeviceSettingPackageItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that associates a device setting configuration item with a device setting package.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceSettingPackageItem : SMS_BaseClass
{
      String DeviceSettingItemUniqueID;
      String PackageID;
};
```

## Methods

The `SMS_DeviceSettingPackageItem` class doesn't define any methods.

## Properties

`DeviceSettingItemUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

GUID or unique ID for the [SMS_DeviceSettingItem Server WMI Class](sms_devicesettingitem-server-wmi-class) object that is contained in the [SMS_DeviceSettingPackage Server WMI Class](sms_devicesettingpackage-server-wmi-class) object represented by `PackageID`. The default value is "".

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

ID of the [SMS_DeviceSettingPackage Server WMI Class](sms_devicesettingpackage-server-wmi-class) object that contains the item represented by `DeviceSettingItemUniqueID`. The default value is "".

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).