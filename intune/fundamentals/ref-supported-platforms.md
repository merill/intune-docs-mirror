---
layout: Conceptual
title: Operating systems and browsers supported by Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms
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
description: Lists supported device platforms and browsers for Intune device management
ms.date: 2025-10-14T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: priyar
locale: en-us
document_id: b2cf3f67-82ac-9839-ffe9-c1a3bb0634f1
document_version_independent_id: b2cf3f67-82ac-9839-ffe9-c1a3bb0634f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/ref-supported-platforms.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/ref-supported-platforms
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/ref-supported-platforms.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 16b20ac0-d3ca-7ccf-bf09-df5d60b805e0
---

# Operating systems and browsers supported by Microsoft Intune - Microsoft Intune | Microsoft Learn

Before setting up Microsoft Intune, review the supported operating systems and browsers.

For more information on configuration service provider support, visit the [Configuration service provider reference](/en-us/windows/client-management/mdm/configuration-service-provider-reference).

## Intune supported operating systems

Intune supports devices running the following operating systems (OS):

- Android
- iOS/iPadOS
- Linux
- macOS
- Windows
- Chrome OS

Note

App protection policies are not supported on Chrome OS

### Apple

- **Devices with user affinity** - devices enrolled with user affinity using ADE (automated device enrollment) or personally enrolled devices.
- Supported:

    - iOS/iPadOS 18 and later
    - macOS 15 and later
- **Devices without user affinity** - devices enrolled without user affinity using ADE (automated device enrollment) or Apple Configurator.

    - Supported:

        - iOS/iPadOS 18 and later
        - macOS 15 and later
    - Allowed to enroll:

        - iOS/iPadOS 16 and later
        - macOS 13 and later

Note

**Supported** versions include devices running the three most recent operating system versions. These devices can enroll and take advantage of all Intune functionality that's applicable, and all new eligible features work on these devices.

**Allowed** versions include devices running a non-supported version (within three versions of the supported versions). These devices can enroll and take advantage of Intune's eligible features but there's no guarantee that they'll work as expected.

Intune requires iOS/iPadOS 17.x or later for app protection policies and app configuration.

### Android

**Android 10.0 and later for user-based management methods**. These methods are:

