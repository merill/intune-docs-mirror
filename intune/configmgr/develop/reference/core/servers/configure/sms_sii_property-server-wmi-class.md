---
layout: Conceptual
title: SMS_SII_Property Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class
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
description: In Configuration Manager, the SMS_SII_Property WMI class is an SMS Provider server class that represents a general-purpose storage object for property data that can be represented as a single integer or two strings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 96d1d67c-5ae5-71c9-d3dd-fd9bde312119
document_version_independent_id: e393d973-0282-1e60-f491-6d75d4a260ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 791c9c03-0e9a-13cc-9a68-8cd045ef5cad
---

# SMS_SII_Property Class - Configuration Manager | Microsoft Learn

The `SMS_SII_Property` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a general-purpose storage object for property data that can be represented as a single integer or two strings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SII_Property : SMS_SiteInstallItem
{
     String ItemName;
     String ItemType;
     String PropertyName;
     UInt32 Value;
     String Value1;
     String Value2;
};
```

## Methods

The `SMS_SII_Property` class does not define any methods.

## Properties

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItem Server WMI Class](sms_siteinstallitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteInstallItem Server WMI Class](sms_siteinstallitem-server-wmi-class).

`PropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the property. The name is case sensitive and might contain several words, for example, "Connection Point".

`Value` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

A numeric value if the property is numeric.

`Value1` Data type: `String`

Access type: Read/Write

Qualifiers: None

A string value if the property is a string. The value is a registry data type if the property comes from the system registry. Otherwise, the value is the actual string for the property.

`Value2` Data type: `String`

Access type: Read/Write

Qualifiers: None

A value to indicate the string value of the property if `Value1` indicates a `REG_SZ` registry data type.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).