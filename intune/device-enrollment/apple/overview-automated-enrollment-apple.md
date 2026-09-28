---
layout: Conceptual
title: Overview of Apple Automated Device Enrollment for iOS/iPadOS in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/overview-automated-enrollment-apple
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: annovich
ms.subservice: enrollment
description: Learn about automated device enrollment (ADE) for Apple mobile devices in Microsoft Intune, including supported scenarios, key features, and how to get started.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: concept-article
ai-usage: ai-assisted
locale: en-us
document_id: 3c9d462c-293a-75e9-3c24-9f0ff68d6e54
document_version_independent_id: 3c9d462c-293a-75e9-3c24-9f0ff68d6e54
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/overview-automated-enrollment-apple.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/overview-automated-enrollment-apple
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/overview-automated-enrollment-apple.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 20c10b5c-92be-80be-8ce7-f296f251f01b
---

# Overview of Apple Automated Device Enrollment for iOS/iPadOS in Intune - Microsoft Intune | Microsoft Learn

Automated device enrollment (ADE) is an Apple enrollment method for corporate-owned devices purchased through Apple Business or Apple School Manager. With ADE, you configure and deploy enrollment policies to devices over the air — without touching the devices. When someone turns on a device for the first time, Apple Setup Assistant guides them through setup and enrollment automatically.

Note

The steps in ADE articles are the same whether you're using Apple Business or Apple School Manager. For brevity, those articles refer to *Apple Business* only, except where clarification is necessary.

## Supported platforms

Microsoft Intune supports automated device enrollment for Apple mobile devices, which include iOS/iPadOS, tvOS, and visionOS. As an administrator, you can create, edit, delete, and assign a platform-specific automated device enrollment policy to devices.

| Platform | Setup article | What it's for |
| --- | --- | --- |
| iOS/iPadOS | [Create an enrollment policy for iOS/iPadOS](setup-automated-ios) | User affinity, no user affinity |
| tvOS | [Create an enrollment policy for tvOS](setup-automated-tv-os) | No user affinity |
| visionOS | [Create an enrollment policy for visionOS](setup-automated-vision-os) | No user affinity |

tvOS and visionOS support automated device enrollment without user affinity only. These platforms enroll using a userless provisioning model and support device-targeted management policies. Device setup is completed through Apple Setup Assistant and device-targeted policies are applied after enrollment.

For macOS information, see [Overview of Apple Automated Device Enrollment for macOS](overview-automated-enrollment-macos).

## Supported scenarios

