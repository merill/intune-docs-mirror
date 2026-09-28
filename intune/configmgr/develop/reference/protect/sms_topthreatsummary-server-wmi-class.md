---
layout: Conceptual
title: SMS_TopThreatSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_topthreatsummary-server-wmi-class
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
description: An SMS Provider server class, in Configuration Manager, that summarizes the top threats per collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7a09abd3-6726-3fc1-9a51-71d5e4735dfe
document_version_independent_id: 2566cce5-3cd2-ef44-2e53-5992e98ea2e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_topthreatsummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_topthreatsummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_topthreatsummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c5229812-7291-7cb4-13f8-1b5bf4ad6130
---

# SMS_TopThreatSummary Class - Configuration Manager | Microsoft Learn

The `SMS_TopThreatSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that summarizes the top threats per collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TopThreatSummary : SMS_BaseClass
{
    String CollectionID;
    UInt32 CollectionMembers;
    String CollectionName;
    UInt32 FailedCount;
    DateTime FirstDetectionTime;
    UInt32 InfectedCount;
    Boolean IsAllowed;
    Boolean IsExcluded;
    Boolean IsRestored;
    DateTime LastDetectionTime;
    DateTime LastUpdateTime;
    UInt32 PendingCount;
    UInt32 RemediatedCount;
    UInt32 Severity;
    UInt32 ThreatCategoryID;
    UInt64 ThreatID;
    String ThreatName;
};
```

## Methods

The `SMS_TopThreatSummary` class does not define any methods.

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier of the collection.

`CollectionMembers` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of collection members.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection.

`FailedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Failed action client count.

`FirstDetectionTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

First time the malware is detected.

`InfectedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Infected client count.

`IsAllowed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if we've trigger the action to allow this malware in this collection.

`IsExcluded` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if we've chosen to exclude this malware path (in the scan list) in this collection.

`IsRestored` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if we've tried to restore this malware in this collection.

`LastDetectionTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last detection time.

`LastUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last update time.

`PendingCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of clients with pending actions to finish the remediation of the malware in this collection.

`RemediatedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Number of clients where malware was remediated successfully in the collection.

`Severity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Threat severity. Possible values are:

| Value | Threat severity |
| --- | --- |
| 0 | Not Yet Classified |
| 1 | Low |
| 2 | Medium |
| 3 | Not Used |
| 4 | High |
| 5 | Severe |

`ThreatCategoryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Category identifier of the threat.

`ThreatID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

Identifier of the threat.

`ThreatName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the threat.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).