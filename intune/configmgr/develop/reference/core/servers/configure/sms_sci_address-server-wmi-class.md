---
layout: Conceptual
title: SMS_SCI_Address Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_address-server-wmi-class
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
description: Learn how to use the SMS_SCI_Address class to represent a sender address, which is a link between the site for which the site control file exists and another site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bfe1e64f-eb41-5ee4-fb31-b00d446852cc
document_version_independent_id: 60341dc7-46f4-3732-5c5e-309a77b2f3da
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_address-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_address-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_address-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 43d48695-cd35-9070-bf73-f735cf6e96ba
---

# SMS_SCI_Address Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_Address` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a sender address, which is a link between the site for which the site control file exists and another site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_Address : SMS_SiteControlItem
{
     UInt32 AddressPriorityOrder;
     String AddressType;
     String DesSiteCode;
     String DesSiteName;
     UInt32 DestinationType;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     SMS_EmbeddedPropertyList PropLists[];
     SMS_EmbeddedProperty Props[];
     UInt32 RateLimitingSchedule[24];
     String SiteCode;
     String SiteName;
     Boolean UnlimitedRateForAll;
     SMS_SiteControlDaySchedule UsageSchedule[7];
};
```

## Methods

The `SMS_SCI_Address` class does not define any methods.

## Properties

`AddressPriorityOrder` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [none]

This property is deprecated.

`AddressType` Data type: `String`

Access type: Read/Write

Qualifiers: [stringnumeration]

This property is deprecated.

`DesSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("3")]

Destination site code with which the sender communicates. The default value is "".

- If `DestinationType` is 0, this value is the destination site code.
- If `DestinationType` is 1, this value is the FQDN of the destination distribution point.

    `DesSiteName` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    Destination site name with which the sender communicates.

    `DestinationType` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: [none]

    Destination site type. Possible values are:

| Value | Destination site type |
| --- | --- |
| 0 | Site server |
| 1 | Distribution point |

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the configuration.

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the configuration.

`RateLimitingSchedule` Data type: `UInt32` Array

Access type: Read/Write

Qualifiers: [lazy]

Array of 24 integers, one for each hour of the day. The values for this 24-hour rate table range from 1 percent to 100 percent. If the `UnlimitedRateForAll` property is `true`, this property contains 100 percent for all 24 elements.

Use the rate-limiting schedule to prevent Configuration Manager from using all available bandwidth on the connection.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`SiteName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`UnlimitedRateForAll` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if unlimited rate is enabled for all senders. If this property is set to `false`, specify a rate schedule for the `RateLimitingSchedule` property. Otherwise, 100 percent is used.

`UsageSchedule` Data type: `SMS_SiteControlDaySchedule` Array

Access type: Read/Write

Qualifiers: None

Usage schedule array of seven [SMS_SiteControlDaySchedule Server WMI Class](sms_sitecontroldayschedule-server-wmi-class) objects, each representing one weekday, for example, 0 for Sunday, 1 for Monday. The schedule is used to control network load during critical time periods by restricting when data can be sent to the address.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

This class is used for inter-site communication by Configuration Manager sender components. For more information, see [Configuration Manager Special Queries](../../../../core/understand/special-queries).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).