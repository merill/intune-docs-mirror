---
layout: Conceptual
title: Overview of enrollment restrictions - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/restrictions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- ContentEnagagementFY23
ms.subservice: enrollment
description: Learn about the enrollment restrictions available in Microsoft Intune.
ms.date: 2025-12-04T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: maholdaa
locale: en-us
document_id: 4363dbd8-50da-f10b-0589-b88002b65de7
document_version_independent_id: 4363dbd8-50da-f10b-0589-b88002b65de7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/restrictions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/restrictions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/restrictions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 06f7d67e-bd79-0919-1ce0-31fe20de6b14
---

# Overview of enrollment restrictions - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Device enrollment restrictions let you restrict devices from enrolling in Intune based on certain device attributes. There are two types of device enrollment restrictions you can configure in Microsoft Intune:

- **Device platform restrictions**: Restrict devices based on device platform, version, manufacturer, or ownership type.
- **Device limit restrictions**: Restrict the number of devices a user can enroll in Intune.

Note

Enrollment restrictions are not security features. Compromised devices can misrepresent their character. These restrictions are a best-effort barrier for non-malicious users.

Each restriction type comes with one default policy that you can edit and customize as needed. Intune applies the default policy to all user and userless enrollments until you assign a higher-priority policy.

This article provides an overview of the available enrollment restrictions, and feature limitations. To start creating restrictions, skip to [Next steps](restrictions#next-steps) (in this article).

## Prerequisites

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Enrollment restrictions are available for the following platforms:
> 
> - Android device administrator
> - Android Enterprise personally-owned devices with a work profile (BYOD)
> - iOS
> - macOS
> - Windows
> 

Availability varies by restriction type.

## Available restrictions

You can configure the following restrictions in the admin center:

- Device limit
- Device platform
- OS version
- Device manufacturer
- Device ownership (personally owned devices)

### Device limit

Put a limit on the number of devices a person can enroll. You can set the device limit from 1 to 15.

This configuration is in the admin center under **Enrollment device limit restrictions**.

### Device platform

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Block devices running on a specific device platform. You can apply this restriction to devices running:

- Android device administrator
- Android Enterprise personally-owned devices with a work profile (BYOD)
- iOS/iPadOS
- macOS
- Windows

In groups where both Android platforms are allowed, devices that support work profile will enroll with a work profile. Devices that don't support work profile will enroll on the Android device administrator platform. Neither work profile nor device administrator enrollment will work until you complete all prerequisites for Android enrollment.

This restriction is in the admin center under **Devices** &gt; **Device onboarding** &gt; **Enrollment** &gt; **Device platform restriction**.

Note

Device platform enrollment restrictions use assignment filters. The update between Microsoft Entra and Intune that processes user, group, and filter assignments typically happens within 15 minutes. It's not instant. This amount of time can affect enrollment assignments. You should wait and enroll devices several minutes after adding the enrolling users to a group, not immediately after.

### OS version

This restriction enforces your maximum and minimum OS version requirements. This type of restriction works with the following operating systems:

- Android device administrator\*
- Android Enterprise personally-owned devices with a work profile (BYOD)\*
- iOS/iPadOS\*
- Windows

\* Version restrictions are supported on these operating systems for devices enrolled via Intune Company Portal only.

This restriction is in the admin center under **Devices** &gt; **Device onboarding** &gt; **Enrollment** &gt; **Device platform restriction**.

### Device manufacturer

This restriction blocks devices made by specific manufacturers, and is applicable to Android devices only. It is in the admin center under **Devices** &gt; **Device onboarding** &gt; **Enrollment** &gt; **Device platform restriction**.

### Personally owned devices

This restriction helps prevent device users from accidentally enrolling their personal devices, and applies to devices running:

- Android
- iOS/iPad OS
- macOS
- Windows

This restriction is in the admin center under **Devices** &gt; **Device onboarding** &gt; **Enrollment** &gt; **Device platform restriction**.

#### Blocking personal Android devices

By default, until you manually make changes in the admin center, your Android Enterprise work profile device settings and Android device administrator device settings are the same.

If you block Android Enterprise work profile enrollment on personal devices, only corporate-owned devices can enroll with [personally owned work profiles](../app-management/protection/mam-vs-work-profiles-android#android-enterprise-personally-owned-work-profiles).

#### Blocking personal iOS/iPadOS devices

By default, Intune classifies iOS/iPadOS devices as personally owned. To be classified as corporate-owned, an iOS/iPadOS device must fulfill one of the following conditions:

- [Registered with a serial number or IMEI](add-corporate-identifiers).
- Enrolled by using Automated Device Enrollment (formerly Device Enrollment Program).

#### Blocking personal Macs

By default, Intune classifies macOS devices as personally owned. To be classified as corporate-owned, a Mac must fulfill one of the following conditions:

- [Registered with a serial number](add-corporate-identifiers).
- Enrolled via Apple Automated Device Enrollment (ADE).

#### Blocking personal Windows devices

If you block personally owned Windows devices from enrollment, Intune checks to make sure that each new Windows enrollment request has been authorized for corporate enrollment. Unauthorized enrollments are blocked.

The following enrollment methods are authorized for corporate enrollment:

- The device enrolls through [Windows Autopilot](/en-us/autopilot/enrollment-autopilot).
- The device enrolls through GPO, or [automatic enrollment from Configuration Manager for co-management](/en-us/configmgr/comanage/quickstart-paths#bkmk_path1).
- The device enrolls through a [bulk provisioning package](windows/create-bulk-package).
- The enrolling user is using a [device enrollment manager account](setup-enrollment-manager).

Note

Since a co-managed device enrolls in the Microsoft Intune service based on its Microsoft Entra device token, and not a user token, only the default Intune enrollment restriction will apply to it.

Intune marks devices going through the following types of enrollments as corporate-owned, and blocks them from enrolling (unless registered with Windows Autopilot) because these methods don't offer the Intune administrator per-device control:

- [Automatic MDM enrollment](windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Microsoft Entra join during Windows setup](/en-us/azure/active-directory/device-management-azuread-joined-devices-frx).
- [Automatic MDM enrollment](windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Microsoft Entra join from Windows Settings](/en-us/azure/active-directory/user-help/user-help-join-device-on-network).
- [Automatic MDM enrollment](windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with Microsoft Entra join or hybrid Entra join via [Windows Autopilot for existing devices](/en-us/autopilot/existing-devices).

Intune also blocks personal devices using these enrollment methods:

- [Automatic MDM enrollment](windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Add Work Account from Windows Settings](/en-us/azure/active-directory/user-help/user-help-register-device-on-network).
- [MDM enrollment only](/en-us/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) option from Windows Settings.
- [Enrollment using the Intune Company Portal app](../user-help/enrollment/enroll-windows).
- Enrollment via a Microsoft 365 app, which occurs when users select the **Allow my organization to manage my device** option during app sign-in.

Important

Devices joined by Workplace Join could be blocked from enrolling if they were ever previously Microsoft Entra joined to the tenant. To avoid being blocked, deregister and remove the device's associated object in Microsoft Entra ID before attempting to join the device by Workplace Join.

## Limitations

- Enrollment restrictions are applied to enrollments that are user-driven. For enrollment scenarios that **aren't** user-driven, Intune enforces the default policy. For example, the following enrollment scenarios use the default policy because they **aren't** user-driven:

    - Windows Autopilot self-deploying mode and Windows Autopilot for pre-provisioned deployment
    - Bulk enrollment via Windows Configuration Designer
    - Co-managed enrollments
    - Userless Apple automated device enrollment (without user-device affinity)
    - Azure Virtual Desktop
    - Windows 365
    - Android Enterprise corporate-owned dedicated devices
- Device limit restrictions can't be applied to devices in the following Windows enrollment scenarios, because these scenarios utilize shared device mode:

    - Co-managed enrollments
    - Group Policy (GPO) enrollments
    - Microsoft Entra joined enrollments, including bulk enrollments
    - Windows Autopilot enrollments
    - Device enrollment manager enrollments

    Instead, you can configure a hard limit for these enrollment types in Microsoft Entra ID. For more information, see [Manage device identities by using the Azure portal](/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).