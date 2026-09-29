---
layout: Conceptual
title: Edit device properties in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/edit-device-properties
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to edit the modifiable properties of a managed device on the Properties tab in the Microsoft Intune admin center, including the device name, ownership, primary user, notes, and scope tags.
ms.date: 2026-07-05T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a6165eba-11fe-4eec-8dee-f4e5392f690f
document_version_independent_id: a6165eba-11fe-4eec-8dee-f4e5392f690f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/inventory-and-status/edit-device-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/inventory-and-status/edit-device-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/inventory-and-status/edit-device-properties.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b4e07a49-bb2e-e1f2-05ee-ec7a0402b1b1
---

# Edit device properties in Microsoft Intune - Microsoft Intune | Microsoft Learn

Each managed device has a set of properties that you can change from the **Properties** tab in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). These editable properties are separate from the read-only information on the **Device details** tab. For the read-only details, see [View device details](device-details).

The **Properties** tab lets you edit:

- **Intune device name** — the device name shown in the admin center. See [Rename a device](rename-device).
- **Ownership** — whether the device is corporate or personal.
- **Primary user** — the user primarily associated with the device.
- **Device notes** — free-form text to record admin context.
- **Scope tags** — tags that control which admins can see and manage the device.

## Open the Properties tab

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. Select the **Properties** tab, and then select **Edit**.
4. Change the properties you want to update, and then save your changes.

The rest of this article describes each editable property.

## Change ownership

Ownership identifies a device as **corporate** or **personal**. Ownership affects the management capabilities available for the device and the information Intune collects from it. On the **Properties** tab, select the ownership value that matches how the device is used in your organization, and then save your changes.

## Change the primary user

The primary user is the user primarily associated with the device (also known as *device affinity*). You change or remove a device's primary user from the **Properties** tab. For the steps, requirements, and important considerations—plus background on how the primary user is assigned—see [Change the primary user](find-primary-user#change-the-primary-user).

## Add device notes

Use **Notes** to record admin context about the device, such as its purpose, location, or a support reference. Notes are visible to admins in the admin center. Add or update the text on the **Properties** tab, and then save your changes.

## Edit scope tags

Scope tags control which admins can see and manage the device, based on their role assignments. In the device's **Scope tags** section, add or remove tags to align device visibility with your distributed IT model. For more information, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

Tip

You can also [assign a device category](../create-device-categories#change-the-category-of-a-device) to automatically group the device for easier management.