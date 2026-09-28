---
layout: Conceptual
title: Get started with Windows frontline worker devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/frontline-worker/windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to manage frontline worker devices using Windows devices in Microsoft Intune. Select the best enrollment option, configure the home screen, and more.
ms.date: 2025-05-29T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: cbernier
locale: en-us
document_id: 111d6ec7-d8f0-fb69-0158-64be949c5dea
document_version_independent_id: 111d6ec7-d8f0-fb69-0158-64be949c5dea
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/frontline-worker/windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/frontline-worker/windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/frontline-worker/windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 49b30744-86e3-4f87-f2ff-7390af63301a
---

# Get started with Windows frontline worker devices - Microsoft Intune | Microsoft Learn

Windows has different devices and cloud services that can be used for frontline workers (FLW). These devices are used globally and in many industries & scenarios, including digital signage, check-in tasks, presentations, kiosks, and more.

You can use physical Windows devices or use Windows 365 Cloud PCs.

Using Intune, you can manage Windows devices used by frontline workers in your organization. This article:

- Helps you determine the best enrollment option and the best device management experience for you and your end users.
- Includes decisions admins need to make, including determining how the device is used, and configuring the device experience.

This article applies to:

- Windows devices owned by the organization and enrolled in Intune

For an overview on FLW devices in Intune, go to [FLW device management in Intune](./).

Use this article to get started with Windows FLW devices in Intune. Specifically:

- Windows 365 Cloud PCs
- Step 1 - Select your enrollment option
- Step 2 - Shared device or user associated device
- Step 3 - Device experience and kiosk

## Step 1 - Select your enrollment option

![](../../media/icons/16/check.svg)**Determine the enrollment option** that's best for your organization.

Determining the enrollment option is the first step. Enrollment determines how the devices are added to Intune for you to manage. The option you choose depends on your business needs and the devices you have.

For FLW devices using Windows, you can use **Windows Autopilot** enrollment or use a **provisioning package**. This section focuses on these enrollment options.

# [Windows Autopilot](#tab/autopilot)
**Windows Autopilot** is the recommended option for FLW devices. You can ship the devices directly to the location without ever touching the devices. With self-deploying mode, users turn on the device, and the enrollment automatically starts.

![](../../media/icons/16/check.svg) If you have Microsoft Entra Premium and you're getting new devices from an OEM, then use Windows Autopilot. You can use the Windows OEM version preinstalled on the devices to automatically enroll the devices. End users only need to turn on the device; no other end user interaction is required.

You can use Windows Autopilot on existing devices. When the existing devices are reset, the Windows Autopilot enrollment can automatically start.

![](../../media/icons/16/error.svg) Windows Autopilot requires Microsoft Entra Premium. If you don't have Entra Premium, then use a provisioning package. There are other Windows enrollment options available, but they're not commonly used for FLW devices.

For information on Windows Autopilot, go to [Windows Autopilot overview](/en-us/autopilot/overview) and [Windows Autopilot self-deploying mode](/en-us/autopilot/self-deploying).

# [Provisioning package](#tab/provpackage)
This option uses the Windows Configuration Designer (WCD) app to create a provisioning package (`.ppkg`). When you create the package, you configure the enrollment settings you want. Then, you make the package available to users on a USB drive or network location (including a SharePoint site).

![](../../media/icons/16/check.svg) If you don't have Microsoft Entra Premium, then use a provisioning package. You can use the provisioning package to bulk enroll many devices. You can also use the provisioning package to enroll new and existing devices.

![](../../media/icons/16/error.svg) If you have Microsoft Entra Premium, then use Windows Autopilot. Windows Autopilot requires Entra Premium.

For information on using a provisioning package with Intune, go to [Bulk enrollment for Windows devices](../../device-enrollment/windows/create-bulk-package).

---

Note

There are other Windows enrollment options available. This article focuses on the enrollment options commonly used for FLW devices. For information on all the Windows enrollment options, go to [Enrollment guide: Enroll Windows client devices in Microsoft Intune](../../device-enrollment/windows/guide).

## Step 2 - Shared device or user associated device

![](../../media/icons/16/check.svg) Determine if the devices are **shared with many users** or **assigned to a single user**.

In this step, this decision depends on your business needs and the end user requirements. It also impacts how these devices are managed with Intune.

These features are configured using Intune device configuration profiles. When the profile has the settings you want, you assign the profile to the devices. The profile can be deployed during Intune enrollment.

# [Shared device](#tab/shared)
**Shared PC** is a feature in Intune, and allows devices to be shared with many users, one user at a time. A user gets the device, completes their tasks, and gives the device to another user. End users sign in to these shared devices with their **Microsoft Entra organization account** or a **guest account**. With this feature, you can delete account information and allow (or prevent) users from saving & viewing files locally.

For example, shared Windows devices can be public computers in libraries, computer labs in schools & universities, shared workstations in offices, and shared laptops in classrooms.

For information on this feature, and to get started, go to:

