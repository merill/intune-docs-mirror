---
layout: Conceptual
title: Get started with frontline worker (FLW) device management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/frontline-worker/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to manage frontline worker devices using Android, iOS/iPadOS, and Windows devices in Microsoft Intune. Get guidance on device use and Intune features built for FLW, like Remote Help. Also, learn about Microsoft Entra shared device mode (SDM) for FLW.
ms.date: 2026-05-28T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: cbernier
locale: en-us
document_id: f998625f-2ef2-e5fd-aced-6d32abcdd962
document_version_independent_id: f998625f-2ef2-e5fd-aced-6d32abcdd962
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/frontline-worker/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/frontline-worker/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/frontline-worker/index.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e3ec8aa3-7a3e-dc81-51f3-2a41db3552e6
---

# Get started with frontline worker (FLW) device management - Microsoft Intune | Microsoft Learn

A frontline worker (FLW) is a person that works in an essential or critical role to your business. They're typically in direct contact with the public and customers. During a crisis or emergency, like a pandemic or natural disaster, frontline workers are often at the forefront of the response effort, providing critical services and support.

Some popular examples of frontline workers include healthcare, emergency responders, law enforcement, retail & food service, and transportation.

The articles in this section apply to:

- [FLW Android devices owned by the organization and enrolled in Intune](android)
- [FLW iOS and iPadOS devices owned by the organization and enrolled in Intune](ios-ipados)
- [FLW Windows devices owned by the organization and enrolled in Intune](windows)

Note

FLW devices are typically owned by the organization. End user personal devices can be used as FLW devices, but personal devices aren't covered in these articles. This set of articles focus on corporate-owned devices.

Frontline workers rely on devices to enable their productivity, like devices used to scan barcodes or devices utilized for field operations. If these devices fail, worker productivity and business operation can stop. Often, these types of devices can be categorized as mission critical.

The articles in this section provide guidance on managing and configuring frontline worker (FLW) devices using Intune. These devices play a key role in running business operations. And, they're an extension of the operator who uses and relies on the device to be productive for day-to-day business operations.

## Before you begin

When you're planning for FLW devices (including rugged devices) and how you manage them, there are questions you need to answer. These questions help you determine the best device management experience for you, your end user frontline workers, and the needs of your organization.

- Determine how the **devices will be used**.

    For example, you can provide a device wide experience where frontline workers access all the apps and settings on the device. Or, provide a locked screen experience where frontline workers only access specific apps. You can configure the device for a single purpose, like scanning inventory. Or, configure the device for multiple purposes, like using an app to check in customers and using another app to check email.

    Intune has built-in kiosk features that can run one app or run many apps for Android, iPadOS, and Windows. This article provides more details about these device management scenarios.
- Determine if the **devices will be shared** with other users, or if the devices are assigned to specific users.

    For example, if the devices are part of a shared pool, then your device management strategy should focus on shared device management. If the devices are assigned to specific users, then your device management strategy should focus on user associated device management.

    Intune has built-in features that offer shared device management for Android, iPadOS, and Windows devices. This article provides more details about shared devices, and the decisions you need to make.
- Determine the **sign-in/sign-out experience** and how user switching happens, including device hand-off. For example, before cradling the device for charging, you might want users to sign out of apps.

    Intune has built-in features that allow users to sign in as a guest, sign in with their Microsoft Entra organization credentials, or only sign in to apps. There are also features that use single sign-on and single sign-out for your apps. This article provides more details about these features.
- Determine the **starting app experience**. For example, users can sign in to the device and then launch an app, or users can get the device and have an app automatically start.

    Intune has built-in features that allow you to configure the starting app experience. This article provides more details about these features.

When you have this information, the next step is to identify the platforms you use and the devices scenarios.

## Intune features designed for FLW

Intune has built-in features that can be used for frontline worker devices, including:

