---
layout: Conceptual
title: SMS_SoftwareMeteringAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_softwaremeteringagentconfig-server-wmi-class
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
description: Learn how to use the SMS_SoftwareMeteringAgentConfig class to specify how client computers retrieve data about the software they use.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 077efde5-994c-0737-94c1-a36aa7b276e1
document_version_independent_id: 029338fe-b611-e4b8-baaa-6a07b3ef8248
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_softwaremeteringagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_softwaremeteringagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_softwaremeteringagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: babb4469-126a-fbdc-acef-5dd95dc0021b
---

# SMS_SoftwareMeteringAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareMeteringAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers retrieve data about the software that they use.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareMeteringAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    String DataCollectionSchedule;
    Boolean Enabled;
    String LastUpdateTimeOfRules;
    UInt32 MaximumUsageInstancesPerReport;
    String MeterRuleIDList[];
    UInt32 MRUAgeLimitInDays;
    UInt32 MRURefreshInMinutes;
    UInt32 ReportTimeout;
};
```

## Methods

The `SMS_SoftwareMeteringAgentConfig` class doesn't define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Software Metering Agent ID is 8.

`DataCollectionSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule for data collection.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`LastUpdateTimeOfRules` Data type: `String`

Access type: Read/Write

Qualifiers: none

Last updated time of the metering rules. This isn't currently used.

`MaximumUsageInstancesPerReport` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum number of usage instances which is sent from the client to the site server when collecting software usage data.

`MeterRuleIDList` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

Identifier list of metering rules. This isn't currently used.

`MRUAgeLimitInDays` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The age limit of the mostly recently used applications maintained on the client. Records older than this age limit are removed.

`MRURefreshInMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

How often the mostly recently used applications list is refreshed. When the applications list is refreshed, the aged records are removed.

`ReportTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum time that the client messaging framework attempts to transmit the report if the destination endpoint is unreachable.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).