- [Shared PC or multi-user Windows devices in Intune](../../device-configuration/templates/ref-shared-device-settings-windows)
- [Shared PC or multi-user Windows devices in Intune - Settings list](../../device-configuration/templates/configure-shared-device)

# [User associated device](#tab/single)
These devices have one user. This user associates the device with themselves, which happens when the user signs in during the Intune enrollment. The device is associated with the user's identity in Microsoft Entra.

These devices are used in FLW scenarios where the device is only used by that user. Some examples include personal computers for support staff, design computers for architects & graphic artists, and work-from-home setups.

---

## Step 3 - Device experience and kiosk

![](../../media/icons/16/check.svg)**Configure the device experience**.

This step is optional and depends on your business scenario. If many users share these devices, then we recommended you configure the device experience using the features described in this section.

On Windows devices, you can configure the home screen and device experience. In this step, consider what frontline workers are doing on the devices and the device experience they need for their jobs. This decision impacts how you configure the device.

Some examples of kiosks include self-service terminals in airports, retail stores, government offices, and other public spaces. These devices allow users to do specific tasks, like check-in for flights, access information, or complete transactions.

These features are configured using device configuration profiles. When the profile has the settings you want, you assign the profile to the devices. The profile can be deployed during Intune enrollment.

The following scenarios are common.

### Scenario 1 - Kiosk with one app or many apps

For this scenario, you configure the device as a kiosk, which allows you to customize the device experience.

For example, you can use the device in a lobby so customers can see your product catalog. Or, use the device to show visual content as a digital sign. For information, go to [Configure kiosks and digital signs on Windows desktop editions](/en-us/windows/configuration/kiosk-methods) (opens another Microsoft web site).

You can pin one app or many apps, select a wallpaper, set icon positions, and more. This scenario is often used for dedicated devices, such as shared devices. You can create a Shared PC profile and configure it be a kiosk using the kiosk settings in Intune.

**What you need to know**:

- Only features added to the kiosk are available to end users. So, you can restrict end users from accessing settings and other device features.
- When you pin one app or pin many apps to the kiosk, only those apps open. They're the only apps users can access. Users are locked to those apps, can't close the apps, or do anything else on the devices. This scenario is used on devices dedicated to a specific use, like airport terminals.

To get started, use the following links:

1. [Add apps to Microsoft Intune](../../app-management/deployment/). When the apps are added, you create app policies that deploy the apps to the devices.
2. Create a device configuration [kiosk profile](../../device-configuration/templates/configure-kiosk) and configure the [Windows kiosk profile - settings list](../../device-configuration/templates/configure-kiosk).

    The following example shows the kiosk profile settings for a single app. Make sure you add the app to Intune before you configure the kiosk profile.

    [![The kiosk device configuration profile settings for a single app on Windows devices in Microsoft Intune.](media/windows/kiosk-single-app.png)](media/windows/kiosk-single-app.png#lightbox)

    The following example shows the kiosk profile settings for multiple apps. Make sure you add the apps to Intune before you configure the kiosk profile.

    [![The kiosk device configuration profile settings for multiple apps on Windows devices in Microsoft Intune.](media/windows/kiosk-multi-app.png)](media/windows/kiosk-multi-app.png#lightbox)

### Scenario 2 - Device wide access with many apps

This scenario is a good scenario for Windows 365 Cloud PCs. Users have access to the apps and settings on the device. You can restrict users from different features, such as simple passwords, features in the Settings app, and more.

This scenario also applies to physical devices. It expands the boundary of traditional frontline worker scenarios by also including knowledge workers.

To configure devices for this scenario, you deploy the apps to the devices. Then, use device configuration policies to allow or block device features.

To get started, use the following links:

1. [Add apps to Microsoft Intune](../../app-management/deployment/). When the apps are added, you create app policies that deploy the apps to the devices.
2. Create a device configuration restrictions profile that [allows or restricts features using Intune](../../device-configuration/templates/ref-device-restrictions-windows). There are hundreds of settings available for you to configure, including more in the [Settings Catalog](../../device-configuration/settings-catalog/).

    ![All the device restrictions settings for Windows devices in Microsoft Intune.](media/windows/device-restrictions.png)

## Windows 365 Cloud PCs

**Windows 365 Cloud PCs** are virtual machines that are hosted in the Windows 365 service. They're accessible from anywhere and from any device. They include a Windows desktop experience and are associated with a user. Basically, end users have their own PC in the cloud.

![](../../media/icons/16/check.svg) Windows 365 Cloud PCs are ideal for frontline workers that need a Windows desktop experience, but don't need a physical device. For example, a call center worker that needs access to a Windows desktop app.

These devices enroll in Intune, and are managed like any other device, including apps, configuration settings, and updates.

For information on Windows 365 Cloud PCs, and to learn more, go to:

- [Windows 365 Cloud PCs overview - Enterprise](/en-us/windows-365/enterprise/overview)
- [Windows 365 Cloud PCs overview - Small & medium business](/en-us/windows-365/business/get-started-windows-365-business)