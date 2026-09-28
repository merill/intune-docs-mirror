---
layout: Conceptual
title: SMS_ST_RecurInterval Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurinterval-server-wmi-class
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
description: In Configuration Manager, the SMS_ST_RecurInterval Windows Management Instrumentation class is an SMS Provider server class that represents a schedule token for events that occur at regular intervals, such as every 10 days.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a65a4b51-57ac-2161-c7f0-9184d9519b7c
document_version_independent_id: 5b12dfd3-025f-5ef9-f4bc-3b76d2ce9ef6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurinterval-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_st_recurinterval-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_st_recurinterval-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5eaee24c-e5ac-d1cf-0704-c4a09ea2f993
---

# SMS_ST_RecurInterval Class - Configuration Manager | Microsoft Learn

The `SMS_ST_RecurInterval` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a schedule token for events that occur at regular intervals, for example, every 10 days.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ST_RecurInterval : SMS_ScheduleToken
{
      UInt32 DayDuration;
      UInt32 DaySpan;
      UInt32 HourDuration;
      UInt32 HourSpan;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      UInt32 MinuteSpan;
      DateTime StartTime;
};
```

## Methods

The `SMS_ST_RecurInterval` class does not define any methods.

## Properties

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`DaySpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-31")]

Number of days spanning schedule intervals. Allowable values are in the range 0-31. The default value is 0.

`HourDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-23")]

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`HourSpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-23")]

Number of hours spanning schedule intervals. Allowable values are in the range 0-23. The default value is 0.

`IsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`MinuteDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-59")]

See [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class).

`MinuteSpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Range("0-59")]

Number of minutes spanning schedule intervals. Allowable values are in the range 0-59. The default value is 0.

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