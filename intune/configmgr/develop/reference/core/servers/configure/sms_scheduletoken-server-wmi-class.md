---
layout: Conceptual
title: SMS_ScheduleToken Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class
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
description: The SMS_ScheduleToken abstract WMI class is an SMS Provider server class that represents a schedule token that is used for the scheduling of events with different frequencies, for example, hourly and daily.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 864f04de-2d65-7c74-71e1-b103ae81c04d
document_version_independent_id: 5bfa6cc3-b33d-ed99-5cec-3d1e9d6e3167
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9029ec79-2061-24c7-bffc-479f7e741b4f
---

# SMS_ScheduleToken Class - Configuration Manager | Microsoft Learn

The `SMS_ScheduleToken` abstract Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a schedule token that is used for the scheduling of events with different frequencies, for example, hourly and daily.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ScheduleToken
{
      UInt32 DayDuration;
      UInt32 HourDuration;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      DateTime StartTime;
};
```

## Methods

The `SMS_ScheduleToken` class does not define any methods.

## Properties

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-31")]

Number of days during which the scheduled action occurs. Allowable values are in the range 0-31. The default value is 0, indicating that the scheduled action continues indefinitely.

`HourDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-23")]

Number of hours during which the scheduled action occurs. Allowable values are in the range 0-23. The default value is 0, indicating no duration.

`IsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the time is in Coordinated Universal Time (UTC). The default value is `false`, for local time.

`MinuteDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-59")]

Number of minutes during which the scheduled action occurs. Allowable values are in the range 0-59. The default value is 0, indicating no duration.

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the scheduled action takes place. The default value is "19700201000000.000000+\*\*\*".

## Remarks

Class qualifiers for this class include:

- Abstract
- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class is the abstract base class for a number of derived classes representing schedule tokens used for scheduling events with different frequencies, for example, daily. An example of a derived class is [SMS_ST_RecurWeekly Server WMI Class](sms_st_recurweekly-server-wmi-class).

    This class defines several properties related to duration. Network Discovery is the only Configuration Manager component that uses the duration properties. The following is an example showing the use of classes derived from `SMS_ScheduleToken` with an interval string decoded to make a connection to the site server.

```
sInterval = "791378800008000055147880001B200055177880001E2000"
...
instance of SMS_ST_NonRecurring
{
 DayDuration = 0;
 HourDuration = 0;
 IsGMT = FALSE;
 MinuteDuration = 0;
 StartTime = "20040719083000.000000+***";
};

instance of SMS_ST_RecurWeekly
{
 Day = 3;
 DayDuration = 0;
 ForNumberOfWeeks = 1;
 HourDuration = 0;
 IsGMT = FALSE;
 MinuteDuration = 0;
 StartTime = "20040720082100.000000+***";
};

instance of SMS_ST_RecurWeekly
{
 Day = 6;
 DayDuration = 0;
 ForNumberOfWeeks = 1;
 HourDuration = 0;
 IsGMT = FALSE;
 MinuteDuration = 0;
 StartTime = "20040723082100.000000+***";
};
```

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).