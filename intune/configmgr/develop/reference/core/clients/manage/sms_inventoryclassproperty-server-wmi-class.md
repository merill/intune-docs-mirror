---
layout: Conceptual
title: SMS_InventoryClassProperty Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclassproperty-server-wmi-class
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
description: Learn how to use the SMS_InventoryClassProperty Windows Management Instrumentation (WMI) class that is embedded in the SMS_InventoryClass.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6cc412b0-827b-c4a4-befa-3e7a21cc36fa
document_version_independent_id: 0cd1fbde-22d3-c609-55c0-2809efa1e6dd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclassproperty-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_inventoryclassproperty-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclassproperty-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8ba8f2d2-aeb4-f5d6-e7b8-07da547f30ee
---

# SMS_InventoryClassProperty Class - Configuration Manager | Microsoft Learn

The `SMS_InventoryClassProperty` Windows Management Instrumentation (WMI) class is an SMS Provider server class, embedded in the `SMS_InventoryClass` that represents the properties associated with an inventory class in Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryClassProperty :
{
    UInt32 IsKey;
    String PropertyName;
    String SMSDeviceUri;
    UInt32 Type;
    String Units;
};
```

## Methods

The `SMS_InventoryClassProperty` class does not define any methods.

## Properties

`IsKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

`true`, if this property is the key of the class. The default value is `false`.

`PropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The name of the property. The default value is an empty string.

`SMSDeviceUri` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS device URI in XML format. This can support multiple device URIs.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

CIMv2 type of property.

`Units` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The units of the property.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).