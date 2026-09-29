---
layout: Conceptual
title: View device details - Microsoft Intune | Microsoft Learn
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
description: Learn how to access device details in the Microsoft Intune admin center, including hardware information, installed apps, and device properties.
ms.date: 2026-07-04T00:00:00.0000000Z
ms.topic: how-to
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
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: c564587c-26f8-2062-9c1e-0e6764e728ba
---

# View device details - Microsoft Intune | Microsoft Learn

The **Device details** tab shows the read-only inventory that Intune collects from a managed device, including hardware, operating system, network, and storage information. It's one of the tabs on a device's **Overview** page, alongside **Monitor** (status dashboards), **Properties** (editable settings), and **Device action status**.

To view a device's details:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. Select the **Device details** tab.

Tip

To change editable settings—such as the device name, ownership, primary user, notes, or scope tags—use the **Properties** tab. See [Edit device properties](edit-device-properties). To find installed apps, app configuration, BitLocker recovery keys, and other information, use the navigation pane on the device page—for example, [Discovered apps](../../app-management/discovered-apps) under **Reports**, or **BitLocker recovery keys** under **Tools**.

Note

Hardware and software inventory refreshes in the Intune service every seven days, starting from the date of enrollment.

## Hardware details

This section lists the hardware details exposed by the device, divided into the following categories:

### System

| Property | Description | Platform |
| --- | --- | --- |
| Device name | The name of the device. | All |
| Intune device name | An easily recognizable device name used only in the Intune admin center. Changing this name doesn't change the device name or the name in the Company Portal. | All |
| Intune device ID | A GUID that uniquely identifies the device in Intune. | All |
| Registered in Microsoft Entra | If **Yes**, the device is registered in Microsoft Entra. | All |
| Microsoft Entra device ID | A GUID that uniquely identifies the device in Microsoft Entra. | All |
| Serial number | The device's serial number from the manufacturer. | All |
| Last check-in | The date and time that the device last connected to Intune. | All |

Note

Due to platform limitations, Intune might not be able to display the serial number for some Android personally owned work profile devices.

### Enrollment details

| Property | Description | Platform |
| --- | --- | --- |
| Enrollment profile | The name of the enrollment profile used to enroll the device in Intune. | All |
| Enrolled date | The date and time that the device was enrolled in Intune. | All |
| Enrolled by | The user that enrolled the device in Intune. | All |
| User approved enrollment | If **Yes**, the device has user approved enrollment that lets admins manage certain security settings on the device. | Windows, iOS |

Note

For Windows devices that are registered with [Windows Autopilot](/en-us/autopilot/add-devices), *Enrolled date* displays the time when you registered devices with Windows Autopilot instead of the time when you enrolled them.

### Operating system

| Property | Description | Platform |
| --- | --- | --- |
| Operating system | The operating system used on the device. | All |
| Operating system build number | The operating system's build number. | Android |
| Operating system edition | The operating system edition. | Windows |
| Operating system language | The language set for the operating system on the device. | Windows, iOS,Android |
| Operating system SKU | The operating system SKU. | Windows |
| Operating system version | The version of the operating system on the device. | All |
| Security patch level | The security patch level for the device. | Android |

### Network details

| Property | Description | Platform |
| --- | --- | --- |
| Ethernet MAC | The primary Ethernet MAC address for the device. For macOS devices with no Ethernet, the device reports the Wi-Fi MAC address. | Windows, macOS |
| ICCID | The Integrated Circuit Card Identifier, which is a SIM card's unique identification number | All |
| Wi-Fi IPv4 address | The IP address assigned to the device when connected to Wi-Fi. Any change to IPv4 might take up to 8 hours to reflect in Intune admin center from the time that network changes on device. | All |
| Wi-Fi MAC | The device's Media Access Control address. | All |
| Wi‑Fi subnet ID | The device's subnet ID. | Android |
| Wired IPv4 IP address | The device's IPv4 address assigned when connected to a wired network. | All |
| Subscriber carrier | The device's wireless carrier. | Windows, iOS/iPadOS, Android |

Note

