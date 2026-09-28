---
layout: Conceptual
title: SMS_HardwareInventoryAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_hardwareinventoryagentconfig-server-wmi-class
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
description: In Configuration Manager, the SMS_HardwareInventoryAgentConfig Windows Management Instrumentation class is an SMS Provider server class that specifies hardware inventory settings for client computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 710fbb1e-481d-d68a-2638-999bb73534ba
document_version_independent_id: 76a64cf1-76ba-1159-4e64-7352f980e353
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_hardwareinventoryagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_hardwareinventoryagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_hardwareinventoryagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 374f1caf-d4b6-c474-1e53-6c01c9b88ca2
---

# SMS_HardwareInventoryAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_HardwareInventoryAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies hardware inventory settings for client computers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_HardwareInventoryAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean Enabled;
    String InventoryReportID;
    String LastUpdateTime;
    UInt32 Max3rdPartyMIFSize;
    UInt32 MIFCollection;
    UInt32 ProviderTimeout;
    String Schedule;
};
```

## Methods

The `SMS_HardwareInventoryAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Hardware Inventory Agent ID is 15.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`InventoryReportID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifies the type of inventory report.

| Value | Inventory type |
| --- | --- |
| Hardware Inventory | {00000000-0000-0000-0000-000000000001} |
| Software Inventory | {00000000-0000-0000-0000-000000000002} |
| Data Discovery Record | {00000000-0000-0000-0000-000000000003} |

`LastUpdateTime` Data type: `String`

Access type: Read/Write

Qualifiers: none

Last time the client setting was updated.

`Max3rdPartyMIFSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum custom MIF file size (KB).

`MIFCollection` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

MIF files to collect.

| Value | MIF files to collect |
| --- | --- |
| 0 | None |
| 0x08 | Collect IDMIF files |
| 0x04 | Collect NOIDMIF files |
| 0x0C | Collect IDMIF and NOIDMIF files |

`ProviderTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This property is not currently used.

`Schedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule of hardware inventory.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).