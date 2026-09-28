---
layout: Conceptual
title: SMS_EndpointProtectionHealthStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_endpointprotectionhealthstatus-server-wmi-class
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
description: Learn how the SMS_EndpointProtectionHealthStatus class is an SMS Provider server class that represents health status of Endpoint Protection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3180b3b7-af80-93c7-4cce-52f9a08b005f
document_version_independent_id: b7facd7e-34eb-5ced-7ea2-9195461872c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/protect/sms_endpointprotectionhealthstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/protect/sms_endpointprotectionhealthstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/protect/sms_endpointprotectionhealthstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bfa0bd67-933c-67cd-6819-6401d9516b4c
---

# SMS_EndpointProtectionHealthStatus Class - Configuration Manager | Microsoft Learn

The `SMS_EndpointProtectionHealthStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents health status of Endpoint Protection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_EndpointProtectionHealthStatus : SMS_BaseClass
{
    UInt32 ApplyPolicyFailedCount;
    UInt32 ApplyPolicySucceededCount;
    String CollectionID;
    UInt32 InstallFailedCount;
    UInt32 InstallRebootPendingCount;
    UInt32 NoSignatureCount;
    UInt32 OverallNotClientCount;
    UInt32 OverallStatusAtRiskCount;
    UInt32 OverallStatusInactiveCount;
    UInt32 OverallStatusNotSupportedCount;
    UInt32 OverallStatusNotYetInstalledCount;
    UInt32 OverallStatusProtectedCount;
    UInt32 SignaturesOlderThan7DaysCount;
    UInt32 SignaturesUpTo1DayOldCount;
    UInt32 SignaturesUpTo3DaysOldCount;
    UInt32 SignaturesUpTo7DaysOldCount;
    DateTime TimeLastUpdated;
    UInt32 TotalMemberCount;
    UInt32 TotalOperationalIssueCount;
    UInt32 UnhealthyCount;
};
```

## Methods

The `SMS_EndpointProtectionHealthStatus` class does not define any methods.

## Properties

`ApplyPolicyFailedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients failed to apply policy.

`ApplyPolicySucceededCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients succeeded to apply policy.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier of collection summarized.

`InstallFailedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients failed to install the Endpoint Protection client.

`InstallRebootPendingCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients pending restart to complete Endpoint Protection client installation.

`NoSignatureCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients without definitions.

`OverallNotClientCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of non-client members.

`OverallStatusAtRiskCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with deficient status (agent health, malware, signatures, agent deployment).

`OverallStatusInactiveCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of inactive clients.

`OverallStatusNotSupportedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients not supported by Endpoint Protection agent.

`OverallStatusNotYetInstalledCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients without Endpoint Protection client installed yet.

`OverallStatusProtectedCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with good overall status (agent health, malware, signatures, agent deployment).

`SignaturesOlderThan7DaysCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with definitions that are 7 days old or older.

`SignaturesUpTo1DayOldCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with definitions less than 24 hours old.

`SignaturesUpTo3DaysOldCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with definitions between 1 and 2 days old.

`SignaturesUpTo7DaysOldCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with definitions between 3 and 6 days old.

`TimeLastUpdated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Time the statistics were last updated.

`TotalMemberCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Total count of members in the collection.

`TotalOperationalIssueCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with any of 5 types of operational issues.

`UnhealthyCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of clients with unhealthy agents.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).