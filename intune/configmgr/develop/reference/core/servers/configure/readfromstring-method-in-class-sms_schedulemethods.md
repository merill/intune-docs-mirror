---
layout: Conceptual
title: ReadFromString Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods
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
description: Article outlining how to read SMS Schedule Token Server Class objects with ReadFromString class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a6d1e648-8162-270e-4bc2-3d1c8a1b4877
document_version_independent_id: bef67f22-4ec8-868d-3bab-ae9f5a369110
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 90f209c3-ff15-e6ff-5736-de27bf11acdc
---

# ReadFromString Method - Configuration Manager | Microsoft Learn

The `ReadFromString` Windows Management Instrumentation (WMI) class method, in Configuration Manager, reads [SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class) objects from an interval string.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 ReadFromString(
   String StringData,
     SMS_ScheduleToken TokenData[]
);
```

#### Parameters

`StringData` Data type: `String`

Qualifiers: [in]

The interval string (details in table below).

`TokenData` Data type: `SMS_ScheduleToken` Array

Qualifiers: [out]

[SMS_ScheduleToken Server WMI Class](sms_scheduletoken-server-wmi-class) objects.

```

The ScheduleToken class uses two DWORDs to store the schedule data.

Values for the first DWORD laid out as follows:

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +-----------+---------+---------+-------+-----------+-----------+
 |  Start    |  Start  |  Start  | Start |   Start   | Duration  |
 |  Minute   |  Hour   |  Day    | Month |   Year    | Minutes   |
 +-----------+---------+---------+-------+-----------+-----------+

Values for the second DWORD laid out as follows:

 SCHED_TOKEN_RECUR_NONE

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-------------------------------------+
 | Duration| Duration|Flags|           Unused                  |U|
 | Hours   | Days    |     |                                   |T|
 |         |         |     |                                   |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_INTERVAL

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----------+---------+---------+-----+
 | Duration| Duration|Flags|  Num of   |  Num of |  Num of |   |U|
 | Hours   | Days    |     |  Minutes  |  Hours  |  Days   |   |T|
 |         |         |     |           |         |         |   |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_WEEKLY

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----+-----+-------------------------+
 | Duration| Duration|Flags| Week|# of |       Unused          |U|
 | Hours   | Days    |     | Day |Weeks|                       |T|
 |         |         |     |     |     |                       |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_MONTHLY_BY_WEEKDAY

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----+-------+-----+-----------------+
 | Duration| Duration|Flags| Week|Num of |Week |     Unused    |U|
 | Hours   | Days    |     | Day |months |Order|               |T|
 |         |         |     |     |       |     |               |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_MONTHLY_BY_DATE

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+---------+-------+-------------------+
 | Duration| Duration|Flags|   Date  |Num of |       Unused    |U|
 | Hours   | Days    |     |         |months |                 |T|
 |         |         |     |         |       |                 |C|
 +---------+---------+-----+-------------------------------------+

```

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).