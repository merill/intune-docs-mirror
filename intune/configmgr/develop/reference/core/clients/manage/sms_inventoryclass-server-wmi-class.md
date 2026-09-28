---
layout: Conceptual
title: SMS_InventoryClass Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclass-server-wmi-class
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
description: In Configuration Manager, the SMS_InventoryClass Windows Management Instrumentation class is an SMS Provider server class that represents inventory classes that exist in the system.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4e99a2b6-36bf-820e-ebcd-4a0d205b1e57
document_version_independent_id: f12962fe-8b1f-9fe0-207a-3e3ae116a86f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclass-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_inventoryclass-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclass-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 072cf663-1774-4f41-942c-a0aec5349898
---

# SMS_InventoryClass Class - Configuration Manager | Microsoft Learn

The `SMS_InventoryClass` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents inventory classes that exist in the system.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryClass :
{
    String ClassName;
    Boolean IsDeletable;
    String Namespace;
    InventoryClassProperty Properties[];
    String SMSClassID;
    String SMSContext;
    String SMSDeviceUri;
    String SMSGroupName;
};
```

## Methods

The following table lists the methods in the `SMS_InventoryClass` class.

| Method | Description |
| --- | --- |
| GetInventoryClassesFromMof Method in Class SMS\_InventoryClass | For internal use only. |

## Properties

`ClassName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The WMI name of the inventory class.

`IsDeletable` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

For internal use only.

`Namespace` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The WMI namespace.

`Properties` Data type: `Object Array`

Access type: Read/Write

Qualifiers: none

The properties of this class.

`SMSClassID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The Class ID that will be used to generate the database table, view and the UI SDK class.

`SMSContext` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS contexts in XML format. This can support multiple contexts.

`SMSDeviceUri` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS device URI in XML format. This could support multiple device URIs.

`SMSGroupName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The default class name displayed in the MOF editor and Resource Explorer, if no localized resources are provided.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).