---
layout: Conceptual
title: SMS_SCI_Configuration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_configuration-server-wmi-class
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
description: In Configuration Manager, the SMS_SCI_Configuration Windows Management Instrumentation class is an SMS Provider server class that represents a configuration item, which is a generic named container of properties and property lists, for a site server component.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c47bce34-48f7-aa72-d3fb-83523ba99e13
document_version_independent_id: fe95eb4b-cd4e-aa6c-0a35-2252344901ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_sci_configuration-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_sci_configuration-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_sci_configuration-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79a94a20-fded-4bf9-ebb0-1232742c1e0c
---

# SMS_SCI_Configuration Class - Configuration Manager | Microsoft Learn

The `SMS_SCI_Configuration` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item, which is a generic named container of properties and property lists, for a site server component.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_Configuration : SMS_SiteControlItem
{
     String ConfigurationName;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     SMS_EmbeddedProperty Props[];
     SMS_EmbeddedPropertyList PropLists[];
     String SiteCode;
};
```

## Methods

The `SMS_SCI_Configuration` class does not define any methods.

## Properties

`ConfigurationName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the configuration.

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

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedProperty Server WMI Class](sms_embeddedproperty-server-wmi-class) objects for the configuration.

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class) objects for the configuration.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key, SizeLimit("3")]

See [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

Run the following query for a complete list of configuration objects on your site server.

```
SELECT * FROM SMS_SCI_Configuration
WHERE SiteCode = "<sitecode>"
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).