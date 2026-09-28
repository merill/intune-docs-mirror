---
layout: Conceptual
title: Data Intune sends to Apple - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-intune-to-apple
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- privacy
- sub-data-privacy
description: List of data that Intune sends to Apple.
ms.date: 2023-12-07T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: 
locale: en-us
document_id: e4dc439b-93b2-3b25-c6d7-ae541d670d96
document_version_independent_id: e4dc439b-93b2-3b25-c6d7-ae541d670d96
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/data-sharing/ref-intune-to-apple.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/data-sharing/ref-intune-to-apple
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/data-sharing/ref-intune-to-apple.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 053d1927-e72d-73ee-d80e-a9f8c31c0504
---

# Data Intune sends to Apple - Microsoft Intune | Microsoft Learn

When any of the following Apple services are enabled on a device, Microsoft Intune establishes a connection with Apple and shares user and device information with Apple:

- [Apple Device Enrollment Program (DEP)](../../device-enrollment/apple/setup-automated-ios)
- [Apple MDM Push certificate (APNS)](../../device-enrollment/apple/create-mdm-push-certificate)
- [Apple School Manager (ASM)](/en-us/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program (VPP)](../../app-management/deployment/manage-vpp-apple)

Before Microsoft Intune can establish a connection, you must create an Apple account for each of the Apple services.

The following table lists the data that Microsoft Intune sends from a device to the enabled Apple services.

| Service | Data sent to Apple | Used for |
| --- | --- | --- |
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | If the server accepts the device, the device provides its push notification device token to the server. The server should use this token to send push messages to the device. This check-in message also contains a PushMagic string. The server must remember this string and include it in any push messages it sends to the device. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Server token | Push notification device token used to authenticate to Apple service. |
| ASM/DEP | server\_name | An identifiable name for the MDM server. |
| ASM/DEP | server\_uuid | A system-generated server identifier. |
| ASM/DEP | admin\_id | Apple ID of the person who generated the current tokens that are in use. |
| ASM/DEP | org\_name | The organization's name. |
| ASM/DEP | org\_email | The organization's email address. |
| ASM/DEP | org\_phone | The organization's phone. |
| ASM/DEP | org\_address | The organization's address. |
| ASM/DEP | org\_id | DEP customer ID. This key is available only in protocol version 3 and later. |
| ASM/DEP | serial\_number | The device's serial number (string). |
| ASM/DEP | model | The model name (string). |
| ASM/DEP | description | A description of the device (string). |
| ASM/DEP | asset\_tag | The device's asset tag (string). |
| ASM/DEP | profile\_status | The status of profile installation. Possible values: **empty**, **assigned**, **pushed**, or **removed**. |
| ASM/DEP | profile\_uuid | The unique ID of the assigned profile. |
| ASM/DEP | device\_assigned\_by | The email of the person who assigned the device. |
| ASM/DEP | os | The device's operating system: iOS/iPadOS, OSX, or tvOS. This key is valid in X-Server-Protocol-Version 2 and later. |
| ASM/DEP | device\_family | The device's Apple product family: iPad, iPhone, iPod, Mac, or AppleTV. This key is valid in X-Server-Protocol-Version 2 and later. |
| ASM/DEP | profile\_name | String. A human-readable name for the profile. |
| ASM/DEP | support\_phone\_number | Optional. String. A support phone number for the organization. |
| ASM/DEP | support\_email\_address | Optional. String. A support email address for the organization. This key is valid in X-Server-Protocol-Version 2 and later. |
| ASM/DEP | department | Optional. String. The user-defined department or location name. |
| ASM/DEP | devices | Array of strings containing device serial numbers. (Might be empty.) |
| VPP | Intune UserId guid | GUID generated by Intune. |
| VPP | Location Token | Secure token used to link Intune with an Apple Business Manager or Apple School Manager tenant. |
| VPP | Managed AppleId UPN | AppleID that was specified by Admin when configuring the Apple Business Manager or Apple School Manager location token (VPP token) connection with Apple. |
| VPP | Serial Number | Serial number of the managed device. |

To stop using Apple services with Microsoft Intune and delete the data, you must both disable the Microsoft Intune Apple token and also delete your Apple account. Refer to Apple account how to perform account management.