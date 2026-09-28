---
layout: Conceptual
title: SMS_ST_RecurMonthlyByDate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybydate-server-wmi-class
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
description: Learn how to represent a schedule token for events that occur on designated days at designated monthly intervals using SMS_ST_RecurMonthlyByDate class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cd1039dc-58c2-155d-7614-620a9f9f3b2a
document_version_independent_id: 545a7d32-0640-df9c-0d50-96fc2a39c7bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybydate-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybydate-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_st_recurmonthlybydate-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f4a7f22c-689e-6ba2-5307-7f96722ff98c
---

# SMS_ST_RecurMonthlyByDate Class - Configuration Manager | Microsoft Learn

The `SMS_ST_RecurMonthlyByDate` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a schedule token for events that occur on designated days at designated monthly intervals, for example, every third month on the 15th day of the month.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ST_RecurMonthlyByDate : SMS_ScheduleToken
{
      UInt32 DayDuration;
      UInt32 ForNumberOfMonths;
      UInt32 HourDuration;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      UInt32 MonthDay;
      DateTime StartTime;
};
```

## Methods

The `SMS_ST_RecurMonthlyByDate` class does not define any methods.

## Properties

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`ForNumberOfMonths` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("1-12")]

Number of months for the recurrence. Allowable values are in the range 1-12. The default value is 1.

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

`MonthDay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-31")]

Day of the month on which the action occurs. Allowable values are in the range 0-31. The default value is 0, indicating the last day of the month.

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).