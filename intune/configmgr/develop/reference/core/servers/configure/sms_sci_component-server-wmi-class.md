---
layout: Conceptual
title: SMS_SCI_Component Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class
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
description: Learn how to represent a Configuration Manager server component installed on one or more servers at a site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 371f0509-57bb-896b-66b4-57a38dd269f6
document_version_independent_id: 4e20bb09-2fb2-4b6d-9333-ce3f8fac6b97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1f161668-4d99-87a1-5582-b8e103fa4623
---

# SMS_SCI_Component Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_Component` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager server component installed on one or more servers at a site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_Component : SMS_SiteControlItem
{
     String ComponentName;
     UInt32 FileType;
     UInt32 Flag;
     String ItemName;
     String ItemType;
     String Name;
     SMS_EmbeddedProperty Props[];
     SMS_EmbeddedPropertyList PropLists[];
     String SiteCode;
};
```

## Methods

The `SMS_SCI_Component` class does not define any methods.

## Properties

`ComponentName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the Configuration Manager server component. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration:ToSubClass]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`Flag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flag identifying the component. Possible values are listed below. The default value is NAMED\_SERVER\_INSTALLED (6).

| Value | Description |
| --- | --- |
| 1 | ROLE\_NOT\_INSTALLED. If the flag is set to this value, the `Name` property specifies the server role. The component is installed on every server having the specified role. |
| 2 | NAMED\_SERVER\_NOT\_INSTALLED. If the flag is set to this value, the `Name` property specifies a particular server on which the component is installed. The server name does not include backslashes. |
| 5 | ROLE\_INSTALLED. If the flag is set to this value, the `Name` property specifies the server role. The component is installed on every server having the specified role. |
| 6 | NAMED\_SERVER\_INSTALLED. If the flag is set to this value, the `Name` property specifies a particular server on which the component is installed. The server name does not include backslashes. |

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Configuration Manager role or server name, depending on the value of `Flag`. The default value is "".

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the component.

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the component.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

Run the following query for a complete list of Configuration Manager server components defined for your site server.

```
SELECT * FROM SMS_SCI_Component
WHERE SiteCode = "<sitecode>"
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).