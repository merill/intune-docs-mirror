---
layout: Conceptual
title: Understand Intune and Microsoft Entra device limit restrictions - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/limits-intune-entra
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Learn the differences between Intune device limit restrictions and Microsoft Entra device limit restrictions.
ms.date: 2024-10-14T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: maholdaa
locale: en-us
document_id: 87a76638-be81-6aa5-3440-849e58fa253a
document_version_independent_id: 87a76638-be81-6aa5-3440-849e58fa253a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/limits-intune-entra.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/limits-intune-entra
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/limits-intune-entra.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 36ca36ac-f693-4384-e191-1eb8006efbce
---

# Understand Intune and Microsoft Entra device limit restrictions - Microsoft Intune | Microsoft Learn

There are two ways to limit the number of devices an employee or student can use for work or school. You can:

- Configure device limit restrictions in the Microsoft Intune admin center.
- Configure a device limit in the Microsoft Entra admin center.

This article provides an overview of each limitation, and describes the device conditions and provisioning scenarios that support them. It applies to:

- Android
- iOS
- macOS
- Windows

## Intune device limit restrictions

Configure Intune device limit restrictions to limit the number of devices a user can enroll in Microsoft Intune. You can allow a user to enroll up to 15 devices. To create a device limit restriction, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** &gt; **Enrollment**. For more information, see [Create a device limit restriction](create-device-limit-restrictions).

Intune device limit restrictions don't apply to devices enrolled via:

- Android device administrator + device enrollment manager
- Android Enterprise dedicated device
- Co-management with Configuration Manager
- Automatic enrollment + group policy
- Automatic enrollment + device enrollment manager
- Automatic enrollment + bulk device enrollment
- Automatic enrollment initiated by user through desktop (for example, when they [connect a work or school account in the Windows Settings app](https://support.microsoft.com/windows/manage-user-accounts-in-windows-104dc19f-6430-4b49-6a2b-e4dbd1dcdf32))
- Windows Autopilot

Devices enrolled via these methods are enrolled automatically or by an Intune admin, not by an employee or student, and are considered shared devices. Instead, you can apply the Microsoft Entra limit, where supported.

## Microsoft Entra device limit

Configure the *maximum number of devices per user* in Microsoft Entra to limit the number of devices that can join or register with Microsoft Entra. To access this setting:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Go to **Identity** &gt; **Devices** &gt; **Device settings**.

The limit applies to devices that are Microsoft Entra joined or Microsoft Entra registered, with some exceptions. It isn't applicable to Microsoft Entra hybrid joined devices, and devices enrolled via:

- Android Enterprise dedicated device
- Windows automatic enrollment + bulk device enrollment
- Windows automatic enrollment + group policy

For more information about configuring these setting in Microsoft Entra ID, see [Configure device settings](/en-us/azure/active-directory/devices/device-management-azure-portal).

## Applicable scenarios

Use the following table to determine the type of limitations you can apply to devices.

| Platform | Device management solution | User affinity | Does Microsoft Entra limitation apply? | Does Intune limitation apply? |
| --- | --- | --- | --- | --- |
| Android | Android Enterprise personally owned work profile | Yes | Yes | Yes |
| Android | Android Enterprise dedicated device | No | No | No |
| Android | Android Enterprise fully managed | Yes | Yes | Yes |
| Android | Android Enterprise corporate-owned work profile | Yes | Yes | Yes |
| Android | Android device administrator | Yes | Yes | Yes |
| Android | Android device administrator + device enrollment manager | No | Yes | No |
| iOS and macOS | BYOD: Apple User Enrollment | Yes | Yes | Yes |
| iOS and macOS | BYOD: Apple Device Enrollment | Yes | Yes | Yes |
| iOS and macOS | Apple Automated Device Enrollment | Yes | Yes | Yes |
| Windows | BYOD: User enrollment | Yes | Yes | Yes |
| Windows | Automatic enrollment + group policy | No | No | No |
| Windows | Automatic enrollment + device enrollment manager | No | Yes | No |
| Windows | Automatic enrollment + bulk device enrollment | No | No | No |
| Windows | Windows Autopilot | Yes | Yes | No |
| Windows | Co-management with Configuration Manager | No | Yes | No |

## Android and iOS devices

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

### iOS or Android devices example 1

- The Microsoft Entra **Maximum number of devices per user** setting is set to 3.
- The Intune **Device limit** setting is set to 5.

**Outcome:** You can enroll up to 3 devices, because the Microsoft Entra ID limits users to a maximum of 3 devices. If you try to enroll more than three devices in Intune, enrollment fails because the fourth device is blocked from registering in Microsoft Entra ID.

### iOS or Android devices example 2

- The Microsoft Entra **Maximum number of devices per user** setting is set to 20.
- The Intune **Device limit** setting is set to 2.

**Outcome:** You can successfully register and enroll two devices. Intune enrollment will be blocked for any additional devices. The Microsoft Entra limit only applies to Apple automated device enrollment when devices are configured with user affinity.

## Windows devices

### Windows example 1

- The Microsoft Entra **Maximum number of devices per user** setting is set to 5.
- The Intune **Device limit** setting is set to 3.
- The devices are Microsoft Entra hybrid joined and enrolled automatically (GPO configured).

**Outcome:** Because the enrollment is provisioned by GPO, the Microsoft Entra device limit doesn't apply. The Intune device limit restriction also doesn't apply.

### Windows example 2

- The Microsoft Entra **Maximum number of devices per user** setting is set to 5.
- The Intune **Device limit** setting is set to 2.
- The devices are local domain joined, and enrolled in the Settings app.

**Outcome:** You can only enroll two devices before they're blocked. You can register up to five devices.