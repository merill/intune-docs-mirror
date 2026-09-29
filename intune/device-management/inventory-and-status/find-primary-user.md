---
layout: Conceptual
title: Change a device's primary user in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/find-primary-user
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Change or reassign the primary user (device affinity) of a managed device in the Microsoft Intune admin center, and learn how the primary user is assigned.
ms.date: 2026-07-05T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davguy
locale: en-us
document_id: 5cadefe7-0baf-c2f7-adb4-346b7e2595ad
document_version_independent_id: 5cadefe7-0baf-c2f7-adb4-346b7e2595ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/inventory-and-status/find-primary-user.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/inventory-and-status/find-primary-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/inventory-and-status/find-primary-user.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 93d462bd-dc0b-67c1-9015-ab26c5173265
---

# Change a device's primary user in Microsoft Intune - Microsoft Intune | Microsoft Learn

A primary user is the user who is primarily associated with a specific Intune device. When a device enrolls in Intune, the signed-in user typically becomes the primary user. The primary user also shows as a device property that you can view and update.

You change or remove a device's primary user from the device's **Properties** tab. This article explains how, and describes how Intune assigns the primary user and where it's used.

When a device is associated with a user, then that association is known as **Device Affinity**.

An Intune device can have one primary user assigned to it, or no user assigned. When there's no primary user assigned, the device is called a **Shared Device**.

The primary user property maps a licensed Intune user to their devices in:

- The Company Portal app
- End-user website
- IT pro experiences, like troubleshooting pages in the Azure portal. These pages map user accounts to devices by using the primary user.

## Intune automatically adds primary user

Intune automatically adds primary user to devices during or soon after enrollment. The enrollment method determines when the primary user is added to a device.

| Platform | Enrollment method | Primary user assigned | Primary user is assigned |
| --- | --- | --- | --- |
| Windows | Add work or school (user driven) | Enrolling user | During enrollment |
| Windows | Modern App sign-in (user driven) | Enrolling user | During enrollment |
| Windows | Enroll in mobile device management (MDM) only (user driven) | Enrolling user | During enrollment |
| Windows | Microsoft Entra join (out of box experience) | Enrolling user | During enrollment |
| Windows | Microsoft Entra join (Windows Autopilot out of box experience) | Enrolling user | During enrollment |
| Windows | Enroll in MDM only | Enrolling user | During enrollment |
| Windows | Microsoft Entra hybrid join + automatic enrollment GPO | First user to sign in to Windows | When first user signs in to Windows |
| Windows | Co-management | First user to sign in to Windows | When first user signs in to Windows |
| Windows | Microsoft Entra join (bulk enrollment token) | None | Not applicable |
| Windows | Microsoft Entra join (Windows Autopilot self-deploying mode) | None | Not applicable |
| Cross-platform | User driven enrollment with Company Portal App | Enrolling user | During enrollment |
| Cross-platform | Device Enrollment Manager (DEM) | Enrolling DEM user | During enrollment |
| iOS/iPadOS, macOS | Apple Automated Device Enrollment (DEP with User Affinity) | Enrolling user | During enrollment |
| iOS/iPadOS, macOS | Apple Automated Device Enrollment (DEP without User Affinity) | None | Not applicable |
| Android | Android Corporate-Owned, Dedicated devices | None | Not applicable |

## Company Portal app and the primary user

The Company Portal app expects that the user account that signed in to the Company Portal is the primary user of that device. If you assign another user as the primary user, the Company Portal shows the following warning:

`This device is already assigned to someone in your organization. Contact company support about becoming the primary device user. You can continue to use Company Portal but functionality is limited.`

If an Intune device has no primary user assigned, then the Company Portal app detects it as a shared device. Shared devices are visually identifiable with a "shared" label in the device tile. In this mode, the Company Portal can still be used to request and install available apps. However, uninstalling apps and self-service actions, like reset, rename, and retire, aren't available.

To appear in the Company Portal on shared devices, available apps might be assigned to the device or user. They're installed in the system context or user context, depending on how the app was configured by the IT administrator. For more information about app context, see [Install apps on Windows devices](../../app-management/deployment/deploy-windows). Company Portal version 10.3.4651.0 or later is required to use this feature.

## Primary user and Microsoft Entra device owner

In some cases, the Intune primary user can be different from the Microsoft Entra Device's **Owner** property (viewable under **Devices** &gt; **Microsoft Entra Devices**). The Microsoft Entra Device owner is added during a device's registration into Microsoft Entra ID.

For newly enrolled Microsoft Entra devices, the Microsoft Entra ID **Owner** property is automatically set at the same time that the Intune primary user is set.

## Find a device's primary user

Use the following steps to find the primary user of a device:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choose **Devices** &gt; choose a device.
3. On the **Overview** page, you can see the primary user listed.

## Change the primary user

For Windows devices that are Microsoft Entra joined or Microsoft Entra hybrid joined, the primary user of a device can be updated.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choose **Devices** &gt; **All devices** &gt; choose a Windows device &gt; **Properties** &gt; **Change primary user**.
3. Select a new user and choose **Select**.

After the primary user is updated, it will also be updated in Intune and Microsoft Entra device blades.

### What you need to know

- Supported on Windows devices only. Enrollment is required to assign a new primary user on iOS/iPadOS and Android devices.
- Supported on Microsoft Entra joined and Microsoft Entra hybrid joined devices only. Not supported on devices that are Microsoft Entra registered only.
- To be assigned as the Primary user, the user must be licensed for Intune.
- Updates to the primary user across Intune and Microsoft Entra ID can take up to 10 minutes to be reflected.
- Changing the primary user of the device doesn't make any changes to local group membership such as adding or removing users from the "Administrators" local group.
- Changing the primary user doesn't change the "Enrolled by" user in Intune.
- To change or remove the Primary user of a device, you need the **Managed devices/Set primary user** permission.