- Reporting for ICCID isn't supported for Android Enterprise corporate-owned work profile devices. For Android Enterprise fully managed and dedicated devices, reporting for ICCID is supported; however, certain SIM cards don't write the data and therefore the ICCID isn't reported in such cases.
- Intune doesn't display Wi-Fi MAC addresses for personally-owned work profile devices.
- Wi-Fi subnet ID - Android Enterprise fully managed, dedicated, and corporate-owned work profiles. Any change to IPv4 or subnet ID might take up to 8 hours to reflect in Intune admin center from the time that network changes on device.
- Wi-Fi IPv4 address - Windows, Android Enterprise fully managed, dedicated, and corporate-owned work profiles. Any change to IPv4 or subnet ID might take up to 8 hours to reflect in Intune admin center from the time that network changes on device.
- Reporting for subscriber carrier isn't supported for Android Enterprise corporate-owned work profile devices. For Android Enterprise fully managed and dedicated devices, reporting for subscriber carrier is supported; however, certain SIM cards don't write the data and therefore the subscriber carrier isn't reported in such cases.

### Storage

| Property | Description | Platform |
| --- | --- | --- |
| Free storage space | The unused storage space on the device (in gigabytes). | Windows, macOS, iOS |
| Total physical memory | The total physical memory on the device (in gigabytes). | Windows |
| Total storage space | The total storage space on the device (in gigabytes). | Windows, iOS |
| Resident users | The number of users currently on a shared iPad device, or defaults to null if the number of users can't be determined. | iPadOS |

### System enclosure

| Property | Description | Platform |
| --- | --- | --- |
| PowerPrecision Battery Health | State-of-Health rating as determined by Zebra (PowerPrecision+ batteries only). | Android |
| PowerPrecision Battery Charge Cycles Consumed | Number of full charge cycles consumed as determined by Zebra (PowerPrecision batteries only). | Android |
| Last Battery Check-in | Date of last check-in for battery last found in the device as determined by Zebra (PowerPrecision and PowerPrecision+ batteries only). | Android |
| Battery Serial Number | Serial number of the battery pack last found in the device as determined by Zebra (PowerPrecision and PowerPrecision+ batteries only). | Android |
| Battery Level | Shows the battery level of the device, between 0 and 100. It defaults to null if the battery level can't be determined. | iOS, macOS |
| Device Manufacturer | The manufacturer of the device. | All |
| IMEI | The device's International Mobile Equipment Identity. | All except Android personally owned work profile devices. |
| MEID | The device's mobile equipment identifier. | All except Android personally owned work profile devices. |
| Phone | The phone number assigned to the device. | All |
| Processor architecture | The processor architecture of the device, such as x64 or ARM. | All |
| Product name | The product name of the device, such as Surface Pro 7. | All |
| System management BIOS version | The version of the system management BIOS on the device. | Windows |
| TPM manufacturer ID | The manufacturer ID of the Trusted Platform Module (TPM) on the device. | Windows |
| TPM manufacturer version | The manufacturer version of the Trusted Platform Module (TPM) on the device. | Windows |
| TPM version | The version of the Trusted Platform Module (TPM) on the device. | Windows |

Note

- Android Enterprise corporate-owned work profile devices don't support reporting for phone number. Android Enterprise fully managed and dedicated devices support reporting for phone number; however, certain SIM cards don't write the data and therefore the phone number isn't reported in such cases.
- For multi-SIM iOS/iPadOS devices, Intune has no control over which SIM data is assigned to the Service Subscription slots on the device for the ICCID, IMEI, MEID, and Phone number values. Intune only reports the first available values received from the device in the following order: CT Subscription Slot One, CT Subscription Slot Two, Top-level ICCID, IMEI, and MEID.

### Conditional access

| Property | Description | Platform |
| --- | --- | --- |
| Actication lock bypass code | The code that can be used to [disable the activation lock](../actions/disable-activation-lock). | iOS, macOS |
| Compliance | The device's compliance state as evaluated by Intune. A compliant device meets all the requirements of the assigned compliance policies, while a non-compliant device fails to meet one or more requirements. Compliance status is used in conditional access policies to allow or block access to resources based on the device's compliance state. | All |
| EAS activated | If **Yes**, then the device is synchronized with an Exchange mailbox. This means that the device is actively communicating with the Exchange server to receive emails, calendar updates, and other mailbox-related information. | All |
| EAS activation ID | The device's Exchange ActiveSync identifier. This unique identifier is used to manage and track the device's synchronization status with the Exchange server, and can be helpful for troubleshooting synchronization issues or managing devices in an organization. | All |
| EAS activation time | The date and time when the device was activated with Exchange ActiveSync. | All |
| Encrypted | If **Yes**, the data stored on the device is encrypted. | All |
| Jailbroken | If **Yes**, the device is jailbroken, which means it has been modified to remove restrictions imposed by the operating system, allowing the installation of unauthorized apps and potentially exposing the device to security risks. | iOS, Android |
| Supervised | If **Yes**, administrators have enhanced control over the device. | iOS, macOS |