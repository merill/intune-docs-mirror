---
layout: Conceptual
title: Configuration Manager Schedules - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-schedules
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
description: The SMS_ScheduleToken WMI class is an abstract parent class for the SMS_ST_ schedule token classes that handle the scheduling of events with differing frequencies.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 6ab75d6b-439d-e459-131e-110a3104eb62
document_version_independent_id: 50b223b4-11fc-37bb-1296-44f9fa55c924
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/about-configuration-manager-schedules.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/about-configuration-manager-schedules
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/about-configuration-manager-schedules.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d597dc8a-5314-58da-ff3e-7798cfb14f9e
---

# Configuration Manager Schedules - Configuration Manager | Microsoft Learn

In Configuration Manager, scheduling information is configured by using schedule tokens. The `SMS_ScheduleToken` Windows Management Instrumentation (WMI) class is an abstract parent class for the SMS\_ST\_ schedule token classes that handle the scheduling of events with differing frequencies such as daily, weekly, and monthly.

The `SMS_ScheduleMethods` WMI class, and the corresponding `ReadFromString` and `WriteToString` methods are used to decode and encode schedule tokens into and from an interval string. The interval strings can be used to set schedule properties when defining or modifying objects.

## Schedule Token Classes Used To Create Different Types of Schedules

The following table describes the embedded classes that you can use to provide scheduling information to Configuration Manager components.

[SMS_ST_NonRecurring Server WMI Class](../../reference/core/servers/configure/sms_st_nonrecurring-server-wmi-class) The `SMS_ST_NonRecurring` WMI class is used for nonrecurring event scheduling by designating a date and time.

[SMS_ST_RecurInterval Server WMI Class](../../reference/core/servers/configure/sms_st_recurinterval-server-wmi-class) The `SMS_ST_RecurInterval` WMI class enables the scheduling of events that occur at regular intervals, such as every 10 days, rather than on designated dates and times.

[SMS_ST_RecurMonthlyByDate Server WMI Class](../../reference/core/servers/configure/sms_st_recurmonthlybydate-server-wmi-class) The `SMS_ST_RecurMonthlyByDate` WMI class enables the scheduling of events that occur on designated days at designated monthly intervals, such as every third month on the 15th day of the month.

[SMS_ST_RecurMonthlyByWeekday Server WMI Class](../../reference/core/servers/configure/sms_st_recurmonthlybyweekday-server-wmi-class) The `SMS_ST_RecurMonthlyByWeekday` WMI class enables the scheduling of events that occur for a specific day of the week, on a given week of the month, at a given monthly interval. For example, the second Saturday of every month.

[SMS_ST_RecurWeekly Server WMI Class](../../reference/core/servers/configure/sms_st_recurweekly-server-wmi-class) The `SMS_ST_RecurWeekly` WMI class enables the scheduling of events that occur at weekly intervals, regardless of the week's sequence in any month, such as every third week on Wednesday.

## Class and Methods Used to Read or Write Schedule Tokens

The following `SMS_ScheduleMethods` WMI class, and the corresponding `ReadFromString` and `WriteToString` methods are used to decode and encode schedule tokens into and from an interval string.

[SMS_ScheduleMethods Server WMI Class](../../reference/core/servers/configure/sms_schedulemethods-server-wmi-class) The `SMS_ScheduleMethods` WMI class contains methods for decoding and encoding schedule tokens into and from an interval string.

These methods are not used to convert the schedule tokens to or from the friendly scheduling strings found in the Configuration Manager console, such as *Occurs every 1 day(s) effective 9:27AM Tuesday*. Instead, the methods are used to convert the schedule tokens to or from SMS interval strings (SMS interval strings are not of the same format as the WMI interval strings). SMS interval strings are an internal representation of the schedule token.

[ReadFromString Method in Class SMS_ScheduleMethods](../../reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods) The `ReadFromString` WMI class method decodes interval strings and places the results into `SMS_ScheduleToken` objects.

[WriteToString Method in Class SMS_ScheduleMethods](../../reference/core/servers/configure/writetostring-method-in-class-sms_schedulemethods) The `WriteToString` WMI class method encodes `SMS_ScheduleToken` data into an SMS interval string.