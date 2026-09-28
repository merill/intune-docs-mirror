---
layout: Conceptual
title: Discovered Apps - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/discovered-apps
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Understand details about the detected apps that Intune found on a device.
ms.date: 2025-12-03T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: arnab
ms.custom: 
locale: en-us
document_id: 510b2aa0-2681-516a-7f73-675077f46f13
document_version_independent_id: 510b2aa0-2681-516a-7f73-675077f46f13
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/discovered-apps.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/discovered-apps
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/discovered-apps.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d0e177d1-0d83-1866-de27-2f55c51e441d
---

# Discovered Apps - Microsoft Intune | Microsoft Learn

Tip

For Windows devices that need faster refresh cycles and richer app metadata, see [App inventory](deployment/enhanced-app-inventory). App inventory is the intended long-term replacement for Discovered apps and collects data multiple times per day with additional properties like install location, app size, and uninstall commands.

Intune **discovered apps** is a list of detected apps on the Intune enrolled devices in your tenant. It acts as a software inventory for your tenant. **Discovered apps** is a separate report from the [app installation](monitor-assignments) reports. For personal devices, Intune never collects information on applications that are unmanaged. On corporate devices, any app whether it's a managed app or not is collected for this report. The following table shows the expected behavior. In general, the report refreshes every seven days for each device, starting from its enrollment date. This refresh isn't performed weekly for the entire tenant. The only exception to this refresh cycle for the **Discovered apps** report is application information that the Intune Management Extension for Win32 Apps collects every 24 hours.

## Monitor discovered apps with Intune

Intune provides an aggregated list of detected apps on the Intune enrolled devices in your tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Monitor** &gt; **Discovered apps**.

Note

You can export the list of discovered apps to a *.csv* file by selecting **Export** from the **Discovered apps** pane.

The **Discovered apps** report provides the following details:

- Application name
- Platform
- Application version
- Device count
- Application publisher

Intune also provides the list of discovered apps for the individual device in your tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **All Devices**.
3. Select a device.
4. To view detected apps for this device, select **Discovered Apps** in the **Monitor** section.

## Details of discovered apps

The following list shows the app platform type. It also shows which apps are monitored for personal devices and for company-owned devices. The refresh cycle is included as well. For more information about app types supported by Intune, see [App types in Microsoft Intune](deployment/#app-types-in-microsoft-intune).

| Platform | For personally owned devices | For company-owned devices | Refresh cycle |
| --- | --- | --- | --- |
| Windows (Win32 Apps) NOTE: [Requires Intune Management Extension](../device-management/tools/management-extension-windows) on device | Not Applicable | Windows Installer apps on the device that appear in add/remove programs | Every 24 hours from device enrollment |
| Windows (Modern Apps) | Only managed modern apps | All modern apps installed on the device | Every seven days from device enrollment |
| Windows 8.1 | Only managed apps | Only managed apps | Every seven days from device enrollment |
| Windows RT | Only managed apps | Only managed apps | Every seven days from device enrollment |
| iOS/iPadOS | Only managed apps | All apps installed on the device except system apps (On iOS/iPadOS 26 and later, All apps installed on the device) | Every seven days from device enrollment |
| macOS | Only managed apps | All apps installed on the device | Every seven days from device enrollment |
| Android device administrator | Only managed apps | All apps installed on the device | Every seven days from device enrollment |
| Android Enterprise personally owned enrollment | Managed apps in the work profile and system apps | Not applicable | Every seven days from device enrollment |
| Android Enterprise corporate-owned enrollments | Not applicable | Apps installed in the work profile | Every seven days from device enrollment |
| AOSP enrollments | Not applicable | Not yet supported | Not applicable |

Note

- Windows co-managed devices, as shown in the [client apps](../configmgr/comanage/workloads#client-apps) workload in Configuration Manager, don't currently collect app inventory through the Intune Management Extension (IME) according to the schedule described earlier. To mitigate this issue, the [client apps](../configmgr/comanage/workloads#client-apps) workload in Configuration Manager should be switched to Intune for the IME to be installed on the device (IME is required for Win32 inventory and PowerShell deployment). Any changes or updates on this behavior are announced in [in development](../whats-new/in-development) and/or [what's new](../whats-new/).
- Software inventory collection for Discovered apps on Windows has an initial delay up to seven days for Windows (Win32 apps) applications on new devices that don't have a Microsoft Entra ID user signed in to the device.
- Personally owned macOS devices enrolled before November 2019 might continue to show all apps installed on the device until the devices are enrolled again.
- Android Open Source Project (AOSP) enrollments don't display discovered apps.
- On Android Enterprise personally owned work profile devices, system apps are automatically associated with the work profile. System apps are apps that the Android operating system or device manufacturer consider essential for correct operation of the device. These apps are included in the Discovered Apps report, even if they aren't visible to the end user in the "Work" tab. To view the list of system apps that might be reported, go to **Settings** &gt; **Apps** &gt; **Show system apps** on the device. For more information, see [Google's Android Enterprise documentation (opens in a new page)](https://source.android.com/docs/devices/admin/implement#default-work-apps).
- If you use a Mobile Threat Defense partner with Intune, [App Sync data](../device-security/mobile-threat-defense/enable-connector) is sent to the partner based on the device check-in interval. Don't confuse this interval with the refresh interval for the Discovered Apps report.
- When you use the iOS or macOS Restricted apps setting, Intune collects but doesn't store the full app inventory for personally owned devices.

The number of discovered apps might not match the app install status count. Possibilities for inconsistencies include:

- Changing the targeting of an installed managed app can cause the install count in the status pane to decrement, but the app remains in detected apps.
- Targeting multiple instances of the same app in a tenant results in different counts due to potential overlap of users or devices. Each instance of the app counts overlapping users, but discovered apps show duplicated counts.
- Discovered apps and app status are collected at different time intervals, which could cause a discrepancy in the app counts.