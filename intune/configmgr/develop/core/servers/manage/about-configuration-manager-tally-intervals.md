---
layout: Conceptual
title: Configuration Manager Tally Intervals - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: The Configuration Manager is configured with 16 default tally intervals, which are maintained in the site control file shown in the following table.
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 96e4dad0-38c5-a41e-b8be-a66c144ed63a
document_version_independent_id: ed80742e-4b36-2c77-a564-dcc07894bfd2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6a8483a3-83ab-a446-e536-f1d2789e1d66
---

# Configuration Manager Tally Intervals - Configuration Manager | Microsoft Learn

Configuration Manager is configured with 16 default tally intervals. The intervals for a site are maintained in the site control file. The values are stored in the order that is shown in the following table. For information about accessing these values in the site control file, see the example at the end of this topic.

Note

You can use only the tally intervals that are listed in the table in your queries. When you use a tally interval that is not from the list, an object is returned that contains no data.

| Schedule | Tally Interval | Class |
| --- | --- | --- |
| Since 12:00AM | 0001128000100008 | SMS\_ST\_RecurInterval |
| Since 04:00AM | 0081128000100008 | SMS\_ST\_RecurInterval |
| Since 08:00AM | 0101128000100008 | SMS\_ST\_RecurInterval |
| Since 12:00PM | 0181128000100008 | SMS\_ST\_RecurInterval |
| Since 04:00PM | 0201128000100008 | SMS\_ST\_RecurInterval |
| Since 08:00PM | 0281128000100008 | SMS\_ST\_RecurInterval |
| Since Sunday | 0001128000192000 | SMS\_ST\_RecurWeekly |
| Since Monday | 00011280001A2000 | SMS\_ST\_RecurWeekly |
| Since Tuesday | 00011280001B2000 | SMS\_ST\_RecurWeekly |
| Since Wednesday | 00011280001C2000 | SMS\_ST\_RecurWeekly |
| Since Thursday | 00011280001D2000 | SMS\_ST\_RecurWeekly |
| Since Friday | 00011280001E2000 | SMS\_ST\_RecurWeekly |
| Since Saturday | 00011280001F2000 | SMS\_ST\_RecurWeekly |
| Since 1st of month | 000A470000284400 | SMS\_ST\_RecurMonthlyByDate |
| Since 15th of month | 000A4700002BC400 | SMS\_ST\_NonRecurring |
| Since site installation | 0001128000080008 | SMS\_ST\_NonRecurring |

The **Schedule** column is the beginning value of the tally interval. You interpret the beginning value of the tally interval as, "Give me the tallies since Monday." The end of the tally interval is always the current time. The complete tally interval is the same as saying, "Give me all the tallies from Monday to the current time."

The classes listed in the tally interval table are embedded schedule token classes that you can use to interpret the interval string. You use the `ReadFromString` method of the `SMS_ScheduleMethods` class to interpret an interval string. This method breaks the interval string into its components and returns the appropriate embedded object.

Tally intervals are commonly used in component (SMS\_ComponentSummarizer) and site detail (SMS\_SiteDetailSummarizer) summarizer queries. For more information, see [About Configuration Manager Status Summarizers](about-configuration-manager-status-summarizers).