---
layout: Conceptual
title: SMS_StateSystemConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_statesystemconfig-server-wmi-class
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
description: In Configuration Manager, the SMS_StateSystemConfig WMI class is an SMS Provider server class that specifies how client computers report state messages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a81767d7-5dc6-2a62-de49-3cb74f83f95c
document_version_independent_id: 2342b429-5751-f5e7-b4eb-8d05583df0d9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_statesystemconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_statesystemconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_statesystemconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eef0de25-4fca-2850-de2e-fe03d1a50667
---

# SMS_StateSystemConfig Class - Configuration Manager | Microsoft Learn

The `SMS_StateSystemConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers report state messages.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StateSystemConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 BulkSendInterval;
    UInt32 BulkSendIntervalHigh;
    UInt32 BulkSendIntervalLow;
    String CacheCleanoutInterval;
    UInt32 CacheMaxAge;
};
```

## Methods

The `SMS_StateSystemConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The State System Config Agent ID is 16.

`BulkSendInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with normal priority.

`BulkSendIntervalHigh` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with high priority.

`BulkSendIntervalLow` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with low priority.

`CacheCleanoutInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`CacheMaxAge` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).