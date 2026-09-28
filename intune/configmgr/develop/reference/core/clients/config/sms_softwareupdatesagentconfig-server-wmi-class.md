---
layout: Conceptual
title: SMS_SoftwareUpdatesAgentConfig Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_softwareupdatesagentconfig-server-wmi-class
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
description: Learn how to represent the settings and properties used by the software updates client agent using SMS_SoftwareUpdatesAgentConfig class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: faf5f973-04f4-f6d5-d762-8a61acd82bfd
document_version_independent_id: 58e287c3-5467-10a5-cbbc-cfe277727fc8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_softwareupdatesagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_softwareupdatesagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_softwareupdatesagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bd345036-4c15-7aa5-0537-0b0e8e5261ea
---

# SMS_SoftwareUpdatesAgentConfig Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareUpdatesAgentConfig` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the settings and properties used by the software updates client agent.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareUpdatesAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    String AlternateContentProviders;
    UInt32 AssignmentBatchingTimeout;
    String BrandingSubTitle;
    String BrandingTitle;
    UInt32 ContentDownloadTimeout;
    UInt32 ContentLocationTimeout;
    UInt32 DayReminderInterval;
    Boolean Enabled;
    String EvaluationSchedule;
    UInt32 HourReminderInterval;
    UInt32 MaxRandomDelayMinutes;
    UInt32 MaxScanRetryCount;
    UInt32 PerDPInactivityTimeout;
    UInt32 ReminderInterval;
    UInt32 ScanRetryDelay;
    String ScanSchedule;
    UInt32 TotalInactivityTimeout;
    UInt32 UpdateStatusRefreshIntervalDays;
    Boolean UserExperience;
    UInt32 UserJobPerDPInactivityTimeout;
    UInt32 UserJobTotalInactivityTimeout;
    UInt32 WSUSLocationTimeout;
    String WSUSScanRetryCodes[];
    UInt32 WUAMaxRebootsWhenOnInternet;
    String WUASuccessCodes[];
};
```

## Methods

The `SMS_SoftwareUpdatesAgentConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The Software Updates Agent ID is 9.

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: none

An XML string to set alternate content provider settings.

`AssignmentBatchingTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The maximum number of seconds between two or more required deployments before those deployments are considered to be a single batch of deployed updates. The default value is 0 (no batching).

`BrandingSubTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

This property is deprecated in Configuration Manager.

`BrandingTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

This property is deprecated in Configuration Manager.

`ContentDownloadTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the timeout value for downloading the content.

`ContentLocationTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates the timeout value for accessing the content location.

`DayReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The day reminder interval. This value is not used by the software updates management feature.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the agent is enabled.

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Deployment re-evaluation schedule.

`HourReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The hour reminder interval. This value is not used by the software updates management feature.

`MaxRandomDelayMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The maximum interval in minutes added to the available after time to prevent a large number of computers from simultaneously downloading the software. This value is not used by the software updates management feature.

`MaxScanRetryCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

When a software update scan returns any error in the array `WSUSScanRetryCodes`, the scan is retried every `ScanRetryDelay` minutes for `MaxScanRetryCount` times.

`PerDPInactivityTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time before the agent no longer attempts to communicate with an inactive or non-responsive distribution point. If 0 is specified, the timeout value is configured as 8 hours. The default value is 1 hour.

`ReminderInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The reminder interval. This value is not used by the software updates management feature.

`ScanRetryDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

When a software update scan returns any error in the array `WSUSScanRetryCodes`, the scan is retried every `ScanRetryDelay` minutes for `MaxScanRetryCount` times.

`ScanSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

Software update scan schedule.

`TotalInactivityTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time before the agent no longer attempts to communicate with an inactive or non-responsive distribution point from all distribution points supplied for system initiated downloads. The agent attempts to communicate with each distribution point supplied for the `PerDPInactivityTimeout` before attempting to communicate with next distribution point supplied.

`UpdateStatusRefreshIntervalDays` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This value is not used by the software updates management client.

`UserExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

This property is deprecated in Configuration Manager.

`UserJobPerDPInactivityTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time before the agent no longer attempts to communicate with an inactive or non-responsive distribution point from all distribution points supplied for user initiated downloads. The agent attempts to communicate with each distribution point supplied for the `PerDPInactivityTimeout` before attempting to communicate with next distribution point supplied. The default timeout is one hour.

`UserJobTotalInactivityTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time before the agent no longer attempts to communicate with an inactive or non-responsive distribution point from all distribution points supplied for user initiated downloads. The agent attempts to communicate with each distribution point supplied for the `PerDPInactivityTimeout` before attempting to communicate with next distribution point supplied. The default timeout is one hour.

`WSUSLocationTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of seconds before the agent no longer waits to receive a list of Windows Software Update Services servers used to perform a software update scan.

`WSUSScanRetryCodes` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

An array of error code values. When a software update scan returns any error in the array `WSUSScanRetryCodes`, the scan is retried every `ScanRetryDelay` minutes for `MaxScanRetryCount` times.

`WUAMaxRebootsWhenOnInternet` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This property is reserved for internal use.

`WUASuccessCodes` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

This property is reserved for internal use.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).