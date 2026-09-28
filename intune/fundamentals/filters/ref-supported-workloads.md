---
layout: Conceptual
title: Platforms and policy types supported by assignment filters - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/filters/ref-supported-workloads
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn which apps, compliance policies, and device configuration profiles and their platforms support assignment filters in Microsoft Intune.
ms.date: 2026-09-17T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1028
locale: en-us
document_id: 9e6a44ad-fc7e-6024-e0d4-e25a5fbbbad5
document_version_independent_id: 9e6a44ad-fc7e-6024-e0d4-e25a5fbbbad5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/filters/ref-supported-workloads.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/filters/ref-supported-workloads
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/filters/ref-supported-workloads.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: 35aa363a-1192-d275-c967-40e43251bf05
---

# Platforms and policy types supported by assignment filters - Microsoft Intune | Microsoft Learn

[Assignment filters in Intune](overview) help you target policies to specific devices and apps based on criteria, like OS version or device properties. You can use filters when assigning apps, compliance policies, device configuration profiles, and app configuration policies to **managed devices** (devices enrolled in Intune) and **managed apps** (apps managed by Intune).

This article lists the app types, compliance policies, device configuration profiles, and app configuration policies that support assignment filters. It also lists the workloads that aren't supported.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- ![](../../media/icons/16/check.svg) : Supports assignment filters.
- ![](../../media/icons/16/error.svg) : Doesn't support assignment filters.
- N/A: Doesn't apply to the platform.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Supported app types for managed devices

You can use assignment filters for some common app policies on the following platforms. For a list of what's not supported on managed devices, go to not supported (in this article).

# [Windows](#tab/windows-apps)
### Windows

| App type | Supported |
| --- | --- |
| Store app | ![](../../media/icons/16/check.svg) |
| Microsoft 365 apps | ![](../../media/icons/16/check.svg) |
| Microsoft Edge version 77 and newer | ![](../../media/icons/16/check.svg) |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](../../media/icons/16/error.svg) |
| Windows web link | ![](../../media/icons/16/check.svg) |
| Line-of-business apps | ![](../../media/icons/16/check.svg) |
| Windows app (Win32) | ![](../../media/icons/16/check.svg) |
| Microsoft Store for Business | ![](../../media/icons/16/check.svg) |

# [Android](#tab/android-apps)
### Android Enterprise

| App type | Supported |
| --- | --- |
| Store app | N/A |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | N/A |
| Line-of-business apps | N/A |
| Android Enterprise system app | ![](../../media/icons/16/check.svg) |
| Managed Google Play store app | ![](../../media/icons/16/check.svg) |
| Managed Google Play web link | ![](../../media/icons/16/check.svg) |
| Managed Android line-of-business app | ![](../../media/icons/16/check.svg) |

Note

Assignment filters aren't supported on Android Enterprise personally-owned devices with work profile (BYOD) when used in "Available" app assignments. If users are targeted with an "Available" app intent, then the app continues to show as available to install from the Google managed play store. Any include or exclude filtering is ignored.

### Android device administrator

| App type | Supported |
| --- | --- |
| Store app | ![](../../media/icons/16/check.svg) |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](../../media/icons/16/error.svg) |
| Line-of-business apps | ![](../../media/icons/16/check.svg) |

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

# [Apple](#tab/apple-apps)
### iOS/iPadOS

| App type | Supported |
| --- | --- |
| Store app | ![](../../media/icons/16/check.svg) |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](../../media/icons/16/error.svg) |
| iOS/iPadOS web clip | ![](../../media/icons/16/check.svg) |
| Line-of-business apps | ![](../../media/icons/16/check.svg) |
| iOS/iPadOS volume purchase program (VPP) app | ![](../../media/icons/16/check.svg) |

### macOS

| App type | Supported |
| --- | --- |
| Store app | N/A |
| Microsoft 365 apps | ![](../../media/icons/16/check.svg) |
| Microsoft Edge version 77 and newer | ![](../../media/icons/16/check.svg) |
| Microsoft Defender for Endpoint | ![](../../media/icons/16/check.svg) |
| Web link | ![](../../media/icons/16/error.svg) |
| Line-of-business apps | ![](../../media/icons/16/check.svg) |

---

## [App configuration policies](../../app-management/configuration/overview)

