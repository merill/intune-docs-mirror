---
layout: Conceptual
title: View Software Update Reports for Apple Devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/apple/monitor-reports
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Track Apple device update status in real time with Intune's declarative software update reporting. Learn how Microsoft Intune surfaces update changes directly from managed Apple devices.
ms.date: 2025-10-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: cd9d85c7-d752-2ad3-2761-cb660ba181d3
document_version_independent_id: cd9d85c7-d752-2ad3-2761-cb660ba181d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/apple/monitor-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/apple/monitor-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/apple/monitor-reports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: 70f3efbf-00a9-274a-686b-60a2bf58b498
---

# View Software Update Reports for Apple Devices - Microsoft Intune | Microsoft Learn

Microsoft Intune uses Apple's declarative software update reporting model to provide near real-time status updates for managed Apple devices. This model enables Intune to surface update status directly from each device whenever its software update status changes.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Software update reporting for Apple devices in Intune requires the following platforms:
> 
> - iOS/iPadOS 17.0 and later
> - macOS 14.0 and later
> 

## View software update reports

Intune provides several reports to help you monitor and troubleshoot software updates across your Apple device fleet:

- **Summary report**: Shows a high-level view of update status across macOS, iOS, and iPadOS devices, including the most recently available update version and release date. Intune checks with Apple once per day to identify newly available updates.
- **Organizational report**: Displays pending and current update details across all managed Apple devices.
- **Failures report**: Lists update failures across macOS, iOS, and iPadOS devices, including failure reasons and timestamps.
- **Per-device report**: Focuses on the update status for an individual device.

Select a tab to learn more about each report.

# [Summary report](#tab/summary)
With the Apple software update **Summary** view, you can monitor details about pending and current software update status across your fleet of managed iOS, iPadOS, and macOS devices.

This summary view presents the following information for each device platform:

- When you last refreshed the summary
- The latest update that's available for the platform
- When the latest update became available
- A chart view that identifies device counts for each software update status category

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Device management** &gt; **Apple updates** &gt; **Summary**.

The following image shows a blank summary report with no device details available, captured from a newly provisioned Intune tenant:

![Screen capture that shows the Apple software update Summary view.](media/monitor-reports/update-summary-report.png)

# [Organizational report](#tab/organizational)
As an organizational report, use the **Apple software update report** to view details about the current software update status across your fleet of managed iOS, iPadOS, and macOS devices.

Details available in this report include:

- When the report view was last generated (refreshed)
- A chart view that identifies device counts for each software update status type
- A list of devices with their most recent update status, which includes the device name, platform, current OS version, pending OS version, and more

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Device management** &gt; **Apple updates** &gt; **Reports**.
2. Select the tile **Apple software update report**.
3. Select the **Generate** button to populate the report view.

This report supports filters to focus results by platforms and update installation status. The report also includes an option to **Export** the report details as a comma-separated values (.csv) file.

The following image shows a blank report with no device details available, captured from a newly provisioned Intune tenant.

![Screen capture that shows the Apple software update report.](media/monitor-reports/software-update-report.png)

# [Failures report](#tab/failures)
With the **Apple software update failures** operational report, you can view details for your managed iOS, iPadOS, and macOS devices that report update failures.

Details available in this report include:

- A list of devices with their name, platform, current OS version, pending OS version, and more
- Details about the failure reason and timestamp of the last failure

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Monitor** &gt; **Apple software update failures**.

The reports include the option to **Refresh** the report view and to **Export** the report details as a comma-separated values (.csv) file.

# [Per-device report](#tab/per-device)
Intune per-device reports provide a software updates view that focuses on a single device.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; select either **iOS/iPadOS** or **macOS**, then select a device.
2. On the device **Overview** page, expand **Monitor**and then, depending on the type of device you're viewing, select the report:
    - For iOS and iPadOS, select **iOS software updates**.
    - For macOS, select **macOS software updates**.

In the per-device view, Intune displays the following information about the device's update status as reported by the device:

- Current OS version
- Current OS build
- Latest available update for this device
- Pending OS version
- Pending Build Version
- Install Reason
- Install State
- Last Reported Time - This value is the last time that the device synced with Intune.

The following example is taken from the *macOS software updates* report:

![Screen capture that shows the per-device report for a macOS device](media/monitor-reports/per-device-macos-software-updates.png)

---