---
layout: Conceptual
title: Move from Android device administrator to mobile application management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/migrate-to-application-management
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- intune-scenario
ms.subservice: enrollment
description: Use Microsoft Intune to set up mobile application management, an alternative option to Android device administrator that focuses on app protection and doesn't require device enrollment.
ms.date: 2024-06-27T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: esalter
locale: en-us
document_id: 2c594f95-82e2-cec5-e710-265339861aed
document_version_independent_id: 2c594f95-82e2-cec5-e710-265339861aed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/migrate-to-application-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/migrate-to-application-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/migrate-to-application-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 82e2ecfe-bb3f-7953-850a-b663a5d52c7f
---

# Move from Android device administrator to mobile application management - Microsoft Intune | Microsoft Learn

**Applies to Android**

This article describes how to move from Android device administrator management to mobile application management in Microsoft Intune, and contains recommendations and best practices for a successful transition as [Microsoft Intune ends support for Android device administrator](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

There are two ways to utilize mobile application management in Intune: with device enrollment or without device enrollment. In this article, you'll learn how to set up *mobile application management without device enrollment* to manage apps and data on personal devices. We recommend this option for organizations that don't need mobile device management (MDM) capabilities like Wi-Fi deployment or email configuration profiles. If your organization has dependencies that require device management on personal devices, we recommend moving to [Android Enterprise personally owned work profile management](migrate-device-admin-to-work-profile) instead.

## Prerequisites

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> You need the following Intune permissions to set up and enforce mobile application management:
> 
> - Managed apps/Assign
> - Managed apps/Create
> - Managed apps/Delete
> - Managed apps/Read
> - Managed apps/Update
> - Managed apps/Wipe
> 
> 
> The built-in [Application Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#application-manager) role has sufficient permissions for mobile application management. You can also add [scope tags](../../fundamentals/role-based-access-control/scope-tags) to policies to control object visibility among Intune admin users.

Important

The Intune Company Portal app must be installed on devices. It enables device users to receive app protection policies.

## Step 1: Configure policies for mobile application management

Create mobile application management policies in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Within these policies you can, for example, allow or block app features such as *copy and paste*. For more app protection settings and capabilities in Intune, see:

- [Android app protection policy settings in Microsoft Intune](../../app-management/protection/ref-settings-android): Describes the settings you can configure in an app protection policy.
- [Intune protected apps](../../app-management/ref-protected-apps#microsoft-apps): Lists apps that support app protection policies.

The following table lists configurations commonly used with Android device administrator management and similar mobile application management settings to consider using going forward.

Tip

Although similar, the mobile app management policies and settings listed in this table don't neccessarily function the same way as the Android device administrator ones you're used to. Review the linked resources to compare and evaluate policies and settings.

| Configuration | Android device administrator policy setting | Mobile application management policy setting | More information |
| --- | --- | --- | --- |
| Conditional Access | Use [device-based Conditional Access policies](../../device-security/conditional-access-integration/create-app-based-policy). | Use [app-based Conditional Access policies](../../device-security/conditional-access-integration/create-app-based-policy). | Before you unenroll devices, consider updating your device-based Conditional Access policies to include an `or` condition for app-based Conditional Access policies. Otherwise, device users could be in an interim state without MDM or mobile application management enforced. |
| Prevent copy and paste | **Restrict copy and paste (Knox only)** Setting available in [Configuration policy &gt; General](../../device-configuration/templates/ref-device-restrictions-android#general). | **Restrict cut, copy, and paste between other apps** Setting available in [App protection policy &gt; Data protection](../../app-management/protection/ref-settings-android#data-protection). |  |
| Enforce password | Password settings vary depending on policy type used.  Settings available in [Configuration policy &gt; Password](../../device-configuration/templates/ref-device-restrictions-android#password) and [Compliance policy &gt; Device security](../../device-security/compliance/ref-android-administrator-settings#device-security). | **PIN for app access** Setting available in [App protection policy &gt; Access requirements](../../app-management/protection/ref-settings-android#access-requirements). |  |
| Enforce minimum and maximum OS version | OS version settings vary depending on policy type used.  Settings available in [Compliance policy &gt; Operating system version](../../device-security/compliance/ref-android-administrator-settings#operating-system-version) and [Enrollment &gt; Device platform restriction](../create-platform-restrictions#create-a-device-platform-restriction). | **Min OS version** and **Max OS version** Settings available in [App protection policy &gt; Conditional launch](../../app-management/protection/ref-settings-android#conditional-launch). |  |
| Block rooted devices | **Rooted devices** Setting available in [Compliance policy &gt; Device health](../../device-security/compliance/ref-android-administrator-settings#device-health). | **Jailbroken/rooted devices** Setting available in [App protection policy &gt; Conditional launch](../../app-management/protection/ref-settings-android#conditional-launch). |  |
| Allow specific manufacturers | **Device manufacturers** Setting available in [Enrollment &gt; Device platform restriction](../create-platform-restrictions#create-a-device-platform-restriction). | **Device manufacturers** Setting available in [App protection policy &gt; Conditional launch](../../app-management/protection/ref-settings-android#conditional-launch). |  |
| VPN | Create a [VPN profile](../../device-configuration/templates/configure-vpn) in a configuration policy. | Set up [Microsoft Tunnel for Mobile App Management](../../device-security/microsoft-tunnel/mam-android). |  |
| Assign and deploy apps | Make apps required for automatic installation or make them available in the Company Portal app.  Settings available in [Apps &gt; Android store app](../../app-management/deployment/add-store-android#add-an-app). | Apps you make available to employees and students automatically appear in the Company Portal for Android app or Managed Google Play app. | Protect line-of-business (LOB) apps with app protection policies by using the Intune app wrapping tool. If you develop LOB apps in-house, your developers can [leverage the Intune App SDK](../../developer/app-sdk/). |
| Wipe corporate data | **Retire** devices to wipe corporate data only, or **Wipe** devices to restore them to factory settings.  Settings available in [remote actions](../../device-management/actions/wipe). | **Wipe corporate data from apps** Setting available in [App selective wipe](../../app-management/protection/wipe-corporate-data). |  |

## Step 2: Restrict Android device administrator

Create a platform enrollment restriction for Android device administrator to prevent further device administrator enrollments from happening. Devices already enrolled as device administrator remain enrolled and unaffected.

For more information about how to create a platform enrollment restriction, see [Create device platform restrictions](../create-platform-restrictions).

## Step 3: Remove devices from device administrator management

Retire enrolled devices in the Microsoft Intune admin center or instruct device users to unenroll them in the Intune Company Portal app.

Removing an enrolled device from Intune can have the following effect:

- The device loses access to work or school apps and websites.
- The device no longer appears in Intune Company Portal.
- Device users can no longer install work or school apps from Company Portal.
- Setting requirements and restrictions (such as device PIN, disabling the camera, and prohibiting screenshots) are no longer enforced.

### Retire device in admin center

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **By platform** &gt; **Android**.
3. Select **Android devices**.
4. Select the name of the device that you want to retire. You can add an **OS** filter to make it easier to see all Android device administrator devices in your tenant.
5. Select **Retire**. Then select **Yes** to confirm that you want to remove the device from device management.

Removal happens the next time the device checks in and receives the remote *retire* action. The device remains visible in the admin center until the device checks in. If you want to remove stale devices immediately, use the *delete* action instead. For more information about how to remove devices from Microsoft Intune, see [Remote Device Action: Delete](../../device-management/actions/delete).

### Let device users unenroll device

Employees and students can unenroll their devices in the Intune Company Portal app. To support them and ensure that they're successful, you can:

- Send them a custom notification about device requirements and next steps. For more information, see [Send notifications](../../device-management/actions/send-custom-notification).
- Use your organization's internal communication channels, such as email, to inform them of device requirements and next steps.

For removal steps that Android device users can do themselves, see [Unenroll Android device](../../user-help/unenrollment/unenroll-android#remove-device-in-company-portal-app).

## Best practices

This section contains best practices for setting up mobile application management.

### Prevent Company Portal enrollment prompts

When Microsoft Intune detects that the user's device is set up for app protection policies without enrollment, it doesn't prompt the user to enroll via Intune Company Portal. To ensure that other users don't enroll their devices, we recommend configuring the Company Portal app so that there's no enrollment prompt. For more information, see [Device enrollment setting options](../../app-management/configuration/configure-company-portal#device-enrollment-setting-options).

To block enrollment of personal devices, create a device enrollment restriction. For more information, see [Best practices for Android platform restrictions](../create-platform-restrictions#best-practice---android-platform-restrictions).

### Unenrolling devices with Microsoft Entra Conditional Access policies

If you have Microsoft Entra Conditional Access policies that require devices to be compliant for corporate access, the devices you remove from Android device administrator management will lose their access. To ensure continued access, review your existing Conditional Access policies. For more information, see [Require device to be marked as compliant](/en-us/entra/identity/conditional-access/concept-conditional-access-grant#require-device-to-be-marked-as-compliant).

You can also:

- Make app protection a requirement for access.
- Limit user access to approved client apps with Intune app protection policies.

For more information, see [Require approved app or app protection policy](/en-us/entra/identity/conditional-access/howto-policy-approved-app-or-app-protection).

## Troubleshooting

This section describes how to fix issues encountered when switching from Android device administrator to mobile application management.

### Device user required to install Company Portal app

**Symptom**: You unenroll a device from device administrator, and when you try to access a protected app you see the message:

> 
> Company Portal required: To use your work or school account with this app, you must install the Intune Company Portal app. Click **Go to store** to continue.

**Cause**: The Intune Company Portal app isn't on the device you're using. App protection is built in to the Intune Company Portal, app so the app is required on devices utilizing app protection without enrollment.

**Solution**: Install the Intune Company Portal app on the device.

### User account removed from protected apps after user unenrolls device

**Symptom**: You're prompted to sign in to a work or school app again, even though you already signed in.

**Cause**: After a device unenrolls from Android device administrator management, Intune performs a mobile application management wipe on protected apps. As a result, the user account is removed from these apps and you're signed out.

**Solution**: Sign in again to the protected app with your work or school account.