- For **managed apps**, you can use assignment filters for app configuration policies on the following platforms:

    - Android
    - iOS/iPadOS
    - Windows
- For **managed devices**, you can use assignment filters for app configuration policies on the following platforms:

    - Android Enterprise
    - iOS/iPadOS

## [App protection policies](../../app-management/protection/overview)

- For **managed apps**, you can use assignment filters for app protection policies on the following platforms:

    - Android
    - iOS/iPadOS
    - Windows
- For **managed devices**, assignment filters aren't supported for app protection policies. For other features not supported on managed devices, go to not supported (in this article).

## Compliance policies

- For **managed apps**, assignment filters aren't supported for compliance policies.
- For **managed devices**, you can use assignment filters for all compliance policies on the following platforms:

    - Android device administrator
    - Android Enterprise
    - Android (AOSP)
    - iOS/iPadOS
    - macOS
    - Windows

## Device configuration profiles and Endpoint security

- For **managed apps**, assignment filters aren't supported for device configuration profiles and endpoint security policies.
- On **managed devices**, you can use filters for some common device configuration policies on the platforms listed in the following tables. For a list of what's not supported, go to not supported (in this article).

Note

Some profile types are only available for specific platforms. For example, the **Device features** profile type includes settings that are only available for iOS/iPadOS and macOS devices.

For a list of all device configuration profiles, and the platforms they apply to, go to [Apply features and settings on your devices](../../device-configuration/overview).

# [Windows](#tab/windows-device-configuration)
### Windows

