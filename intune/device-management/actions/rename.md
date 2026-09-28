---
layout: Conceptual
title: 'Device Action: Rename Device - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/rename
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.reviewer: mattcall
ms.subservice: remote-actions
zone_pivot_group_filename: device-management/actions/zone-pivot-groups.json
description: Learn how to use the Rename device action in Microsoft Intune to update the device name shown in the admin center. Useful for standardizing naming conventions, managing shared devices, and improving inventory clarity.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 51e33912-415a-402f-8201-8acebf3e4991
locale: en-us
document_id: 04048905-c64e-67b0-4a88-109410579e1a
document_version_independent_id: 04048905-c64e-67b0-4a88-109410579e1a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/rename.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/rename
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/rename.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/029d2366-5c16-4816-8cb8-dadeaf730762
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/082dcafd-01b6-47e9-8abe-5795dbab1ea9
platformId: d4f156cb-dae2-8581-0183-34a8d668bdc2
---

# Device Action: Rename Device - Microsoft Intune | Microsoft Learn

The *rename device* action in Microsoft Intune allows IT administrators to change the *Device name* displayed in the Intune admin center for a managed device. This action does not affect the *Management name* in Intune or the *Device name* shown in the Company Portal.

Renaming a device can help improve clarity and consistency across your device inventory—especially in environments with shared devices, standardized naming conventions, or large-scale deployments. It's useful for aligning device names with asset tags, user roles, or location-based identifiers, making it easier to manage and troubleshoot devices at scale.

::: zone pivot="android"

Note

Renaming Android Enterprise devices only changes the **Device name** in the Intune admin center and not on the device itself. The Device name in Intune is a friendly name that users can change.

::: zone-end

::: zone pivot="windows"

Note

Renaming Microsoft Entra hybrid joined devices from Intune is not supported. To rename hybrid joined devices, use domain-based methods outside of Intune.

::: zone-end

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Fully Managed (COBO)
> - Android Enterprise corporate-owned Dedicated (COSU)
> - Android Enterprise corporate-owned Work Profile (COPE)
> - iOS/iPadOS in [Supervised Mode](/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - macOS (corporate-owned)
> - Windows (corporate-owned)
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Set device name**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to rename a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Rename device**.

::: zone pivot="windows"

1. In the **Rename device**pane, type the new name in the text box. The new name must follow these rules:
    - Less than or equal to 63 characters, not including trailing NULL
    - Not null or an empty string
    - Allowed ASCII: Letters (a-z, A-Z), numbers (0-9), and hyphens
    - Allowed Unicode: characters &gt;= 0x80, must be valid UTF8, must be IDN-mappable (that is, RtlIdnToNameprepUnicode succeeds; see RFC 3492)
    - Names must not contain only numbers
    - No spaces in the name
    - Disallowed characters: `{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % `` ( ) + / , . _ *)`

::: zone-end

::: zone pivot="ios,macos"

1. In the **Rename device** pane, type the new name in the text box. You can use letters, numbers, and hyphens. The name must contain at least one letter or hyphen.

::: zone-end

::: zone pivot="android"

1. In the **Rename device** pane, type the new name in the text box. You can use letters, numbers, and hyphens.

::: zone-end

1. If you want to restart the device after renaming it, Select **Yes** next to **Restart after rename**.
2. Select **Rename**.

::: zone pivot="ios"

Note

If you have an iOS enrollment profile with a Device Name Template, the device will be renamed but will revert to the template after the next sync with Intune.

::: zone-end

::: zone pivot="android"

Note

It could take 10 minutes or more for a renamed Android Enterprise device to update in the **Devices** list.

::: zone-end

## How to bulk rename devices from the Intune admin center

You can choose to rename devices in bulk, based on the device platform. The bulk rename option uses the same rules as renaming a single device. However, you must also include one of the following variables as part of the device name:

- `{{serialnumber}}` - Add the device's serial number to the name.
- `{{rand:x}}` - Add a random string of numbers, where x equals the number of digits to add.

To use the bulk rename action:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. Select **Bulk Device Actions**.
3. On the Basics page, for **OS** select the platform of the devices you want to rename, and then for **Device action** select **Rename**.
4. Complete the configuration wizard.

## Reference links

- Microsoft Graph API: [setDeviceName action](/en-us/graph/api/intune-devices-manageddevice-setdevicename)

::: zone pivot="windows"

- Configuration service provider (CSP) used to initiate the action: [Accounts CSP](/en-us/windows/client-management/mdm/accounts-csp)

::: zone-end