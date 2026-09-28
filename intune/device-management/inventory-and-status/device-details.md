---
layout: Conceptual
title: View device details with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to view hardware, app, compliance, and configuration details for devices managed with Microsoft Intune to monitor status and troubleshoot issues.
ms.date: 2026-08-20T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
ms.reviewer: davguy
locale: en-us
document_id: 28c77ff8-8fe6-7279-1ae2-e1a33a3c61c1
document_version_independent_id: 28c77ff8-8fe6-7279-1ae2-e1a33a3c61c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/inventory-and-status/device-details.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/inventory-and-status/device-details
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/inventory-and-status/device-details.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: c564587c-26f8-2062-9c1e-0e6764e728ba
---

# View device details with Microsoft Intune - Microsoft Intune | Microsoft Learn

The **Devices** feature provides more details about the devices you manage, including their hardware and the apps installed.

This article shows you how to view all your devices, and their properties in the Microsoft Intune admin center.

## View the device details

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **All devices** &gt; select one of your listed devices to open its details:

    - **Overview** shows the device name, and lists some key properties of the device, like whether it's a personal or corporate device, serial number, primary user, and more. Depending on the device platform, you can perform different actions. For more information, see [Use remote actions to manage devices using Intune](../actions/).
    - Use **Properties** to assign a [device category you create](../create-device-categories), and change ownership of the device to a personal device, or a corporate device.
    - **Hardware** includes many details about the device, like the device ID, operating system and version, storage space, and more details.
    - **Discovered apps** lists all the apps that Intune found installed on the device, and the app versions. For more information, see [Intune discovered apps](../../app-management/discovered-apps).
    - **Device compliance** lists all assigned compliance policies, and if the device is compliant or not compliant.
    - **Device configuration** shows all device configuration policies assigned to the device, and if the policy succeeded or failed.
    - **App configuration**
    - **Recovery keys** shows available BitLocker keys found for the device
    - **Managed apps** lists all the managed apps that Intune configured and has deployed to the device.

## Hardware device details

Depending on the carrier used by the devices, not all details might be collected.

Note

Hardware and Software inventory is refreshed in the Intune service every 7 days, starting from the date of enrollment.

Note

Hardware device details are currently not supported for Linux devices.

