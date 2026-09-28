---
layout: Conceptual
title: How to Use Intune in Environments Without Google Mobile Services - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/manage-without-gms
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
description: Learn how to use Intune in environments without Google Mobile Services.
ms.date: 2024-10-28T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: priyar
locale: en-us
document_id: a6c09a43-d0e8-ba2d-bb4e-695dc47e42aa
document_version_independent_id: a6c09a43-d0e8-ba2d-bb4e-695dc47e42aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/manage-without-gms.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/manage-without-gms
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/manage-without-gms.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c801c09c-e467-ecdb-ec58-e19149465bc0
---

# How to Use Intune in Environments Without Google Mobile Services - Microsoft Intune | Microsoft Learn

Microsoft Intune uses Google Mobile Services (GMS) to communicate with the Microsoft Intune company portal when managing Android devices. In some cases, devices can temporarily or permanently not have access to GMS. For example, a device might ship without GMS, or the device might be connecting to a closed network where GMS isn't available. This document summarizes the differences and limitations you can observe when installing and using Intune to manage Android devices without GMS.

Note

These GMS related limitations also apply to Device Administrator management and Android (AOSP) Management.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Install the Intune Company Portal app without access to the Google Play Store

### For users outside of People's Republic of China

If Google Play isn't available, Android devices can download the [Microsoft Intune Company Portal for Android](https://www.microsoft.com/download/details.aspx?id=49140) and sideload the app. When installed this way, the app doesn't receive updates or fixes automatically. You must be sure to regularly update and patch the app manually.

### For users in People's Republic of China

Because the Google Play Store is currently not available in People's Republic of China, Android devices must obtain apps from Chinese app marketplaces. For more information, see [Install the Company Portal app in People's Republic of China](../user-help/company-portal/install-android-china).

## Limitations of Intune management when GMS is unavailable

### Unavailable Intune features

Some Intune features rely on components of GMS such as the Google Play store or Google Play services. Because these components are not available in environments without GMS, the following features in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) might be unavailable.

| Scenario | Features |
| --- | --- |
| Device compliance policies | When you create or edit compliance policies for Android device administrator, all options listed under **Google Play Protect** are unavailable. |
| App protection policies (conditional launch) | **Play integrity verdict**, **Require threat scan on apps**, and **Max Company Portal version age (days)** are device conditions that can't be used for conditional launch. |
| Client apps | Apps of type **Android** are not available. Use **Line-of-business app** instead to deploy and manage apps. |
| Mobile Threat Defense (MTD) | Work with your MTD vendor to understand if their solution is integrated with Intune, if it's available in the region of interest, and if it relies on GMS. |

### Some tasks can be delayed

In environments where GMS is available, Intune relies on push notifications to speed tasks to finish. For example, if you try to remotely wipe the device, notifications generally get to the device in seconds. In conditions where GMS isn't available, push notifications might also not be available.

All Android devices enrolled with device administrator or Android (AOSP) management report to Intune every 8 hours. For example, if a device reports to Intune at 1 PM and the remote tasks are issued at 1:05 PM, then Intune contacts the device at 9 PM to complete the tasks.

In conditions where GMS isn't available:

- If the device is enrolled with device administrator and running the Company Portal app version 5.0.5655.0 and newer, then Intune tries to check for new tasks and notifications approximately every 15 minutes.
- If the device is enrolled with Android (AOSP) management and running the Intune app version 24.02.4 and newer, then Intune tries to check for new tasks and notifications normally every 15 minutes, however some tasks on AOSP devices may take up to 8 hours to complete.

This frequency is also affected by the device manufacturer, device usage patterns, and whether battery optimization is enabled for the Company Portal or Intune apps.

For more information on Intune policy refresh intervals, go to [Common questions, answers, and scenarios with Intune policies](../device-configuration/troubleshoot-device-profiles).

The following tasks can require up to 8 hours to finish:

**Microsoft Intune admin center**:

- Full wipe
- Selective wipe
- New or updated app deployments
- Remote lock
- Passcode reset

**Intune Company Portal app for Android**:

- Remote device removal
- Device reset
- Installation of available line-of-business apps

**Intune app for Android (AOSP)**:

- Remote device removal
- Device reset

**Intune Company Portal website**:

- Device removal (local and remote)
- Device reset
- Device passcode reset

If the device recently enrolled, the compliance, non-compliance, and configuration check-in runs more frequently. For more information on device check-ins, see [Common questions, issues, and resolutions with device policies and profiles in Microsoft Intune](../device-configuration/troubleshoot-device-profiles).