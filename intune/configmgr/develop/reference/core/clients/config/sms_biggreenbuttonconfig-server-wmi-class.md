---
layout: Conceptual
title: SMS_BigGreenButtonConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_biggreenbuttonconfig-server-wmi-class
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
description: Learn how to stop clients from connecting to the client notification server with SMS_BigGreenButtonConfig.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3a8e542a-82e8-a67b-67d0-e8052b572073
document_version_independent_id: fee3f4bd-e369-864a-102c-bd398bd25b15
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_biggreenbuttonconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_biggreenbuttonconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_biggreenbuttonconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6f673bbc-c086-ba84-d2d7-d8373497180d
---

# SMS_BigGreenButtonConfig Class - Configuration Manager | Microsoft Learn

The `SMS_BigGreenButtonConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that can stop clients from connecting to the client notification server (a hidden role, co-located with management point).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BigGreenButtonConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean EnableClientNotification;
};
```

## Methods

The `SMS_BigGreenButtonConfig` class doesn't define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The BigGreenButton Agent ID is 18.

`EnableClientNotification` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`false` to stop clients from connecting to the client notification server (a hidden role, co-located with management point). No active connections are established between the clients and the client notification server. The default value is `true`.

This setting is part of the client infrastructure and turned on by default. This value would likely only be changed to troubleshoot a significant performance issue.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).