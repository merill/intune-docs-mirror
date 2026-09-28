---
layout: Conceptual
title: SMS_CH_SummaryHistory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_ch_summaryhistory-server-wmi-class
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
description: Learn how to use the SMS_CH_SummaryHistory class to represent client summary histories.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4adb82bf-ac0a-9c76-f56e-82808ba817bc
document_version_independent_id: 48ac1a99-b0f1-4e08-79bc-8cacf97e91d7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/status/sms_ch_summaryhistory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/status/sms_ch_summaryhistory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/status/sms_ch_summaryhistory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79c6e36a-c0ef-3dba-7898-1d5318f9b00d
---

# SMS_CH_SummaryHistory Class - Configuration Manager | Microsoft Learn

The `SMS_CH_SummaryHistory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the client summary history.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CH_SummaryHistory : SMS_BaseClass
{
    UInt32 ClientsActive;
    UInt32 ClientsActiveHealthyOrActiveNoResults;
    UInt32 ClientsHealthy;
    UInt32 ClientsInactive;
    UInt32 ClientsRemediationSuccess;
    UInt32 ClientsRemediationTotal;
    UInt32 ClientsTotal;
    UInt32 ClientsUnhealthy;
    String CollectionID;
    DateTime Date;
    String SiteCode;
};
```

## Methods

The `SMS_CH_SummaryHistory` class does not define any methods.

## Properties

`ClientsActiveHealthyOrActiveNoResults` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of active, healthy clients and active clients with no results.

`ClientsActive` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of active clients.

`ClientsHealthy` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of healthy clients.

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

Total count of clients.

`ClientsUnhealthy` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of unhealthy clients.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique auto-generated ID containing eight characters that identifies the collection.

`Date` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [key]

The summary date.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Three-letter site code of the site.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).