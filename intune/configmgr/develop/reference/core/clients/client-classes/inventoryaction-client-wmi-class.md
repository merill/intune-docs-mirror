---
layout: Conceptual
title: InventoryAction Client WMI Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventoryaction-client-wmi-class
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
description: Learn how to associate a set of queries with reporting details, tying together the item to report and the destination of the report.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 122a2497-3c07-9e20-7978-7e0073cee70b
document_version_independent_id: 762dd8ae-ee89-66ae-db95-d9af57a3c6ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/inventoryaction-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/inventoryaction-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/inventoryaction-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 090081a0-b14a-f45c-c05b-1d1920164e6b
---

# InventoryAction Client WMI Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `InventoryAction` class is a client Windows Management Instrumentation (WMI) class that associates a set of queries with reporting details, tying together the item to report and the destination of the report.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class InventoryAction : SMS_InventoryAgent_Policy
{
      UInt32 DefaultTimeout;
      String Description;
      String InventoryActionID;
      String InventoryActionLastUpdateTime;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String ReportDestination;
      UInt32 ReportTimeout;
      String ReportType;
};
```

## Methods

The `InventoryAction` class does not define any methods.

## Properties

`DefaultTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Maximum time, by default, that the agent waits for each `InventoryDataItem` class query before canceling the query. The individual `InventoryDataItem` instances can override this default timeout.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Text field that describes the inventory action. Possible values are:

- Hardware
- Software
- Discovery

    `InventoryActionID` Data type: `String`

    Access type: Read/Write

    Qualifiers: [realkey]

    Unique ID for the inventory action. Possible values are:

| Inventory Action ID type | Value |
| --- | --- |
| Discovery | {00000000-0000-0000-0000-000000000003} |
| Hardware Inventory | {00000000-0000-0000-0000-000000000001} |
| Software Inventory | {00000000-0000-0000-0000-000000000002} |
| SoftwareFileCollection | {00000000-0000-0000-0000-000000000010} |
| IDMIF collection | {00000000-0000-0000-0000-000000000011} |

`InventoryActionLastUpdateTime` Data type: `String`

Access type: Read/Write

Qualifiers: None

Timestamp of the last update to the InventoryAction instance.

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

Qualifiers: Key

Unique ID of the rule used to create the policy.

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Source of the policy.

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Version of the policy.

`ReportDestination` Data type: `String`

Access type: Read/Write

Qualifiers: None

Destination address for the generated report.

`ReportTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Maximum time that the client messaging framework attempts to transmit the report if the destination endpoint is unreachable.

`ReportType` Data type: `String`

Access type: Read/Write

Qualifiers: None

Type of inventory report. Possible values are:

| Value | Description |
| --- | --- |
| Full | Report contains all instances collected by the associated `InventoryDataItem` queries. |
| Delta | Report contains instances that have changed since the last report |
| Resync | Report contains instances in full report and also is triggered by a site policy resynchronization request |

## Remarks

Three predefined inventory actions are provided through the site policy: hardware inventory, data discovery, and software inventory. For each of these inventory actions, the Inventory Agent generates a report by using the associated [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) queries and sends the generated report to the specified destination.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).