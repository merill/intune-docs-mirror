---
layout: Conceptual
title: Reports for Windows Driver Update Policies reports - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-driver-updates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to use Intune reports to monitor Windows driver updates for devices assigned to Windows Driver update policies.
ms.date: 2026-01-12T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: zadvor
locale: en-us
document_id: 37fc330f-79c1-e224-109f-c52c76734832
document_version_independent_id: 37fc330f-79c1-e224-109f-c52c76734832
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/monitor-driver-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/monitor-driver-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/monitor-driver-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bb130aac-68f5-7f5a-4bba-340e62d91b54
---

# Reports for Windows Driver Update Policies reports - Microsoft Intune | Microsoft Learn

Intune offers integrated reports to view detailed status for Windows driver updates for devices assigned to Windows Driver update policies. To use these reports, you must first configure the prerequisites and policies that support data collection from devices. These reports are applicable to Windows 10 and Windows 11.

## Before you begin

- Ensure your environment meets the prerequisites for managing Windows driver updates. For details, see [Manage Windows driver updates: Prerequisites](manage-driver-updates#prerequisites).

## Accessing driver updates reports

The data in the Intune reports for Windows Driver update policies is used only for these reports and doesn't appear in other Intune reports. The following reports are available:

- Windows Driver updates summary
- Windows Driver updates report
- Windows Driver update failures

Select a tab to learn more about each report.

# [Driver updates summary](#tab/summary)
The *Windows Driver updates summary* report provides an overview of the status of driver updates across all your Windows Driver update policies.

To access the Windows Driver updates summary report:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Windows Updates**.
2. Select the **Summary** tab and find the **Windows Driver updates** section: [![Screen capture of the Windows Driver Updates summary page.](media/monitor-driver-updates/driver-updates-summary.png)](media/monitor-driver-updates/driver-updates-summary.png#lightbox)

This report shows the status of driver updates for each policy. It displays the number of devices that are up-to-date (*Success*), failed (*Error*), paused (*Paused*), etc. for the driver updates in that policy. However, each device is only represented once in a single status column, based on the worst status across all of the updates that apply to that device.

Intune ranks the following statuses in order of priority, from best (Success) to worst (NeedsReview):

- **Success**: All applicable driver updates have installed successfully.
- **In progress**: At least one update remains in progress, and none have been paused, failed, or worse.
- **Paused**: At least one update has been paused, but none have failed to install, been cancelled, or are pending review.
- **Error**: At least one update failed to install, but none are cancelled or pending review.
- **Cancelled**: At least one update has been declined, but none are pending review.
- **NeedsReview**: One or more updates are new to the policy and pending review to approve or decline.

For example: A policy might have three applicable driver updates for an assigned device. If one of the three fails to install on that device while the other two updates install successfully, the device is identified by adding one to the *Error* column. Once all three updates install successfully, the device is represented by adding one to the *Success* column and reducing the count of the *Error* column by one.

This report doesn't support drilling in for more details about devices, driver updates, or policy details.

# [Driver updates](#tab/updates)
The Windows driver updates report allows you to select a single driver update and view details about the policies in which it's applicable for a device. This report provides information about the driver from all your driver update policies, offering a different perspective than other reports, which only provide details specific to a single policy.

To access the Windows Driver updates report:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Windows Updates**.
2. Select the **Reports** tab and select the **Windows Driver Update Report** tile.

In the following screen capture, the report shows details for the driver update *Microsoft: APPLIANCES: 1.0.0.1*.

[![Screen capture of the Windows Driver updates report.](media/monitor-driver-updates/driver-updates-list.png)](media/monitor-driver-updates/driver-updates-list.png#lightbox)

To change the focus of this report to a different driver:

1. On the **Windows Driver updates** view, select **Select a driver update** to open the **Driver updates** pane.
2. The *Driver updates* pane displays a list of updates that are approved and applicable for at least one device from across all your driver update policies.
3. On the Driver updates pane, select a driver, and then **OK** to return to the Windows Driver updates report view that now shows information for the driver you selected, and select **Generate again** to update the report.

In the following screen capture, only four drivers remain applicable to devices with driver update policies, and those four updates are different versions of the same driver update.

[![Screen capture of Driver Updates pane of a driver update policy.](media/monitor-driver-updates/driver-updates-policy-detail.png)](media/monitor-driver-updates/driver-updates-policy-detail.png#lightbox)

### Column details

While most of the column details should be clear, the following warrant some explanation:

- **Update State**: This column presents the most recent status of the selected driver update, as reported by each device to which it applies. Further details can be found in the *Update Substrate*column.
    - **Cancelled**: The update was paused in the policy that applies to this device.
    - **Offering**: The update is approved, but the device hasn't yet installed it.
    - **Installed**: The update installed successfully.
    - **Needs attention**: There's an installation issue for the update on this device.
- **Policy**: This column identifies the name of the policy in which the update was approved.
- **Last Scan Time**: This column provides insight into when a device last checked for updates. This can help explain why approved updates haven't installed. For instance, if the last scan time is several weeks old, it may indicate that the device is either offline or unable to connect to scan for updates.

# [Update failures](#tab/failures)
Windows driver updates include a report on driver update failures.

To access the Windows Driver update failures report:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Monitor** &gt; **Driver update policies with alerts**.
2. When you select the report, you can view a list of your update policies and see a count of devices in each policy that have at least one driver update error.

By selecting that policy and entry, you can then view more information about the error, including:

- Device Name
- Driver Name
- Driver Class
- Alert Message
- Deployment Error Code
- UPN
- Intune Device ID

---

## Data retention

As devices across all your updates policies install the latest versions of a driver update, older driver update versions that are no longer needed by any device drops off the driver updates list. However, this isn't necessarily an immediate event. Reporting data for driver updates remains available until the end of a data retention period is reached. This period is six months since the last time an event for the update is received.

- If the update is approved and all applicable devices have installed the update, then six months after the last device updates is status, the update is removed from reporting details.
- Similarly, if an update is paused and shows no activity for the retention period, that update is also dropped from reporting details after six months. After an updates data ages out, if a paused update that remains applicable to a device is reapproved, subsequent status for that update begins to appear in reports. Previous data that aged out of reports won't be restored or available.