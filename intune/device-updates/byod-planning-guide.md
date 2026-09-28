---
layout: Conceptual
title: Admin checklist for software updates on BYOD in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/byod-planning-guide
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Guidance and advice for administrators that create and manage software updated for BYOD and personally owned devices using Microsoft Intune. See tasks and settings that can manage updates on personal devices on Android and iOS/iPadOS platforms.
ms.date: 2025-04-07T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: ahamil, talima
locale: en-us
document_id: 46aa1a5b-9713-b6e5-7f00-72748f34b9d5
document_version_independent_id: 46aa1a5b-9713-b6e5-7f00-72748f34b9d5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/byod-planning-guide.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/byod-planning-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/byod-planning-guide.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 971ee4ec-7f30-b260-0551-cf2817724fd9
---

# Admin checklist for software updates on BYOD in Microsoft Intune - Microsoft Intune | Microsoft Learn

As organizations embrace a hybrid and remote workforce, admins are challenged with controlling and managing software updates on devices owned by users. These devices are often called BYOD (bring your own device) or personally owned devices. When devices are organization owned, IT admins manage software updates. On personal devices, IT admins typically don't have any control of software updates.

By default, when a new update is available for unmanaged devices (not enrolled in Intune), users receive notifications and/or see the latest updates available on their devices (Settings &gt; Software Updates). The timing of these updates varies depending on the carrier, OEM, and the device itself. At any time, users can check for updates themselves.

To help manage the software updates on unmanaged devices, there are Intune policies and features that can help. This section lists the Microsoft-recommended policies to install software updates on unmanaged devices.

This article applies to:

- Android Enterprise
- iOS/iPadOS

Tip

If your devices are organization owned, then go to the software updates planning guides for:

- [Managed Android devices](android/planning-guide)
- [Supervised iOS/iPadOS devices](apple/planning-guide-ios-ipados)
- [Managed macOS devices](apple/planning-guide-macos)

## Create enrollment restrictions

Users can enroll their personal devices in Microsoft Intune.

- When users enroll their personal Android devices, these devices automatically get a work profile. Any policies you create apply to the work profile, not the personal profile. For information on the Android enrollment option for personal devices, go to [Android enrollment guide](../device-enrollment/android/guide).
- When they enroll iOS/iPadOS devices, the behavior depends on the enrollment option you use. For information on the different iOS/iPadOS enrollment options for personal devices, go to [iOS/iPadOS enrollment guide](../device-enrollment/apple/guide-ios-ipados).

✅ Create an enrollment restrictions policy that requires a minimum and maximum operating system version. This policy helps create a good baseline for new enrollments.

The following example shows an enrollment device platform restrictions policy for Android Enterprise devices:

![Screenshot that shows enrollment restrictions policy for Android devices in the Microsoft Intune admin center.](android/media/planning-guide/enrollment-restrictions-policy.png)

When users enroll their personal devices, this policy checks the version info. If the devices are outside the versions you enter, then they're prevented from enrolling.

For more information on this feature, go to [Device platform restrictions in Intune](../device-enrollment/create-platform-restrictions).

## Create compliance policies

Compliance policies help keep devices up-to-date. If a device isn't using a version you define, then the device is marked as noncompliant. Noncompliant devices are shown in the Microsoft Intune admin center.

✅ Create compliance policies. Use the built-in reporting to see noncompliant devices and see the individual settings that aren't compliant.

In your compliance policy, you can:

- Notify the user that the OS version doesn't meet your requirements.
- Allow a grace period before the device is marked noncompliant, to allow them time to upgrade.

![Screenshot that shows a compliance policy with actions for noncompliance in the Microsoft Intune admin center.](android/media/planning-guide/compliance-policy-actions-noncompliance.png)

If you combine your compliance policies with Conditional Access (CA), then you can block users from resource access until they meet the OS version requirements.

For more information on compliance policies, go to:

- [Create a compliance policy in Intune](../device-security/compliance/create-policy)
- [Configure actions for noncompliant devices in Intune](../device-security/compliance/configure-noncompliance-actions)
- [Monitor results of your compliance policies in Intune](../device-security/compliance/monitor-policy)

## Use app protection policies

✅ Use app protection policies on unmanaged personal devices that access organization resources.

At the app level, you can use app protection policies to determine the minimum OS and patch versions.

When users open or resume an app that's managed by you, the app protection policy can prompt users to upgrade the OS. In the policy, if the version they're running doesn't meet your requirements, then you can warn users that a new OS version is required, or block access:

![Screenshot that shows device-based conditions in an app protection policy in the Microsoft Intune admin center.](android/media/planning-guide/app-protection-policy-device-conditions.png)

For more information on app protection policies, go to [App protection policies overview](../app-management/protection/overview).

## Use custom notifications

✅ Create a custom notification to alert users of upcoming OS version requirements. Use this feature to proactively communicate to users to update their devices so they don't lose access:

![Screenshot that shows a custom notification message in the Microsoft Intune admin center.](android/media/planning-guide/custom-notification.png)

Remember, if the OS updates can't be forced or controlled, which is common on personal devices, then end users need to update their own devices.

For more information on these features, go to:

- [Conditional launch actions with app protection policies in Intune](../app-management/protection/configure-conditional-launch)
- [Using custom notifications in Intune](../device-management/actions/send-custom-notification)