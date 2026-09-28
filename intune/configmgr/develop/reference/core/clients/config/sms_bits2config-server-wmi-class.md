---
layout: Conceptual
title: SMS_BITS2Config Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_bits2config-server-wmi-class
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
description: Learn how to specify Background Intelligent Transfer settings for client computers using SMS_BITS2Config class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9f5348ff-522e-f3aa-c002-51196f16a1e5
document_version_independent_id: 39124f11-bb35-101d-2927-835f0f08e494
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_bits2config-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_bits2config-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_bits2config-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ce8d9b7d-d987-02de-69ee-23b3ed279857
---

# SMS_BITS2Config Class - Configuration Manager | Microsoft Learn

The `SMS_BITS2Config` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies Background Intelligent Transfer settings for client computers.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BITS2Config : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean ApplyToAllClients;
    Boolean EnableBitsMaxBandwidth;
    Boolean EnableDownloadOffSchedule;
    UInt32 MaxBandwidthValidFrom;
    UInt32 MaxBandwidthValidTo;
    UInt32 MaxTransferRateOffSchedule;
    UInt32 MaxTransferRateOnSchedule;
};
```

## Methods

The `SMS_BITS2Config` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The BITS2Config Agent ID is 11.

`ApplyToAllClients` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to apply Background Intelligent Transfer settings to all computers.

`EnableBitsMaxBandwidth` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable maximum network bandwidth for BITS background transfers.

`EnableDownloadOffSchedule` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to allow BITS downloads outside of the throttling window.

`MaxBandwidthValidFrom` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Throttling window end time. Valid values are from 0-23.

`MaxBandwidthValidTo` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Throttling window start time. Valid values are from 0-23.

`MaxTransferRateOffSchedule` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum transfer rate outside of the throttling window (Kbps).

`MaxTransferRateOnSchedule` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum transfer rate during the throttling window (Kbps).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).