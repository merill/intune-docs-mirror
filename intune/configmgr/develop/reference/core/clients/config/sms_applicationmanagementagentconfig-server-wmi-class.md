---
layout: Conceptual
title: SMS_ApplicationManagementAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_applicationmanagementagentconfig-server-wmi-class
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
description: In Configuration Manager, the SMS_ApplicationManagementAgentConfig WMI class is an SMS Provider server class that contains the configuration of Application Management client agent settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: eccb7996-1aa6-a0c1-a8f7-d09d4cd11cef
document_version_independent_id: 9d0b5285-2d88-a86a-a10f-19df81f21091
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_applicationmanagementagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_applicationmanagementagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_applicationmanagementagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5a46936a-de66-bd53-405a-45a42959714d
---

# SMS_ApplicationManagementAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_ApplicationManagementAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains the configuration of Application Management client agent settings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ApplicationManagementAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    String AlternateContentProviders;
    Boolean AppXInplaceUpgradeEnabled;
    Boolean Enabled;
    String EvaluationSchedule;
};
```

## Methods

The `SMS_ApplicationManagementAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Application Management Agent ID is 17.

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: none

An XML string to set alternate content provider settings. This property does not apply to a software update package or a driver package.

```
<AlternateDownloadSettings SchemaVersion="1.0">    <Provider Name="logical name here">        <Data>provider specific data here</Data>    </Provider>    <Provider Name="logical name here">         <Data>provider specific data here</Data>    </Provider></AlternateDownloadSettings>
```

`AppXInplaceUpgradeEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether Windows app package (.appx files) in-place upgrade is enabled.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Evaluation schedule for deployments.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).