| Detail | Description | Platform |
| --- | --- | --- |
| Name | The name of the device. | Windows, macOS, iOS, Android |
| Management name | An easily recognizable device name used only in the Intune admin center. Changing this name does not change the device name or the name in the Company Portal. | Windows, macOS, iOS, Android  NOTE: Management names won't automatically populate for Android Enterprise dedicated, fully managed, and corporate-owned with work profile devices that were enrolled before November 2021. However, the admin may still edit the management name. |
| UDID | The device's Unique Device identifier. | macOS, iOS |
| Intune Device ID | A GUID that uniquely identifies the device. | Windows, macOS, iOS, Android |
| Serial number | The device's serial number from the manufacturer. | Windows, macOS, iOS, iPadOS, Android  NOTE: Intune might not be able to display the serial number for personally owned work profile devices running Android 12 and newer due to platform limitations. |
| Shared device | If **Yes**, the device is shared by more than one user. | Windows, iOS |
| User approved enrollment | If **Yes**, then the device has user approved enrollment that lets admins manage certain security settings on the device. | Windows, iOS |
| Operating system | The operating system used on the device. | Windows, macOS, iOS, Android |
| Operating system version | The version of the operating system on the device. | Windows, iOS, iPadOS, Android |
| Operating system language | The language set for the operating system on the device. | Windows, iOS, Android |
| Build number | The operating system's build number. | Android |
| Security patch level | The security patch level for the device. | Android |
| Total storage space | The total storage space on the device (in gigabytes). | Windows, macOS, iOS |
| Total physical memory | The total physical memory on the device (in gigabytes). | Windows |
| Free storage space | The unused storage space on the device (in gigabytes). | Windows, iOS |
| PowerPrecision+ Battery Health | State-of-Health rating as determined by Zebra (PowerPrecision+ batteries only). | Android |
| PowerPrecision Battery Charge Cycles Consumed | Number of full charge cycles consumed as determined by Zebra (PowerPrecision batteries only). | Android |
| Last Battery Check-in | Date of last check-in for battery last found in the device as determined by Zebra (PowerPrecision and PowerPrecision+ batteries only). | Android |
| Battery Serial Number | Serial number of the battery pack last found in the device as determined by Zebra (PowerPrecision and PowerPrecision+ batteries only). | Android |
| IMEI | The device's International Mobile Equipment Identity. | Windows, iOS/iPadOS, Android  On Android Enterprise fully managed, dedicated, and corporate-owned work profile devices, Intune reports all IMEI numbers for the device (usually one or two). |
| MEID | The device's mobile equipment identifier. | Windows, iOS/iPadOS, Android  NOTE: Intune might not be able to display MEID for personally owned work profile devices running Android 12 and newer due to platform limitations. |
| Manufacturer | The manufacturer of the device. | Windows, macOS, iOS/iPadOS, Android |
| Model | The model of the device. | Windows, macOS, iOS/iPadOS, Android |
| Phone number | The phone number assigned to the device. | Windows, iOS/iPadOS, Android  On Android Enterprise corporate-owned fully managed (COBO) and corporate-owned dedicated (COSU) devices running Android 15 and later, expanded SIM inventory reports the phone number associated with each SIM. Reporting isn't supported for corporate-owned work profile (COPE) devices. Some SIM cards don't provide the phone number, so the value might not be reported. |
| Subscriber carrier | The device's wireless carrier. | Windows, iOS/iPadOS, Android  On Android Enterprise corporate-owned fully managed (COBO) and corporate-owned dedicated (COSU) devices running Android 15 and later, expanded SIM inventory reports the carrier name for each eSIM. Reporting isn't supported for corporate-owned work profile (COPE) devices. Some SIM cards don't provide the carrier name, so the value might not be reported. |
| Cellular technology | The radio system used by the device. | Windows, iOS/iPadOS, Android |
| Wi-Fi MAC | The device's Media Access Control address. | Windows, macOS, iOS/iPadOS, Android**NOTE**: As of October 2021, Intune doesn't display Wi-Fi MAC addresses for newly enrolled personally owned work profile devices and devices managed with device administrator running Android 9 and later. |
| Ethernet MAC | The primary Ethernet MAC address for the device. For macOS devices with no ethernet, the device reports the Wi-Fi MAC address. | macOS |
| ICCID | The Integrated Circuit Card Identifier, which is a SIM card's unique identification number. | Windows, iOS/iPadOS, Android Enterprise corporate-owned fully managed (COBO), corporate-owned dedicated (COSU), and corporate-owned work profile (COPE) devices  On corporate-owned devices running Android 15 and later, Intune reports all ICCIDs for all physical SIMs and eSIM profiles. On earlier Android versions, COBO and COSU devices report a single ICCID when the SIM provides the value. Full multi-ICCID inventory lets you identify the correct ICCID for a [**Remove eSIM** action](../actions/update-cellular-data-plan#remove-an-esim-from-one-android-enterprise-device). |
| EID | The eSIM identifier, which is a unique identifier for the embedded SIM (eSIM) for cellular devices that have an eSIM. | iOS/iPadOS, Android Enterprise COBO, COSU, and COPE devices running Android 13 and later. On supported corporate-owned Android devices, Intune reports all EIDs. |
| Activation state | The activation state of each deployed eSIM. | Android Enterprise COBO, COSU, and COPE devices running Android 15 and later. |
| SIM origin | Indicates whether an eSIM was added by an admin or locally on the device, or whether the SIM is physical. | Android Enterprise COBO, COSU, and COPE devices running Android 15 and later. |
| Wi-Fi IPv4 address | The device's IPv4 address. | Windows, Android Enterprise fully managed, dedicated and corp-owned work profiles.**NOTE**: Any change to IPv4 or subnet ID may take up to 8 hours to reflect in Intune admin center from the time that network changes on device. |
| Wi-Fi subnet ID | The device's subnet ID. | Android Enterprise fully managed, dedicated and corp-owned work profiles.**NOTE**: Any change to IPv4 or subnet ID may take up to 8 hours to reflect in Intune admin center from the time that network changes on device. |
| Enrolled date | The date and time that the device was enrolled in Intune. | Windows, macOS, iOS/iPadOS, Android |
| Last contact | The date and time that the device last connected to Intune. | Windows, macOS, iOS/iPadOS, Android |
| Activation lock bypass code | The code that can be used to disable the activation lock. | iOS |
| Microsoft Entra registered | If **Yes**, the device is registered with Azure Directory. | Windows, macOS, iOS/iPadOS, Android |
| Intune registered | If **Yes**, the device is registered with Intune | Windows, macOS, iOS/iPadOS, Android |
| Compliance | The device's compliance state. | Windows, macOS, iOS/iPadOS, Android |
| EAS activated | If **Yes**, then the device is synchronized with an Exchange mailbox. | Windows, macOS, iOS/iPadOS, Android |
| EAS activation ID | The device's Exchange ActiveSync identifier. | Windows, macOS, iOS/iPadOS, Android |
| Supervised | If **Yes**, administrators have enhanced control over the device. | iOS/iPadOS |
| Encrypted | If **Yes**, the data stored on the device is encrypted. | Windows, macOS, iOS/iPadOS, Android |
| Product Name | The product name of the device, such as iPad 8. | iOS/iPadOS, macOS |
| Battery level | Shows the battery level of the device, between 0 and 100, or defaults to null if the battery level can't be determined. | iOS/iPadOS |
| Resident users | Shows the number of users currently on the shared iPad device, or defaults to null if the number of users can't be determined. | iOS/iPadOS |

Note

- For Windows devices that are registered with [Windows Autopilot service](/en-us/autopilot/add-devices), Enrolled date displays the time when devices were registered with Windows Autopilot instead of the time when they were enrolled.
- For multi-SIM iOS/iPadOS devices, Intune has no control over which SIM data is assigned to the Service Subscription slots on the device for the ICCID, IMEI, MEID, and Phone number values. Intune only reports the first available values received from the device in the following order:
- CT Subscription Slot One &gt; - CT Subscription Slot Two &gt; - Top-level ICCID, IMEI, MEID, and Phone number properties (deprecated)