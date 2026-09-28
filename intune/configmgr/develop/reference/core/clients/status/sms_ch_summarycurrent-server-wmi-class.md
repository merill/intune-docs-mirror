---
layout: Conceptual
title: SMS_CH_SummaryCurrent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_ch_summarycurrent-server-wmi-class
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
description: In Configuration Manager, the SMS_CH_SummaryCurrent Windows Management Instrumentation class is an SMS Provider server class that represents client summary.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4f57e4f6-f1f5-14d2-c7cc-a6e8707a427d
document_version_independent_id: 0fc60d86-7f8a-5f46-b919-3675e9469a9e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/sms_ch_summarycurrent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/sms_ch_summarycurrent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/sms_ch_summarycurrent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 45a1add6-c5ac-0f32-209b-671b99c041ea
---

# SMS_CH_SummaryCurrent Class - Configuration Manager | Microsoft Learn

The `SMS_CH_SummaryCurrent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents client summary.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CH_SummaryCurrent : SMS_BaseClass
{
    UInt32 ClientsActive;
    UInt32 ClientsHealthUnknown;
    UInt32 ClientsHealthy;
    UInt32 ClientsHealthyActive;
    UInt32 ClientsHealthyInactive;
    UInt32 ClientsInactive;
    UInt32 ClientsRemediationSuccess;
    UInt32 ClientsRemediationTotal;
    UInt32 ClientsTotal;
    UInt32 ClientsUnhealthy;
    UInt32 ClientsUnhealthyActive;
    UInt32 ClientsUnhealthyInactive;
    String CollectionID;
};
```

## Methods

The `SMS_CH_SummaryCurrent` class does not define any methods.

## Properties

`ClientsActive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of active clients.

`ClientsHealthUnknown` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of healthy unknown clients.

`ClientsHealthy` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of healthy clients.

`ClientsHealthyActive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of health and active clients.

`ClientsHealthyInactive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of healthy and inactive clients.

`ClientsInactive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of inactive clients.

`ClientsRemediationSuccess` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of successfully remediated clients.

`ClientsRemediationTotal` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Total count of remediated clients (successful and unsuccessful).

`ClientsTotal` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients.

`ClientsUnhealthy` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of unhealthy clients.

`ClientsUnhealthyActive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of unhealthy and active clients.

`ClientsUnhealthyInactive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of unhealthy and inactive clients.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique auto-generated ID containing eight characters that identifies the collection.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).