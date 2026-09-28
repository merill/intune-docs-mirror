---
layout: Conceptual
title: SMS_ComponentSummarizer Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_componentsummarizer-server-wmi-class
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
description: The SMS_ComponentSummarizer WMI class is an SMS Provider server class that represents a component summarizer that reports on the health of individual components.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bea1aa81-dfec-0a67-39c6-61843cc822c0
document_version_independent_id: bf5f2ab4-d32f-c9a5-470c-0157db667c90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_componentsummarizer-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_componentsummarizer-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_componentsummarizer-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f2e2ec3-1340-6377-3bec-f69802e900d6
---

# SMS_ComponentSummarizer Class - Configuration Manager | Microsoft Learn

The `SMS_ComponentSummarizer` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a component summarizer that reports on the health of individual Configuration Manager components.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ComponentSummarizer : SMS_BaseClass
{
      UInt32 AvailabilityState;
      String ComponentName;
      String ComponentType;
      UInt32 Errors;
      UInt32 HeartbeatInterval;
      UInt32 Infos;
      DateTime LastContacted;
      DateTime LastHeartbeat;
      DateTime LastStarted;
      String MachineName;
      DateTime NextScheduledTime;
      String SiteCode;
      UInt32 State;
      UInt32 Status;
      String TallyInterval;
      UInt32 Type;
      UInt32 Warnings;
};
```

## Methods

The following table lists the methods in `SMS_ComponentSummarizer`.

| Method | Description |
| --- | --- |
| [DeleteStatistics Method in Class SMS_ComponentSummarizer](deletestatistics-method-in-class-sms_componentsummarizer) | Deletes statistics reported by the component summarizer. |

## Properties

`AvailabilityState` Data type: `UInt32`

Access type: Read

Qualifiers: None

Availability state of the component. The default value is 0.

`ComponentName` Data type: `String`

Access type: Read

Qualifiers: [key, SizeLimit("40")]

Name of the Configuration Manager component.

`ComponentType` Data type: `String`

Access type: Read

Qualifiers: None

The component type.

`Errors` Data type: `UInt32`

Access type: Read

Qualifiers: None

Count of all error status messages reported by the component during the tally interval.

`HeartbeatInterval` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The heartbeat interval.

`Infos` Data type: `UInt32`

Access type: Read

Qualifiers: None

Count of all informational status messages reported by the component during the tally interval.

`LastContacted` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time of when a status message was last received from the component. The time zone is based on the time zone of the site specified in the `SiteCode` property.

`LastHeartbeat` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time of the last heartbeat.

`LastStarted` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time when the component last started. The time zone is based on the time zone of the site specified in the `SiteCode` property.

`MachineName` Data type: `String`

Access type: Read

Qualifiers: [key]

Name of the computer on which the component is installed. Some components might run on computers other than the site server.

`NextScheduledTime` Data type: `DateTime`

Access type: Read

Qualifiers: None

Date and time when the component is next scheduled to start, if the component runs according to a schedule. The time zone is based on the time zone of the `SiteCode` property.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key, SizeLimit("3")]

Site code of the Configuration Manager site to which the component is related.

`State` Data type: `UInt32`

Access type: Read

Qualifiers: None

State of the component. Possible values are:

| Value | State |
| --- | --- |
| 0 | STOPPED |
| 1 | STARTED |
| 2 | PAUSED |
| 3 | INSTALLING |
| 4 | RE\_INSTALLING |
| 5 | DE\_INSTALLING |

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: None

Status value indicating the health of the component. Possible values are:

| Value | Status |
| --- | --- |
| GREEN(0) | OK. There are no warning or error messages. |
| YELLOW(1) | Warning. Warning messages were generated, but not error messages. |
| RED(2) | Critical. There are error messages. |

`TallyInterval` Data type: `String`

Access type: Read

Qualifiers: [key]

Interval or time period for which the statistics apply. You must specify a tally interval in the WHERE clause to query instances of this class. The statistics are reset to zero each time the schedule elapses. To use this property, see [How to Read The Tally Intervals For a Configuration Manager Site](../../../../core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site).

`Type` Data type: `UInt32`

Access type: Read

Qualifiers: None

Type of component, for example, one that autostarts (runs continuously). Possible values are:

| Value | Type |
| --- | --- |
| 0 | AUTOSTARTING |
| 1 | SCHEDULED |
| 2 | MANUAL |

`Warnings` Data type: `UInt32`

Access type: Read

Qualifiers: None

Count of all warning status messages reported by the component during the tally interval.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class reports on component health by counting the error, warning, and informational status messages that are produced by each component. It provides a high-level view of the health of server components at a given site. An instance of this class is created for each server component running in the site.

    Queries must include a `TallyInterval` value.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).