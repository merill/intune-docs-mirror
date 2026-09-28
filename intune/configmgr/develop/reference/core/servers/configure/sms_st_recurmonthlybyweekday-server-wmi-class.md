---
layout: Conceptual
title: SMS_ST_RecurMonthlyByWeekday Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybyweekday-server-wmi-class
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
description: Learn how to represent a schedule token for events that occur for a specific time interval using SMS_ST_RecurMonthlyByWeekday class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 56d9382a-197b-1f1c-88e2-5045931ad7f9
document_version_independent_id: cb7cf245-2a93-678b-3172-5e49fd195a6b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybyweekday-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybyweekday-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybyweekday-server-wmi-class.md
cmProducts: []
platformId: ca5f52e5-6a7c-e71f-2709-518926efdaaf
---

# SMS_ST_RecurMonthlyByWeekday Class - Configuration Manager | Microsoft Learn

The `SMS_ST_RecurMonthlyByWeekday` WMI class is an SMS Provider server class, in Configuration Manager, that represents a schedule token for events that occur for a specific day of the week, on a given week of the month, at a given monthly interval, for example, the second Saturday of every month.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ST_RecurMonthlyByWeekday : SMS_ScheduleToken
{
      UInt32 Day;
      UInt32 DayDuration;
      UInt32 ForNumberOfMonths;
      UInt32 HourDuration;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      DateTime StartTime;
      UInt32 WeekOrder;
};
```

## Methods

The `SMS_ST_RecurMonthlyByWeekday` class does not define any methods.

## Properties

`Day` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Day of the week when the event is scheduled to occur. Possible values are listed below. The default value is 1.

| Value | Day |
| --- | --- |
| 1 | SUNDAY |
| 2 | MONDAY |
| 3 | TUESDAY |
| 4 | WEDNESDAY |
| 5 | THURSDAY |
| 6 | FRIDAY |
| 7 | SATURDAY |

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-31")]

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`ForNumberOfMonths` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("1-12")]

Number of months for recurrence. Allowable values are in the range 1-12. The default value is 1.

`HourDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-23")]

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`IsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`MinuteDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-59")]

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`WeekOrder` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Week of the month when the event is scheduled to occur. Possible values are listed below. The default value is 0.

| Value | Week |
| --- | --- |
| 0 | LAST |
| 1 | FIRST |
| 2 | SECOND |
| 3 | THIRD |
| 4 | FOURTH |

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).