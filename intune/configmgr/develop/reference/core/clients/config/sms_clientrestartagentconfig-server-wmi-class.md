---
layout: Conceptual
title: SMS_ClientRestartAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientrestartagentconfig-server-wmi-class
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
description: An SMS Provider server class that represents the settings and properties used by the client restart agent.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e1c19d03-5393-704e-f68d-c475bed00234
document_version_independent_id: 1012f7f3-30e8-e54f-1cb8-0f4ce59e456a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientrestartagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientrestartagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientrestartagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cdfb00a2-7991-b1f3-a309-972e1e381d48
---

# SMS_ClientRestartAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_ClientRestartAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the settings and properties used by the client restart agent.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientRestartAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 RebootLogoffNotificationCountdownDuration;
    UInt32 RebootLogoffNotificationFinalWindow;
};
```

## Methods

The `SMS_ClientRestartAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The SMS\_ClientRestartAgentConfig Agent ID is 21.

`RebootLogoffNotificationCountdownDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Display a temporary notification to the user that indicates the interval before the user is logged off or the computer restarts (minutes).

`RebootLogoffNotificationFinalWindow` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Display a dialog box that the user cannot close, which displays the countdown interval before the user is logged off or the computer restarts (minutes).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).