---
layout: Conceptual
title: InventoryDataItem Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class
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
description: A Windows Management Instrumentation class that defines an inventory.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d4f72974-791c-9f84-7fef-2a5d57f72625
document_version_independent_id: ef69b659-771f-56b3-430b-149090c9aded
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c341935-f4dd-2ead-4d8d-fc43fb2b42e6
---

# InventoryDataItem Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `InventoryDataItem` class is a client Windows Management Instrumentation (WMI) class that defines an inventory collection query.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class InventoryDataItem : SMS_InventoryAgent_Policy
{
      String AssocClass[];
      InventoryDataContext Context[];
      String DataItemID;
      String Filter;
      String InventoryActionID;
      String ItemClass;
      String Namespace;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String Properties;
      PropertyRule ReportRules[];
      UInt32 Timeout;
};
```

## Methods

The `InventoryDataItem` class does not define any methods.

## Properties

`AssocClass` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Reserved for future use.

`Context` Data type: `InventoryDataContext` Array

Access type: Read/Write

Qualifiers: None

Optional context qualifier for the class query. For more information, see [InventoryDataContext Client WMI Class](inventorydatacontext-client-wmi-class).

`DataItemID` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

Unique identifier for an [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) object.

`Filter` Data type: `String`

Access type: Read/Write

Qualifiers: None

Class query property filter, for example, NumberOfProcessors=1 AND DomainRole=1. The Inventory Agent uses this field to build the WQL WHERE clause for the class instance query.

`InventoryActionID` Data type: `String`

Access type: Read/Write

Qualifiers: None

ID that matches the `InventoryActionID` value for an associated [InventoryAction Client WMI Class](inventoryaction-client-wmi-class) object. The Inventory Agent uses this value to find the [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) class for a particular inventory action.

`ItemClass` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

WMI instance class to query, for example, Win32\_ComputerSystem.

`Namespace` Data type: `String`

Access type: Read/Write

Qualifiers: [realkey]

WMI namespace to query, for example, \\\\.\\root\\cimv2.

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy.

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy instance.

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Precedence for the policy.

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the rule used to create the policy.

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Source of the policy.

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Version of the policy.

`Properties` Data type: `String`

Access type: Read/Write

Qualifiers: None

Class properties to query, for example, Domain, Name, and UserName. The Inventory Agent uses this property to build the WQL SELECT clause for the class instance query.

`ReportRules` Data type: `PropertyRule` Array

Access type: Read/Write

Qualifiers: None

Reserved for future use.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Maximum time that the agent waits for the `InventoryDataItem` class query to complete before canceling the query. This property overrides `DefaultTimeOut` property in the [InventoryAction Client WMI Class](inventoryaction-client-wmi-class) class.

## Remarks

The Inventory Agent uses each instance of this class to build a WMI query for the referenced class; for example, `SELECT Name FROM Win32_ComputerSystem WHERE  DomainRole=1`.

The Inventory Agent collects items returned by [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) queries and builds a report based on the results. Each `InventoryDataItem` object contains a reference to an [InventoryAction Client WMI Class](inventoryaction-client-wmi-class) object. Multiple `InventoryDataItem` queries are used to build the combined report for an `InventoryAction` object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).