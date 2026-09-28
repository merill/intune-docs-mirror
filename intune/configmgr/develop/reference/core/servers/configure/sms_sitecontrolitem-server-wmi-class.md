---
layout: Conceptual
title: SMS_SiteControlItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class
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
description: In Configuration Manager, the SMS_SiteControlItem WMI class is an SMS Provider server class that represents the abstract base class for all site control item classes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1ef42ebd-c759-d38d-a952-45ca6ea599bd
document_version_independent_id: 8c8075d7-bf0b-6fa3-b4fc-d1c53d9069ff
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: deb83e8b-86e5-a5c0-b0e2-2201ee2ac0b8
---

# SMS_SiteControlItem Class - Configuration Manager | Microsoft Learn

The `SMS_SiteControlItem` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the abstract base class for all site control item classes.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteControlItem : SMS_BaseClass
{
     UInt32 FileType;
     String ItemName;
     String ItemType;
     String SiteCode;
};
```

## Methods

The `SMS_SiteControlItem` class does not define any methods.

## Properties

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

The property is deprecated.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Unique name identifying the site control item within items of the same type. The default value is "".

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Unique type of the site control item. The default value is "".

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

Unique three-letter site code identifying the site. The default value is "".

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Your application uses classes derived from this class to read and update items in the site control file. These classes are named with the prefix "SMS\_SCI\_". An example of a derived class is [SMS_SCI_Address Server WMI Class](sms_sci_address-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).