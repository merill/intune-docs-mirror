---
layout: Conceptual
title: SMS_Client_Reg_MultiString_List Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class
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
description: An SMS Provider server class that represents a list of client registry multi-string items from the site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7c025c71-930a-c1ba-9ac2-2afcbcc268c4
document_version_independent_id: 43aa963b-cdc7-4e23-cc54-24c9a4da09af
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3f509a18-8e06-848d-2123-643497d735ba
---

# SMS_Client_Reg_MultiString_List Class - Configuration Manager | Microsoft Learn

The `SMS_Client_Reg_MultiString_List` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents a list of client registry multi-string items from the site control file.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Client_Reg_MultiString_List
{
     String ItemType;
     String ValueName;
     String KeyPath;
     String ValueStrings[];
};
```

## Methods

The `SMS_Client_Reg_MultiString_List` class doesn't define any methods.

## Properties

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Client registry multstring item type.

`ValueName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Property name reflected in the system registry key where the multi-string items are stored. The default value is "".

`KeyPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Path to the multi-string item. The default value is "".

Note

Do not set this property when updating the `ValueName` property.

`ValueStrings` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of strings that serve as registry data values. The meaning of the strings is determined by the `ValueName` property.

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class behaves the same as [SMS_EmbeddedPropertyList Server WMI Class](sms_embeddedpropertylist-server-wmi-class). It's used to represent data that is stored in the system registry with the `REG_MULTI_SZ` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).