| Profile type | Supported |
| --- | --- |
| Update rings for Windows | ![](../../media/icons/16/check.svg) |
|  |  |
| **Device configuration profile** |  |
| Custom | ![](../../media/icons/16/check.svg) |
| Derived credential | N/A |
| Delivery optimization | ![](../../media/icons/16/check.svg) |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| Device Restrictions (Windows 10 Team) | ![](../../media/icons/16/check.svg) |
| Device Features | N/A |
| Device Firmware Configuration Interface (DFCI) on Windows on supported UEFI | ![](../../media/icons/16/check.svg) |
| Domain Join | ![](../../media/icons/16/check.svg) |
| Edition upgrade and S mode switch | ![](../../media/icons/16/check.svg) |
| Email | ![](../../media/icons/16/check.svg) |
| Endpoint analytics Remediations scripts | ![](../../media/icons/16/check.svg) |
| Endpoint Protection | ![](../../media/icons/16/check.svg) |
| Enrollment device platform restrictions | ![](../../media/icons/16/check.svg) Support for a subset of filter properties including device `osVersion`, `operatingSystemSKU`, and `enrollmentProfileName` |
| Kiosk | ![](../../media/icons/16/check.svg) |
| Network boundary | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| PKCS imported certificate | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Secure assessment (Education) | ![](../../media/icons/16/check.svg) |
| Settings catalog | ![](../../media/icons/16/check.svg) |
| Shared multi-user device | ![](../../media/icons/16/check.svg) |
| Trusted certificate | ![](../../media/icons/16/check.svg) |
| VPN | ![](../../media/icons/16/check.svg) |
| Wi-Fi | ![](../../media/icons/16/check.svg) |
| Wired network | ![](../../media/icons/16/error.svg) |
| Windows health monitoring | ![](../../media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | ![](../../media/icons/16/check.svg)**Account protection**, **Local user group membership**, and **Local admin password solution (Windows LAPS)** |
| Antivirus | ![](../../media/icons/16/check.svg) |
| Attack surface reduction | ![](../../media/icons/16/check.svg) Excludes **Web protection (Microsoft Edge Legacy)**, **Application control**, and **App and browser isolation** |
| Disk encryption | ![](../../media/icons/16/check.svg) |
| Endpoint detection and response | ![](../../media/icons/16/check.svg) |
| Endpoint Privilege Management (EPM) | ![](../../media/icons/16/check.svg) |
| Firewall | ![](../../media/icons/16/check.svg) |
| Microsoft Defender for Endpoint (Windows Desktop) | ![](../../media/icons/16/check.svg) |
| Security baselines | ![](../../media/icons/16/error.svg) |

# [Android](#tab/android-device-configuration)
### Android Enterprise

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](../../media/icons/16/check.svg) |
| Derived credential | ![](../../media/icons/16/check.svg) |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| Device Restrictions (Windows 10 Team) | N/A |
| Device Features | N/A |
| Email | ![](../../media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](../../media/icons/16/error.svg) |
| OEMConfig | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| PKCS imported certificate | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Settings catalog | ![](../../media/icons/16/check.svg) |
| Trusted certificate | ![](../../media/icons/16/check.svg) |
| VPN | ![](../../media/icons/16/check.svg) |
| Wi-Fi | ![](../../media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

### Android (AOSP)

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Settings catalog | ![](../../media/icons/16/check.svg) |
| Trusted certificate | ![](../../media/icons/16/check.svg) |

### Android device administrator

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](../../media/icons/16/check.svg) |
| Derived credential | N/A |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| Device restrictions (Windows 10 Team) | N/A |
| Device features | N/A |
| Email | N/A |
| Email (Samsung KNOX only) | ![](../../media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](../../media/icons/16/error.svg) |
| MX profile (Zebra only) | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| PKCS imported certificate | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Settings catalog | N/A |
| Trusted certificate | ![](../../media/icons/16/check.svg) |
| VPN | ![](../../media/icons/16/check.svg) |
| Wi-Fi | ![](../../media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

# [Apple](#tab/apple-device-configuration)
### iOS/iPadOS

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](../../media/icons/16/check.svg) |
| Derived credential | ![](../../media/icons/16/check.svg) |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| Device Restrictions (Windows 10 Team) | N/A |
| Device Features | ![](../../media/icons/16/check.svg) |
| Email | ![](../../media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| PKCS imported certificate | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Settings catalog (MDM) | ![](../../media/icons/16/check.svg) |
| Settings catalog (DDM) | ![](../../media/icons/16/check.svg) |
| Trusted certificate | ![](../../media/icons/16/check.svg) |
| VPN | ![](../../media/icons/16/check.svg) |
| Wi-Fi | ![](../../media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

### macOS

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](../../media/icons/16/check.svg) |
| Derived credential | N/A |
| Device restrictions | ![](../../media/icons/16/check.svg) |
| Device restrictions (Windows 10 Team) | N/A |
| Device features | ![](../../media/icons/16/check.svg) |
| Email | N/A |
| Endpoint Protection | ![](../../media/icons/16/check.svg) |
| Enrollment device platform restrictions | ![](../../media/icons/16/check.svg) |
| Extensions | ![](../../media/icons/16/check.svg) |
| PKCS certificate | ![](../../media/icons/16/check.svg) |
| PKCS imported certificate | ![](../../media/icons/16/check.svg) |
| Preference file | ![](../../media/icons/16/check.svg) |
| SCEP certificate | ![](../../media/icons/16/check.svg) |
| Settings catalog (MDM) | ![](../../media/icons/16/check.svg) |
| Settings catalog (DDM) | ![](../../media/icons/16/check.svg) |
| Trusted certificate | ![](../../media/icons/16/check.svg) |
| VPN | ![](../../media/icons/16/check.svg) |
| Wi-Fi | ![](../../media/icons/16/check.svg) |
| Wired network | ![](../../media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | ![](../../media/icons/16/check.svg) |
| Attack surface reduction | N/A |
| Disk encryption | ![](../../media/icons/16/check.svg) |
| Endpoint detection and response | N/A |
| Firewall | ![](../../media/icons/16/check.svg) |
| Security baselines | N/A |

---

## Not supported on managed devices

The following features on managed devices don't support using assignment filters:

- Custom compliance policies for Windows (preview)
- App protection policies for Android and iOS/iPadOS

    You can use assignment filters on app protection policies for managed apps. For more information on managed apps, go to [Use filters when assigning your apps, policies, and profiles in Intune](overview).
- End user experiences customization policies
- Enrollment notifications
- Feature updates for Windows
- iOS/iPadOS app provisioning profiles
- Linux platform workloads
- Partner device management
- Policies for Office apps
- Policy sets
- PowerShell scripts for Windows
- S mode supplemental policies for Windows
- Shell scripts for macOS
- Terms and conditions
- Update policies MDM template for iOS/iPadOS (deprecated)
- Devices that are targeted with Endpoint Security configuration using Microsoft Defender for Endpoint integration, such as servers. These devices aren't enrolled in Intune.