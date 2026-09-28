---
layout: Conceptual
title: SMS_DeviceSettingItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class
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
description: The SMS_DeviceSettingItem WMI class provides the functionality to create a device setting configuration item in the database.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: af4f9ec6-9ee5-d183-76bb-a82850f39cdf
document_version_independent_id: 9fb61ef7-fbb7-d10e-34db-f5acda480dc5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/sms_devicesettingitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 15205518-d649-c98d-7bca-5d1f0d18b32f
---

# SMS_DeviceSettingItem Class - Configuration Manager | Microsoft Learn

The `SMS_DeviceSettingItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides the functionality to create a device setting configuration item in the database.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceSettingItem : SMS_BaseClass
{
    String Description;
    String DeviceSettingItemUniqueID;
    String Name;
    String PropList;
    String SourceSite;
    String Type;
    UInt32 Version;
};
```

## Methods

The `SMS_DeviceSettingItem` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the device setting to create. The default value is "".

`DeviceSettingItemUniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

A GUID or unique ID that identifies the device setting item to create. The default value is "".

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [unique]

Name of the device setting item to create. The default value is "".

`PropList` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

A list of properties for the device setting item.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code of the site for which to create the device setting item. The default value is "".

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: None

Type of device setting item. The default value is "".

`Version` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The version of the device setting item. The default value is 1.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).