- **[Cloud-native Windows endpoints](../cloud-native-endpoints/overview)**

    You can turn a Windows client device into a cloud-optimized device. It simplifies the devices, and you can secure them with Microsoft-recommended security features.

    For more information, go to:

    - [Learn more about cloud-native endpoints](../cloud-native-endpoints/overview)
    - [Tutorial: Set up cloud-native Windows endpoints with Microsoft Intune](../cloud-native-endpoints/tutorial-cloud-native-setup)
- **[Remote Help](../../remote-help/)**

    This feature is cloud-based solution that secures help desk connections. With these connections, your support staff can remote connect to FLW devices on:

    - [Android](../../remote-help/)
    - [macOS](../../remote-help/)
    - [Windows](../../remote-help/)
- **[Specialty devices](../../device-management/specialty-devices)**

    These devices include augmented reality (AR) & virtual reality (VR) headsets, large smart-screen devices, and some conference room meeting devices, like Microsoft Teams Rooms devices. They can be managed using Intune policies.

Note

Some features may require additional licenses. For more information, go to [Microsoft Intune advanced capabilities](../../fundamentals/advanced-capabilities) or [Microsoft Intune licensing](../../fundamentals/licensing).

## Microsoft Entra shared device mode for FLW

Microsoft Entra shared device mode (SDM) is designed for frontline workers (FLW). It's an Entra feature that focuses on building apps so many users can use the apps on the same device. Users sign in/sign out of apps, have all their data removed, and have the device ready for the next user.

Some of the benefits of Entra SDM include:

- Entra SDM supports multiple users on devices designed for one user. Some mobile devices running Android and iOS are designed for single users. Most apps optimize their experience for a single user. Apps built with Entra SDM support multiple users on one device.
- Entra SDM does automatic single sign-in and single sign-out. Employees can sign in once and get single sign-on (SSO) to all apps that support Entra SDM, giving them faster access to information.

    This feature is good for organizations with a set of apps in a device pool that employees share. Devices can be immediately ready for use by the next employee with no access to the previous user's data.
- Apps built for Entra SDM use the Microsoft Authentication Library (MSAL) and the Microsoft Authenticator app. When a device is in shared device mode, and with (MSAL) and the Microsoft Authenticator app, Microsoft provides information to your app. This information allows the app to modify its behavior based on the state of the user on the device, which helps protect user data.

Shared device mode (SDM) is a feature of Microsoft Entra. It's not an Intune feature. On Android, Entra SDM and Intune can work together. On iOS/iPadOS, you must use Entra SDM or use Intune. For more information, go to the following articles:

- [Frontline worker for Android devices in Microsoft Intune](android)
- [Frontline worker for iOS/iPadOS devices in Microsoft Intune](ios-ipados)

For more information on Entra SDM, go to [Overview of shared device mode](/en-us/azure/active-directory/develop/msal-shared-devices).

## More Microsoft services for FLW

**Microsoft 365 for frontline workers** is a licensing option designed for frontline worker scenarios. It's ideal for a mobile workforce that primarily interacts with customers and needs to stay connected to the rest of the organization. It interacts with other apps and services, including Microsoft Teams, Outlook, SharePoint, and more.

For more information and to get started, go to:

- [Get started with Microsoft 365 for frontline workers](/en-us/microsoft-365/frontline/flw-overview)
- [Choose your scenarios for Microsoft 365 for frontline workers](/en-us/microsoft-365/frontline/flw-choose-scenarios)

**Windows 365 Frontline** is a version of Windows 365 that provides a single license to provision some Cloud PC virtual machines. It can help organizations save costs. It's ideal for workers who share computing resources and don't require 24/7 devices, including users who:

- Are on a rotation schedule
- Work across time zones and regions
- Are part-time workers
- Are contingent staff

For more information and to get started, go to:

- [Windows 365 Frontline](https://www.microsoft.com/windows-365/frontline)
- [What is Windows 365 Frontline?](/en-us/windows-365/enterprise/introduction-windows-365-frontline)