| Scenario | Supported |
| --- | --- |
| Supervised mode | ✅ ADE devices are supervised by default, giving you more management control. |
| Corporate-owned devices | ✅ Designed for devices purchased through Apple Business or Apple School Manager. |
| Zero-touch deployment | ✅ Devices can ship directly to users. Enrollment starts when they turn on the device. |
| Bulk enrollment | ✅ Enroll a few devices or thousands using a single enrollment policy. |
| Devices with a single assigned user | ✅ Supported on iOS/iPadOS, not tvOS or visionOS. |
| Userless devices (kiosk, shared-use) | ✅ Supported on all Apple mobile platforms. |
| Microsoft Entra shared device mode | ✅ Supported on iOS/iPadOS for frontline worker scenarios. |
| Apple Shared iPad | ✅ Supported on iPadOS. |
| BYOD or personal devices | ❌ Not supported. Use [MAM](../../app-management/protection/mam-without-enrollment) or [user and device enrollment](setup-user-company-portal) instead. |
| Device enrollment manager (DEM) accounts | ❌ Not supported. |
| Devices managed by another MDM provider | ❌ Users must unenroll from their current MDM provider before enrolling in Intune. For help migrating devices, see [Apple making device migration to Microsoft Intune easy with upcoming OS 26 release](https://techcommunity.microsoft.com/blog/IntuneCustomerSuccess/apple-making-device-migration-to-microsoft-intune-easy-with-upcoming-os-26-relea/4439895) on the Microsoft Community Hub. |

## How ADE works

Setting up ADE in Intune involves three main tasks:

1. **Get an enrollment program token**: Create a trust relationship between Intune and Apple Business. This is typically a one-time setup task per token. For more information, see [Set up enrollment token](setup-apple-token).
2. **Create and assign an enrollment policy**: Configure the enrollment experience for your devices, including user affinity, authentication method, and Setup Assistant screens. Then assign the policy to device groups.
3. **Sync and distribute devices**: Sync device records from Apple Business to Intune, then distribute devices to users. Enrollment starts automatically through Apple Setup Assistant when a device is turned on. For more information, see [Managed Apple mobile devices and tokens](manage-devices-tokens-apple).

## What is supervised mode?

Supervised mode provides more management control over corporate-owned devices, so you can do things like block screen captures and restrict AirDrop.

Corporate-owned devices running iOS/iPadOS 11 and later and enrolled through automated device enrollment should always be in supervised mode, which you can turn on in the enrollment policy. For more information about supervised mode, see [Enable supervised mode](enable-supervised-mode). Microsoft Intune ignores the *is\_supervised* flag for devices running iOS/iPadOS 13.0 and later because these devices are automatically put in supervised mode at the time of enrollment.

## Certificates

This enrollment type supports the Automated Certificate Management Environment (ACME) protocol. When new devices enroll, the management profile from Intune receives an ACME certificate. ACME provides better protection than the SCEP protocol against unauthorized certificate issuance through robust validation mechanisms and automated processes, which helps reduce errors in certificate management.

ACME is supported on:

- iOS 16.0 or later
- iPadOS 16.1 or later
- tvOS 26.0 or later
- visionOS 26.0 or later

## Enrolling devices in shared device mode

You can set up automated device enrollment for devices in [shared device mode](/en-us/azure/active-directory/develop/msal-ios-shared-devices). *Shared device mode* is a feature of Microsoft Entra ID that enables frontline workers to share a single device throughout the day, signing in and out as needed. For more information about how to enable enrollment for devices in Microsoft Entra shared device mode, see [Automated device enrollment for shared device mode](setup-automated-shared-device-mode).

## Before you begin

Before setting up ADE in Intune, make sure you have the following in place across all platforms:

- [Microsoft Intune Suite licensing](../../fundamentals/licensing).
    - Microsoft Intune Plan 2 is required for tvOS and visionOS device management.
    - Microsoft Intune Plan 1 is the minimum requirement for iOS/iPadOS device management.
- Access to [Apple Business](https://business.apple.com/) or [Apple School Manager](https://school.apple.com/).
- An [Apple MDM push certificate in Intune](create-mdm-push-certificate).
- An active ADE token (.p7m file) linking your Apple Business or Apple School Manager account to Intune. For steps, see [Set up an ADE token](setup-apple-token).
- New or wiped corporate-owned devices added to Apple Business or Apple School Manager.

Additionally, decide how you want users to authenticate:

- **Setup Assistant with modern authentication** (recommended):

    - Supported on iOS/iPadOS 13.0 and later.
    - Supports multifactor authentication and just-in-time (JIT) registration, eliminating the need for the Company Portal app if configured with a device configuration policy.
- **Intune Company Portal app**:

    - Also supports modern authentication and multifactor authentication.
    - Still requires users to complete Microsoft Entra registration through the app.
- **Setup Assistant (Legacy)**:

    - Supports devices running iOS/iPadOS earlier than 13.0.
    - Not recommended or supported.

Important

We recommend using **Setup Assistant with modern authentication** for all Automated Device Enrollment (ADE) scenarios with user device affinity. Avoid using legacy authentication.

tvOS and visionOS enrollment happens without user affinity. Authentication selection isn't required for these types of devices. For more information about authentication options, see [Authentication methods for automated device enrollment](ref-automated-authentication-methods).