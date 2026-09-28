---
layout: Conceptual
title: SMS_PowerAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_poweragentconfig-server-wmi-class
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
description: The SMS_PowerAgentConfig Windows Management Instrumentation class is an SMS Provider server class, in Configuration Manager, that specifies power management settings on client computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a7d113ca-fec6-5ddf-d740-4ee010b3efbb
document_version_independent_id: e531741c-7bb2-de27-6841-fdfa2a78ab7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_poweragentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_poweragentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_poweragentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: def8b24f-a741-b9bc-e8fb-649b5c512a9e
---

# SMS_PowerAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_PowerAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies power management settings on client computers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PowerAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean AllowUserToOptOutFromPowerPlan;
    Boolean Enabled;
    Boolean EnableP2PWakeupSolution; (obsolete in SP1)
    Boolean EnableWakeupProxy;
    Boolean EnableUserIdleMonitoring;
    UInt32 MaxCPU;
    UInt32 MaxMachinesPerManager;
    UInt32 MinimumServersNeeded;
    UInt32 NumOfDaysToKeep;
    UInt32 NumOfMonthsToKeep;
    UInt32 Port;
    UInt32 WakeupProxyDirectAccessPrefixList;
    UInt32 WakeupProxyFirewallFlags;
    UInt32 WolPort;
};
```

## Methods

The `SMS_PowerAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Power Management Agent ID is 18.

`AllowUserToOptOutFromPowerPlan` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to allow users to exclude their device from power management.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`EnableP2PWakeupSolution` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

This method/property has been removed or deprecated in Configuration Manager SP1.

`EnableWakeupProxy` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

EnableWakeupProxy.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`EnableUserIdleMonitoring` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if user idle status needs to be monitored. The default value is `true`.

`MaxCPU` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`MaxMachinesPerManager` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`MinimumServersNeeded` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`NumOfDaysToKeep` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum number of days that power data will be kept on the client computer. The default value is 31.

`NumOfMonthsToKeep` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum number of months that power data will be kept on the client computer. The default value is 13.

`Port` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`WakeupProxyDirectAccessPrefixList` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

WakeupProxyDirectAccessPrefixList.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`WakeupProxyFirewallFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

WakeupProxyFirewallFlags.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`WolPort` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).