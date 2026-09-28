---
layout: Conceptual
title: SMS_ClientCommunicationConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientcommunicationconfig-server-wmi-class
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
description: Learn how to control how Windows 8 client computers communicate with Configuration Manager sites when they use metered Internet connections.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5e7ddd41-cd15-97c2-4c23-21ece8cc94b5
document_version_independent_id: f7253d3d-96fe-bc30-2aee-0209c5e382de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_clientcommunicationconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_clientcommunicationconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_clientcommunicationconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae27e5a5-0f1d-66bb-4a77-49587eb9814e
---

# SMS_ClientCommunicationConfig Class - Configuration Manager | Microsoft Learn

The `SMS_ClientCommunicationConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that controls how Windows 8 client computers communicate with Configuration Manager sites when they use metered Internet connections.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientCommunicationConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 MeteredNetworkUsage;
};
```

## Methods

The `SMS_ClientCommunicationConfig` class doesn't define any methods.

## Properties

`MeteredNetworkUsage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Set metered network usage behavior. Possible values are:

| Value | Metered network usage policy |
| --- | --- |
| 1 | Allow metered network use. |
| 2 | Only use the metered network for deployments that are marked to allow use of the metered network. This means meta-data such as policy will always use the metered network. And based on the policy, the client decides whether or not to use the metered network for the deployment. |
| 4 | Block metered network usage. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).