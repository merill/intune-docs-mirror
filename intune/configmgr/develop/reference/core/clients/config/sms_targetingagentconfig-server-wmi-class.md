---
layout: Conceptual
title: SMS_TargetingAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_targetingagentconfig-server-wmi-class
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
description: In Configuration Manager, the SMS_TargetingAgentConfig Windows Management Instrumentation class is an SMS Provider server class that represents how the client is configured for user and device affinity.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 97362fd5-ba99-a457-4018-e6e54cabd62e
document_version_independent_id: d32b6718-f667-1832-97f8-b469a8d13543
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_targetingagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_targetingagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_targetingagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 547ce1f6-0e33-917e-67df-bea3c57932f6
---

# SMS_TargetingAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_TargetingAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents how the client is configured for user and device affinity.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TargetingAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 AllowUserAffinity;
    UInt32 AllowUserAffinityAfterMinutes;
    UInt32 AutoApproveAffinity;
    UInt32 ConsoleMinutes;
    UInt32 IntervalDays;
};
```

## Methods

The `SMS_TargetingAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Targeting Agent Config ID is 10.

`AllowUserAffinity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Allows users to define their primary devices.

`AllowUserAffinityAfterMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This property is obsolete.

`AutoApproveAffinity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Automatically configures user device affinity from usage data.

`ConsoleMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

User device affinity usage threshold in minutes.

`IntervalDays` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

User device affinity usage threshold in days.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).