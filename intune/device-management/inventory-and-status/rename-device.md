---
layout: Conceptual
title: Rename a device in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/rename-device
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to rename a single managed device or rename devices in bulk from the Microsoft Intune admin center, including platform-specific naming rules.
ms.date: 2026-07-05T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davguy
locale: en-us
document_id: 0a115f36-991d-abfa-71d1-b034b170bcbf
document_version_independent_id: 0a115f36-991d-abfa-71d1-b034b170bcbf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/inventory-and-status/rename-device.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/inventory-and-status/rename-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/inventory-and-status/rename-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f41c64dd-b31c-82f3-ff13-5ea0c864e9dc
---

# Rename a device in Microsoft Intune - Microsoft Intune | Microsoft Learn

Renaming a device changes the **Device name** displayed in the Microsoft Intune admin center. It doesn't affect the *Management name* in Intune or the *Device name* shown in the Company Portal. Renaming helps you keep names consistent across your inventory—for example, aligning names with asset tags, user roles, or location-based identifiers.

You rename a single device from its **Properties** tab, or rename multiple devices at once by using **Bulk Device Actions**.

## Supported platforms

Rename is supported on:

- Android Enterprise corporate-owned Fully Managed (COBO), Dedicated (COSU), and Corporate-Owned Work Profile (COPE)
- iOS/iPadOS in [Supervised mode](/en-us/intune/intune-service/remote-actions/device-supervised-mode)
- macOS (corporate-owned)
- Windows (corporate-owned)

Note

- **Android Enterprise**: Renaming changes only the **Device name** in the admin center, not the name on the device. This friendly name is one that users can change. It can take 10 minutes or more for a renamed device to update in the **Devices** list.
- **Windows**: Renaming Microsoft Entra hybrid joined devices from Intune isn't supported. To rename hybrid joined devices, use domain-based methods outside Intune.
- **iOS/iPadOS**: If you use an enrollment profile with a Device Name Template, the device is renamed but reverts to the template after the next sync with Intune.

## Rename a single device

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. Select the **Properties** tab, and then select **Edit**.
4. Update the device name. The allowed characters depend on the platform:
    - **Windows**: 63 characters or fewer (excluding trailing NULL); not null or empty; letters (a–z, A–Z), numbers (0–9), and hyphens; Unicode characters ≥ 0x80 must be valid UTF-8 and IDN-mappable; names can't be only numbers; no spaces; and these characters aren't allowed: `{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ( ) + / , . _ *`
    - **iOS/iPadOS and macOS**: Letters, numbers, and hyphens. The name must contain at least one letter or hyphen.
    - **Android**: Letters, numbers, and hyphens.
5. For Windows, to restart the device after renaming, set **Restart after rename** to **Yes**.
6. Save your changes.

## Bulk rename devices

You can rename devices in bulk by platform, using **Bulk Device Actions**. Bulk rename follows the same naming rules as a single rename, but you must include one of the following variables in the name:

- `{{serialnumber}}` — adds the device's serial number to the name.
- `{{rand:x}}` — adds a random string of numbers, where *x* is the number of digits.

To bulk rename devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Select **Bulk Device Actions**.
3. On the **Basics** page, select the **OS** of the devices you want to rename, and for **Device action** select **Rename**.
4. Complete the configuration wizard.

## Reference links

- Microsoft Graph API: [setDeviceName action](/en-us/graph/api/intune-devices-manageddevice-setdevicename)
- Configuration service provider (CSP) used to initiate the rename action on Windows: [Accounts CSP](/en-us/windows/client-management/mdm/accounts-csp)