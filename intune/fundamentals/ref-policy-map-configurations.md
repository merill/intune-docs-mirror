---
layout: Conceptual
title: Configurations policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/ref-policy-map-configurations
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
description: A detailed list of the policy map between Basic Mobility and Security configurations and Intune.
ms.date: 2025-12-03T00:00:00.0000000Z
ms.topic: article
ms.reviewer: dagerrit
locale: en-us
document_id: f9c72a53-45d3-52ef-1d4e-e6d5f3f36344
document_version_independent_id: f9c72a53-45d3-52ef-1d4e-e6d5f3f36344
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/ref-policy-map-configurations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/ref-policy-map-configurations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/ref-policy-map-configurations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 17a37a4b-ef65-ca4a-4207-efa1753bf968
---

# Configurations policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn

You can move from Basic Mobility and Security to Microsoft Intune.

Use this article to map the settings in Microsoft Purview compliance portal configuration policies to the equivalent settings in Intune.

Intune offers more policy flexibility. So, each Office policy translates into multiple Intune and Microsoft Entra policies to achieve the same result.

To see these settings in the Microsoft Purview compliance portal, sign in to the [Purview compliance portal](https://protection.office.com/devicev2). Then, select **Device security policies** &gt; policy name &gt; **Edit policy** &gt; **Configurations**.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- To configure the settings in an Intune policy, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). [Role-based access control (RBAC) with Microsoft Intune](role-based-access-control/overview) lists and describes the built-in roles that can create policies.

## Require encrypted backup

This setting was never supported for Windows or Android in Basic Mobility and Security.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Cloud and Storage** &gt; **Force encrypted backup**

## Block cloud backup

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervices iOS devices.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Cloud and Storage** &gt; various **Block iCloud** settings

## Block document synchronization

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervices iOS devices.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Cloud and Storage** &gt; **Block iCloud document and data sync**

## Block photo synchronization

This setting was never supported for Windows or Android in Basic Mobility and Security.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Cloud and Storage** &gt; **Block My Photo Stream**

## Block screen capture

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Three Intune configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Screen capture (mobile only)**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Block screenshots and screen recording**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Screen capture (Samsung KNOX only)**

## Block video conferences on device

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervised iOS devices.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Built-in Apps** &gt; **Block FaceTime**

## Block sending diagnostic data from device

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

For Windows devices, the most restrictive value prevents sending security-related data.

Three Intune configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Reporting and Telemetry** &gt; **Share usage data**

    | Block sending diagnostic data from device value | Share usage data value |
    | --- | --- |
    | Selected | Security |
    | Not selected | Not configured |
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Block sending diagnostic and usage data to Apple**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Diagnostic data (Samsung Knox only)**

## Block access to application store

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

For iOS, this setting is only supported on supervised iOS devices.

Three Intune configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **App store** &gt; **App store (mobile only)**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **App store, Doc Viewing, Gaming** &gt; **Block App store**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; choose a profile with type **Device administrator** &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Google Play Store** &gt; **Google Play store (Samsung Knox only)**

## Require password when accessing application store

This setting was never supported for Windows or Android in Basic Mobility and Security.

Apple doesn't block accessing the app store without a password, but blocks purchases without a password.

One Intune configuration profile:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **App store, Doc Viewing, Gaming** &gt; **Require iTunes Store password for all purchases**

## Block connection with removable storage

This setting was never supported for iOS/iPadOS in Basic Mobility and Security.

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Two Intune configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; **General** &gt; **Removable storage**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; choose a profile with type **Device administrator** &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Cloud and Storage** &gt; **Removable storage (Samsung Knox only)**

## Block Bluetooth connection

This setting was never supported for iOS/iPadOS in Basic Mobility and Security.

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Two Intune configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; profile name &gt; **Properties** &gt; **Configuration settings Edit** &gt; &gt; **Cellular and connectivity** &gt; **Bluetooth**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; choose a profile with type **Device administrator** &gt; **Properties** &gt; **Configuration settings Edit** &gt; **Cellular and connectivity** &gt; **Bluetooth (Samsung Knox only)**

## Related article

- [Move from Basic Mobility and Security to Intune](migrate-from-other-mdm)