---
layout: Conceptual
title: SMS_EmbeddedProperty Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class
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
description: An SMS Provider that represents a general-purpose embedded property. The property is used by the site control file to define the properties of a site control item.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6d7a2f67-658d-8a54-bdf5-2807854e61af
document_version_independent_id: afd52c4b-c928-79aa-b03c-0b4d33af8399
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d86cc4ad-8a01-cfb7-1925-4ebadf5edacd
---

# SMS_EmbeddedProperty Class - Configuration Manager | Microsoft Learn

The `SMS_EmbeddedProperty` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents a general-purpose embedded property used by the site control file to define the properties of a site control item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_EmbeddedProperty
{
     String ItemType;
     String PropertyName;
     UInt32 Value;
     String Value1;
     String Value2;
};
```

## Methods

The `SMS_EmbeddedProperty` class doesn't define any methods.

## Properties

`ItemType` Data type: **String**

Access type: Read-only

Qualifiers: [key, read]

Property token item, site control file.

`PropertyName` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name of the property. The name is case sensitive and might contain several words, such as "Startup Schedule". The default value is "".

`Value` Data type: **UInt32**

Access type: Read/Write

Qualifiers: None

A numeric value if the property is numeric. The default value is 0.

`Value1` Data type: **String**

Access type: Read/Write

Qualifiers: None

A string value if the property is a string. The value is a registry data type if the property comes from the system registry. Otherwise, the value is the actual string for the property. The default value is "".

`Value2` Data type: **String**

Access type: Read/Write

Qualifiers: None

A value to indicate the string value of the property if `Value1` indicates a `REG_SZ` registry data type. The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Some properties contain multiple property values and store values in both `Value1` and `Value2`. Properties that contain multi-string registry data types use the [SMS_Client_Reg_MultiString_List Server WMI Class](sms_client_reg_multistring_list-server-wmi-class).

    There's no list that defines the properties for each site control item. Property names that contain the word "Reserved" can't be modified.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).