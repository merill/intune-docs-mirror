---
layout: Conceptual
title: SMS_SCI_ClientConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientconfig-server-wmi-class
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
description: Learn how to represent general configuration information that can be used by more than one client component using SMS_SCI_ClientConfig class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 84f26346-9f0a-d4e3-18ed-5e3b98a13c09
document_version_independent_id: e198ced4-fd6d-76e9-1b8c-8792126855b9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_clientconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 308549e6-a7f1-a675-7789-499c77d78d67
---

# SMS_SCI_ClientConfig Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_ClientConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents general configuration information that can be used by more than one client component.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_ClientConfig : SMS_SiteControlItem
{
     String ClientConfigName;
     UInt32 FileType;
     UInt32 Flags;
     String ItemName;
     String ItemType;
     String Platforms[];
     SMS_EmbeddedPropertyList PropLists[];
     SMS_EmbeddedProperty Props[];
     SMS_Client_Reg_MultiString_List RegMultiStringLists[];
     String SiteCode;
};
```

## Methods

The `SMS_SCI_ClientConfig` class does not define any methods.

## Properties

`ClientConfigName` Data type: `String`

Access type: Read/Write

Qualifiers: [StringEnumeration]

Name of the client configuration block. Currently the only defined value is COMP\_STATUS\_MESSAGE\_FILTER (Component Status Message Filter).

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flags identifying the configuration block. Possible values are listed below. The default value is 0.

1 ACTIVE

2 BASE\_INSTALL

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`Platforms` Data type: `String` Array

Access type: Read/Write

Qualifiers: [StringEnumeration]

This property is obsolete.

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the configuration.

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the configuration.

`RegMultiStringLists` Data type: `SMS_Client_Reg_MultiString_List` Array

Access type: Read/Write

Qualifiers: None

[SMS_Client_Reg_MultiString_List Server WMI Class](sms_client_reg_multistring_list-server-wmi-class) objects for the configuration.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

Run the following query for a complete list of client configuration components defined for your site server.

```
SELECT * FROM SMS_SCI_ClientConfig
WHERE SiteCode = "<sitecode>"
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).