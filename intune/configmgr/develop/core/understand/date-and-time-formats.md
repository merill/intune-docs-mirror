---
layout: Conceptual
title: Date and Time Formats - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/date-and-time-formats
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
description: When you write queries or compose reports from information that is stored in the Configuration Manager site database, you can express the date and time in any valid SQL format.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 96fd9001-573c-ee68-4b1e-62b8d942a2f1
document_version_independent_id: 0bb73167-636a-3fc1-dfb8-d32ef836d3e3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/date-and-time-formats.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/date-and-time-formats
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/date-and-time-formats.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 6d23121d-b12c-544a-b66d-9d81c7bc52d0
---

# Date and Time Formats - Configuration Manager | Microsoft Learn

Actions, in Configuration Manager, that include date and time values are common, such as get current date and time, 50 days from today is what date?, or find out what day of the week falls on a certain date. When you write queries or compose reports from information that is stored in the Configuration Manager site database, you can express the date and time in any valid SQL format. An example is any expression that has a SQL Server `datetime` data type or that can be converted implicitly, such as an appropriately formatted character string (for example, "1998.10.31").

The times that are stored in the Configuration Manager site database can be local or in Coordinated Universal Time (UTC). Status Message Viewer can convert to local time, but queries and reports cannot. What you see might be seven hours later than expected, if local time is Pacific Daylight time. Therefore, the user must be aware of the following:

Status messages are all in UTC.

Offers can be in UTC or local time, depending on a switch that is set in the Configuration Manager console. The property in `SMS_Advertisement` is `AssignedScheduleIsGMT` (`true`/`false`).

Inventory is always in local time.

This property is `lazy`, but you can view it by using WBEMtest.

Depending on the context, you might encounter time notations in the following format:

19981118175900000000+\*\*\*

The following information corresponds to the values in the previous example.

| Value | Description |
| --- | --- |
| 1998 | Year |
| 11 | Month |
| 18 | Day |
| 1759 | Hour |
| 00 | Second |
| 000000 | Microsecond |
| +\*\*\* | Offset from local time |

The following table lists valid `datetime` formats that you can use.

| Style number without century | Style number with century | Type | Output Style |
| --- | --- | --- | --- |
| - | 0 or 100 | Default | mon dd yyyy hh:mm |
| 1 | 101 | USA | mm/dd/yyyy |
| 1 | 102 | ANSI | yyyy.mm.dd |
| 3 | 103 | British/French | dd/mm/yyyy |
| 4 | 104 | German | dd.mm.yyyy |
| 5 | 105 | Italian | dd-mm-yyyy |
| 6 | 106 | – | dd-mon-yyyy |
| 7 | 107 | – | mon.dd.yyy |
| – | 8 or 108 | – | hh:mm:ss |
| – | 9 or 109 | – | mon dd yyyy hh:mi:ss:mmmAM (or PM) |
| 10 | 110 | USA | mm-dd-yy |
| 11 | 111 | JAPAN | yy/mm/dd |
| 12 | 112 | ISO | yymmdd |
| – | 13 or 113 | – | dd mon yyyy hh:mi:ss:mmm (24 h) |
| 14 | 114 | – | hh:mi:ss:mmm (24 h) |

Besides full `datetime` formats, you can also use `datepart` formats, which are also valid for Query Builder or for writing reports from the Configuration Manager site database. `Datepart` formats provide only part of the full `datetime` format (for example, the year or just the day of the month). The following table lists valid `datepart` formats.

| Datepart value | Abbreviations | Limits |
| --- | --- | --- |
| Year | Yy | 1753-9999 |
| Month | Mm | 1-12 |
| Day | Dd | 1-31 |
| Hour | Hh | 1-23 |
| Minute | Mi | 0-59 |
| Second | Ss | 0-59 |
| Millisecond | Ms | 0-999 |