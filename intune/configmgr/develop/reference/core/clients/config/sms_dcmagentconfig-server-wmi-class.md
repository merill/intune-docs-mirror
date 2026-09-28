---
layout: Conceptual
title: SMS_DCMAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_dcmagentconfig-server-wmi-class
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
description: Learn how the SMS_DCMAgentConfig Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers retrieve compliance settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 21c8c5d8-374e-7e1b-92e5-ded52a1f9b68
document_version_independent_id: a320ae96-e4cc-7237-e731-a333fdda7a0a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_dcmagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_dcmagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_dcmagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: ea5ccf3f-ddaf-d943-e544-3dc63a070957
---

# SMS_DCMAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_DCMAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers retrieve compliance settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DCMAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean Enabled;
    Boolean EnableUserStateManagement;
    UInt32 PerProviderTimeout;
    UInt32 PerScanDefaultPriority;
    UInt32 PerScanTimeout;
    UInt32 PerScanTTL;
};
```

## Methods

The `SMS_DCMAgentConfig` class doesn't define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Settings Management Agent identifier is 1.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`EnabledUserStateManagement` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable user state management.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`PerProviderTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicated the timeout value for accessing the provider.

`PerScanDefaultPriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Priority of the Settings Management evaluation job. Possible values are:

| Value | Settings scan priority |
| --- | --- |
| priIdle | Idle |
| priNormal | Normal (recommended) |
| priHigh | High |
| priForeground | Foreground |

`PerScanTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Time after which an in-progress Settings Management evaluation will be canceled.

This property is deprecated.

`PerScanTTL` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Time to live (TTL) for the baseline evaluation result. If a baseline is evaluated and then quickly evaluated again, the second evaluation may be ignored depending TTL value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).