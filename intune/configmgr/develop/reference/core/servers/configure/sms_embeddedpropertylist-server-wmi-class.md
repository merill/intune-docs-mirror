---
layout: Conceptual
title: SMS_EmbeddedPropertyList Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class
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
description: An SMS Provider server class that represents a general-purpose embedded object, which defines property lists.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 207ce927-5d5e-0bb8-d9c6-001a2ac59546
document_version_independent_id: b7cd56f0-2dc9-9b8a-9f6f-5b306c03c152
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 47193207-7826-e2dd-7ee4-e0e3f96bdbca
---

# SMS_EmbeddedPropertyList Class - Configuration Manager | Microsoft Learn

The `SMS_EmbeddedPropertyList` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents a general-purpose embedded object that defines property lists. The property lists are used by the site control file to define the string array properties of a site control item.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_EmbeddedPropertyList
{
     String ItemType;
     String PropertyListName;
     String Values[];
}
```

## Methods

The `SMS_EmbeddedPropertyList` class doesn't define any methods.

## Properties

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Property list token item, site control file.

`PropertyListName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the property list. The name is case sensitive and might contain several words, for example, "Network Connection Accounts". The default value is "".

`Values` Data type: `String` Array

Access type: Read/Write

String values for the property list. For example, "SITE\_DEFN\_NETWK\_CONN\_ACCNTS" is the value corresponding to the property list name "Network Connection Accounts". The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    There is no list that defines the properties for each site control item. The best way to determine the properties for each site control item is to follow the steps defined in `Determining Which Site Control Item to Use`. Property names that contain the word Reserved cannot be modified.

    Arrays of strings that come from the system registry use the [SMS_Client_Reg_MultiString_List Server WMI Class](sms_client_reg_multistring_list-server-wmi-class) class.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).