---
layout: FAQ
title: Windows Autopilot device preparation FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/faq
summary: >
  <p><strong>Applies to:</strong></p>

  <ul>

  <li><a href="/windows/release-health/supported-versions-windows-client#windows-11-supported-versions">Windows 11</a>.</li>

  </ul>

  <p>This article provides OEMs, partners, administrators, and users with answers to some frequently asked questions about deploying Windows with Windows Autopilot device preparation.</p>
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: This article provides OEMs, partners, administrators, and users with answers to some frequently asked questions about deploying Windows with Windows Autopilot device preparation.
ms.date: 2025-04-04T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: faq
locale: en-us
document_id: 4c246b9f-70da-f9e3-839e-310a062b5ecb
document_version_independent_id: 4c246b9f-70da-f9e3-839e-310a062b5ecb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/faq.yml
site_name: Docs
depot_name: MSDN.autopilot
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 3cbda551-1a0e-994f-e53b-127790729ff5
---

# Windows Autopilot device preparation FAQ | Microsoft Learn

**Applies to:**

- [Windows 11](/en-us/windows/release-health/supported-versions-windows-client#windows-11-supported-versions).

This article provides OEMs, partners, administrators, and users with answers to some frequently asked questions about deploying Windows with Windows Autopilot device preparation.

## How is Windows Autopilot device preparation different from Windows Autopilot?

Windows Autopilot device preparation is a re-architecture of Windows Autopilot. While the experience to OEMs, IT admins, and users is similar, the underlying architecture is different. The updated architecture in Windows Autopilot Device preparation gives new capabilities that improves the deployment experience.

## Who does Windows Autopilot device preparation benefit?

Windows Autopilot device preparation benefits government customers who can now use Windows Autopilot device preparation to streamline their deployments at scale. It also benefits new customers onboarding Windows Autopilot device preparation by reducing the complexity of setting up the deployment.

## Is Windows Autopilot device preparation available in all sovereign clouds?

Windows Autopilot device preparation is available for Government Community Cloud (GCC) High, U.S. Department of Defense (DoD), and Intune operated by 21Vianet in China.

## What scenarios does Windows Autopilot device preparation support?

Currently Windows Autopilot device preparation supports the following scenarios:

- User-driven scenario for physical devices.
- Automatic deployment for Windows 365 Frontline for shared devices (in preview).

## What about the other Windows Autopilot scenarios like pre-provisioning and self-deploying mode?

The pre-provisioning mode and self-deploying mode scenarios will be supported in the future, but aren't part of the initial release.

## Why is there a limit on the number of applications and PowerShell scripts in the Windows Autopilot device preparation policy?

We limited the number of applications that can be applied during the out-of-box experience (OOBE) to increase stability and achieve a higher success rate. Looking at our telemetry, almost 90% of all Windows Autopilot deployments are deployed with 10 or fewer apps. This limit is intended to improve the overall user experience so that users can become more productive quickly. We understand that there are outliers and companies that want to target more during setup. However, for the user-driven approach, we want to use the desktop experience for non-essential applications.

## Does Windows Autopilot device preparation support deploying both Win32 and line-of-business (LOB) applications in the same deployment?

Yes. While we always recommend Win32 applications, mixing applications in Windows Autopilot deployments might result in errors. With the Windows Autopilot device preparation, we have streamlined the providers so different application types shouldn't affect each other.

## What is the guidance on user-based targeting vs device-based targeting?

Only device-based configurations are delivered during OOBE. For this reason:

- Assign security policy to devices.
- Ensure all selected applications in the Windows Autopilot device preparation policy are set to install in the **System** context.
- Ensure all selected applications in the Windows Autopilot device preparation policy are targeted to the device security group specified in the Windows Autopilot device preparation policy.
- Ensure all selected PowerShell scripts in the Windows Autopilot device preparation policy are targeted to the device security group specified in the Windows Autopilot device preparation policy.

## How do users know when the required setup is complete?

Many users aren't sure when the provisioning process is complete. To help mitigate confusion and calls to support, we added a completion page in OOBE. The completion page lets the user know that OOBE setup is complete. However, additional installations that were assigned to the device group but not specified in the Windows Autopilot device preparation policy might still be occurring in the background.

## Can Windows Autopilot Device preparation be used by non-Microsoft mobile device management (MDM) providers?

Windows Autopilot device preparation will support non-Microsoft MDMs. In this initial release, configuration is only possible via Intune.

## Is Windows Autopilot device preparation available on Windows 10 devices?

Currently, Windows Autopilot device preparation is only available on:

- Windows 11, version 23H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later.
- Windows 11, version 22H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later.

## Do existing Windows Autopilot profiles need to be migrated to Windows Autopilot device preparation?

There's no need to migrate from existing Windows Autopilot profiles to Windows Autopilot device preparation policies. We expect both solutions to exist in parallel for a while as we work to improve the experience and add more functionality.

## Does this mean that Windows Autopilot isn't being invested in any longer?

Not at all! We're continuing to work on Windows Autopilot in parallel with developing Windows Autopilot device preparation. The first release of Windows Autopilot device preparation doesn't have all the scenarios of Windows Autopilot, specifically pre-provisioning and self-deploying modes, so we'll continue to invest in those areas. Additionally, in the future, we plan to add any high value features from Windows Autopilot device preparation to Windows Autopilot to improve the experience for all customers.

## Does Windows Autopilot device preparation support Microsoft Entra hybrid join?

No. Windows Autopilot device preparation only supports Microsoft Entra join.

## What type of applications does Windows Autopilot device preparation support?

The following types of applications are supported for use with Windows Autopilot device preparation:

- [Line-of-business (LOB)](/en-us/intune/app-management/deployment/add-lob-windows).
- [Win32](/en-us/intune/app-management/deployment/create-win32-package).
- [Microsoft Store](/en-us/intune/app-management/deployment/add-microsoft-store) - only Microsoft Store apps that support WinGet are supported.
- [Microsoft 365](/en-us/intune/app-management/deployment/add-microsoft-365-windows).
- [Enterprise App Catalog](/en-us/intune/app-management/deployment/add-enterprise-catalog-app).

## Do devices need to be pre-staged with Windows Autopilot device preparation?

No. Windows Autopilot device preparation policies are deployed to a user group and not a device group. Once a user in that user group signs into the device during OOBE, the Windows Autopilot device preparation deployment begins. During the deployment, the device is then automatically added to the device group specified in the Windows Autopilot device preparation policy.

## Which Windows Autopilot device preparation policy receives priority if multiple policies are deployed to a user?

If multiple Windows Autopilot device preparation policies are deployed to a user, the policy with the highest priority gets priority. Policy priorities are displayed at the **Home** &gt; **Enroll devices | Windows enrollment** &gt; **Device preparation policies** screen. The policy with the highest priority is higher in the list and has the smallest number under the **Priority** column. To change a policy's priority, move it in the list by dragging the policy within the list.

## What makes Windows Autopilot device preparation deployments more efficient than Windows Autopilot?

The key to making Windows Autopilot device preparation deployments more efficient than Windows Autopilot is [Enrollment Time Grouping](overview#enrollment-time-grouping). With Enrollment Time Grouping, devices are automatically added to an assigned device group specified in the Windows Autopilot device preparation policy. Since the device group is assigned instead of dynamic as used in Windows Autopilot, anything assigned to the device group is processed faster and more efficiently. The assigned group eliminates the need to perform queries that are required with dynamic groups.

## What makes Windows Autopilot device preparation deployments more consistent and reliable than Windows Autopilot?

Windows Autopilot device preparation ensures configurations and apps are delivered in a serialized way, minimizing conflicts. Delivering in a serialized way allows you to deliver Line-of-business and Win32 apps in the same deployment reliably.

## How does a user know that a Windows Autopilot device preparation deployment is running on their device?

During a Windows Autopilot device preparation deployment, a **Setting up for work or school** window with a round progress bar displays on the device:

![Screenshot that shows the Status screen for Windows Autopilot device preparation deployment.](../images/device-preparation/apdp-status.png)

Windows Autopilot device preparation doesn't use the Enrollment Status Page (ESP) like Windows Autopilot. If the ESP displays during the deployment, then the device isn't running a Windows Autopilot device preparation deployment. Instead, the device might be:

- A Windows Autopilot registered device.
- A Windows Autopilot profile is assigned to the device.

Verify that the device isn't registered as a Windows Autopilot device and that a Windows Autopilot profile isn't assigned to the device. Windows Autopilot profiles take precedence over Windows Autopilot device preparation policies.

If a device needs to be removed as a Windows Autopilot device, see [Deregister a device](../registration-overview#deregister-a-device).