- Android Enterprise personally owned with a work profile
- Android Enterprise corporate owned work profile
- Android Enterprise fully managed
- Android Open Source Project (AOSP) user-based
- Android device administrator ([Intune ended support for Android device administrator on devices with GMS in December 2024](https://techcommunity.microsoft.com/blog/intunecustomersuccess/intune-ending-support-for-android-device-administrator-on-devices-with-gms-in-de/3915443))

**Android 8.0 and later for userless management methods**. These methods are:

- Android Enterprise dedicated
- AOSP userless

**Additional**

- Samsung KNOX Standard 3.0 and higher: [requirements](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+)
- Android open source project devices: [See here for the list of supported devices](aosp-supported-devices)

Note

This requirement does not apply to [Microsoft Teams Android devices](https://www.microsoft.com/microsoft-teams/across-devices/devices?rtc=2) as these devices will continue to be supported.

For Intune app protection policies and app configuration delivered through Managed apps app configuration policies, Intune requires Android 10.0 or higher.

### Linux

- Ubuntu Desktop 24.04 and 26.04 LTS with a GNOME graphical desktop environment
- Ubuntu LTS, version 24.04 and 26.04
- RedHat Enterprise Linux 9
- RedHat Enterprise Linux 10

Note

Ubuntu Desktop already has a GNOME graphical desktop environment installed.

### Microsoft

- Windows 11 Home, S, Pro, Pro Education, Education, Enterprise, and IoT Enterprise editions
- Windows 10/11 Cloud PCs on Windows 365

    You can continue to use Microsoft Intune to manage devices running Windows 11 the same as with Windows 10. If another article doesn't explicitly reference Windows 11, assume that feature support for Windows 10 also includes Windows 11.

    Some features might not be available on Windows 11. This article lists some known issues. As always, test your policies before broadly deploying them across your devices.
- Windows 10 LTSC 2019/2021 and Windows 11 LTSC 2024 (Enterprise and IoT Enterprise editions)
- Windows Holographic for Business

    For more information about managing devices running Windows Holographic for Business, see [Windows Holographic for Business support](../solutions/windows-holographic).

Note

Not all Windows editions support all available operating system features being configured through MDM. For more information, see the [Windows configuration service provider reference docs](/en-us/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers). Each CSP highlights which Windows editions are supported.

Customers with Enterprise Management + Security (EMS) can also use [Microsoft Entra ID to register Windows devices](../device-enrollment/windows/enable-automatic-mdm).

For guidelines on using Windows virtual machines with Intune, see [Using Windows virtual machines](../solutions/windows-virtual-machines).

Important

- On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
- Intune doesn't currently support managing UWF enabled devices. For more information, see [Unified Write Filter (UWF) feature](/en-us/windows-hardware/customize/enterprise/unified-write-filter).

### Windows 11 known issues

- Currently, you can use Intune to configure a single-app kiosk on Windows 11 devices. For more information about Windows 11 multi-app kiosk support, go to [Set up a multi-app kiosk on Windows 11 devices](/en-us/windows/configuration/lock-down-windows-11-to-specific-apps).

    For more information on dedicated kiosk devices in Intune, go to [Windows and Windows Holographic for Business device settings to run as a dedicated kiosk using Intune](../device-configuration/templates/configure-kiosk).
- Management capabilities to deliver customized Start and Taskbar experiences are currently limited. For more information, see the following articles:

    - [Supported configuration service provider (CSP) policies for Windows 11 Start menu](/en-us/windows/configuration/supported-csp-start-menu-layout-windows)
    - [Supported configuration service provider (CSP) policies for Windows 11 taskbar](/en-us/windows/configuration/supported-csp-taskbar-windows)
    - [Windows device settings to allow or restrict features using Intune](../device-configuration/templates/ref-device-restrictions-windows)

### Cloning physical and virtual devices

Intune does not support using a cloned image of a computer that is already enrolled. This includes both physical and virtual devices such as Azure Virtual Desktop (AVD). When device enrollment or identity tokens are replicated between devices, Intune device enrollment or synchronization failures will occur.

- For more information, see [Mobile device enrollment - Windows Client Management](/en-us/windows/client-management/mobile-device-enrollment) and [Certificate authentication device enrollment - Windows Client Management](/en-us/windows/client-management/certificate-authentication-device-enrollment).
- For information on disabling token roaming in AVD, see [Using Azure Virtual Desktop multi-session with Microsoft Intune](../solutions/azure-virtual-desktop-multi-session#prerequisites).
- For information on troubleshooting issues related to image cloning, see [Error hr 0x8007064c: The machine is already enrolled](/en-us/troubleshoot/mem/intune/troubleshoot-windows-enrollment-errors#error-hr-0x8007064c-the-machine-is-already-enrolled).

### Supported platforms for Microsoft Defender for Endpoint Integration

For more information, see [Microsoft Defender for Endpoint on devices with Microsoft Intune](../device-security/microsoft-defender/security-settings-management)

### Supported Samsung Knox Standard devices

Microsoft Intune only attempts Samsung Knox activation during enrollment on supported Knox devices. Devices that don't support Samsung Knox enroll as standard Android devices. For a list of devices that support Samsung Knox, see [Devices secured by Knox](https://www.samsungknox.com/knox-supported-devices/knox-workspace) on the Samsung Knox website. It's important to look for your device model number when verifying support, because some device models support Knox while others don't. Always verify Knox compatibility with your device reseller before you buy and deploy Samsung devices.

Note

You may need to enable access to Samsung servers to enroll Samsung Knox devices. For more information about enrollment, see [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](../device-enrollment/android/setup-samsung-knox-mobile).

The Samsung device models in the following table don't support Knox solutions and features. Intune enrolls them as native Android devices.

| Device Name | Device Model Numbers |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355HSM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386FSM-G386W |
| Galaxy Grand | GT-I9082LGT-I9082GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100HSM-J100MSM-J100ML |
| Galaxy J1 Ace | SM-J110FSM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200HSM-J210F |
| Galaxy J3 | SM-J320FSM-J320FNSM-J320HSM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930SSM-N9300SM-N930FSM-N930TSM-N9300SM-N930FSM-N930SSM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730ASM-G730V |
| Galaxy S3 Neo | GT-I9300GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0" | SM-T280SM-T285 |
| Galaxy Tab 3 7"/Tab 3 Lite 7" | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0" | SM-T311 |
| Galaxy Tab 3 10.1" | GT-P5200GT-P5210GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

## Intune supported web browsers

Device management and administrative tasks are done in the Microsoft Intune admin center. Use these portals to access the admin center:

- [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure portal](https://portal.azure.com/)

Microsoft Intune is supported with the following web browsers:

- Microsoft Edge (latest version)
- Safari (latest version, Mac only)
- Chrome (latest version)
- Firefox (latest version)