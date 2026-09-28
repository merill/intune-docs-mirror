---
layout: Conceptual
title: Use maintenance windows - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/use-maintenance-windows
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
description: Use collections and maintenance windows to effectively manage clients in Configuration Manager.
ms.date: 2025-07-25T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 41833b7b-2c49-1d57-72cb-b177ea054c2f
document_version_independent_id: 8bb9cc02-2b06-c8a0-1d45-693c1ddd60f5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/use-maintenance-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/use-maintenance-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/use-maintenance-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dcb2e747-0c7a-fdc7-925d-ea644c79fa2f
---

# Use maintenance windows - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use maintenance windows to define when Configuration Manager can run impacting tasks on devices. Maintenance windows help make sure that client configuration changes occur during times that don't affect productivity. With Software Center, users can see the device's next maintenance window on the **Installation status** tab. 

The following tasks support maintenance windows:

- Application and package deployments
- Software update deployments
- Compliance settings deployment and evaluation
- OS and custom task sequence deployments

Configure maintenance windows with an effective date, a start and end time, and a recurrence pattern. The maximum duration of a window has to be less than 24 hours. The console doesn't allow a single maintenance window longer than 24 hours. For example, if you want to allow maintenance all day Saturday and Sunday, then create two 24-hour maintenance windows for each day.

By default, computer restarts caused by a deployment aren't allowed outside of a maintenance window, but you can override the default. Maintenance windows affect only the time when the deployment runs. Deployments that you configure to download and run locally can download content outside of the window.

When a client is a member of a device collection that has a maintenance window, a deployment runs only if its maximum allowed run time doesn't exceed the duration of the window. If the deployment fails to run, the client generates an alert. It then reruns the deployment during the next scheduled maintenance window that has available time.

Tip

A *maintenance window* is for a client. A *service window* is for a site server. For more information, see [Service windows for site servers](../../../servers/manage/service-windows).

## Multiple maintenance windows

When a client computer is a member of multiple device collections that have maintenance windows, these rules apply:

- If the maintenance windows don't overlap, the client treats them as two independent maintenance windows.
- If the maintenance windows overlap, the client treats them as a single window for the entire time of both windows. For example, you create two maintenance windows on a collection. The first is effective from 6:00 to 7:00, and the second is effective from 6:30 to 7:30. Because they overlap by 30 minutes, the effective duration of the combined maintenance window is 90 minutes from 6:00 to 7:30.

When a user installs an application from Software Center, the client starts it immediately. It prioritizes the user's intent over the administrator's.

If an application deployment with a purpose of **Required** reaches its installation deadline during the non-business hours that a user configures in Software Center, the client installs the application. It prioritizes the administrator's intent over the user's.

By default, with multiple maintenance windows, the client only installs software updates during **Software Update** type windows. It ignores any **All deployments** maintenance windows, unless they're the only type. You can configure this behavior with the following client setting in the **Software updates** group: **Enable installation of software updates in "All deployments" maintenance window when "Software Update" maintenance window is available**. For more information, see [About client settings](../../deploy/about-client-settings#bkmk_SUMMaint).

Note

This setting also applies to maintenance windows that you configure to apply to **Task sequences**.

If the client only has an **All deployments** window available, it still installs software updates or task sequences in that window.

## Configure maintenance windows

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace.
2. Select the **Device Collections** node, and then select a collection.

    Note

    You can't create maintenance windows for the **All Systems** collection.
3. On the **Home** tab of the ribbon, in the **Properties** group, choose **Properties**.
4. Switch to the **Maintenance Windows** tab, and select the **New** icon.

    1. Specify a **Name** to uniquely identify this maintenance window for the collection.
    2. Configure the **Time** settings:

        - **Effective date**: The date when the maintenance windows starts. The default is the current date.
        - **Start** and **End**: The start and end times of the maintenance window. It calculates the **Duration** for the window. The minimum duration is five minutes, and the maximum is 24 hours. The default duration is three hours, from 01:00 to 04:00.
        - **Coordinated Universal Time (UTC)**: Enable this option for the client to interpret the start and end times in the UTC time zone. For regionally or globally distributed devices in the same collection, this option sets the maintenance window to occur simultaneously on all devices in the collection. Disable this option for the client to use the device's local time zone. This option is disabled by default.
    3. Configure the recurrence pattern. The default is once per week on the current day of the week.

        Note

        Starting in version 2207, you can offset monthly maintenance window schedules to better align deployments with the release of monthly security updates. For example, using an offset of two days after the second Tuesday of the month, sets the maintenance window for Thursday.
    4. **Apply this schedule to**: By default the window applies to **All deployments**. You can select either **Software updates** or **Task sequences** to further control what deployments run during this window.

        Tip

        If you configure multiple maintenance windows of different types on the same collection, make sure you understand the client behaviors. For more information, see Multiple maintenance windows.
5. Select **OK** to save and close the window.

The **Maintenance Windows** tab of the collection properties displays all configured windows.

## Use PowerShell

You can use PowerShell to configure maintenance windows. For more information, see the following articles:

- [Get-CMMaintenanceWindow](/en-us/powershell/module/configurationmanager/get-cmmaintenancewindow)
- [New-CMMaintenanceWindow](/en-us/powershell/module/configurationmanager/new-cmmaintenancewindow)
- [Remove-CMMaintenanceWindow](/en-us/powershell/module/configurationmanager/remove-cmmaintenancewindow)
- [Set-CMMaintenanceWindow](/en-us/powershell/module/configurationmanager/set-cmmaintenancewindow)

## Known Issues

### Using Offset Maintenance Windows in the last week of the month

Offset Maintenance Windows scheduled in the last week of the month may encounter the following scheduling discrepancies:

- If the offset value causes the start date to fall in the following month, it will be adjusted to the end of the current month.
- If the offset value causes the start date to fall on the last day of the current month, no Maintenance Window will be scheduled for that month.

Note

The issues with Offset Maintenance Windows scheduled in the last week of the month is resolved in version 2503. Offset values that cause the Maintenance Window to be scheduled on or after the last day of the current month now schedule as expected.

### UTC Maintenance Windows and Daylight Saving Time

When calculating the difference from UTC to local time, the client will use the active [bias](/en-us/exchange/client-developer/web-service-reference/bias) from the "Effective date" of the maintenance window to calculate the local time from the UTC time:

- If Daylight Saving Time (DST) is active on the effective date, then this bias from UTC will always be used, causing the Maintenance Window to open an hour earlier than expected when DST ends.
- If Daylight Saving Time (DST) is not active on the effective date, then this bias from UTC will always be used, causing the Maintenance Window to open an hour later than expected when DST starts.