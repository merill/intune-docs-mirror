---
layout: Conceptual
title: Shared or multi-user Windows device settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-shared-device
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Add and use Windows 10/11 and Windows Holographic for Business devices that are shared, or used by multiple users in Microsoft Intune. See a list of all the settings and what they do on the devices, including Microsoft HoloLens. Control guest accounts, manage accounts and delete inactive accounts, allow or prevent saving to local storage, set power and sleep options, choose when updates are installed, and use devices in education environments in a device configuration profile.
ms.date: 2024-04-22T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: dbd7274c-3c61-ebb0-0d49-7300a3c0718c
document_version_independent_id: dbd7274c-3c61-ebb0-0d49-7300a3c0718c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-shared-device.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-shared-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-shared-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d57ff2d6-5189-a855-a35e-1ae3ddf19688
---

# Shared or multi-user Windows device settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Devices that have multiple users are called shared devices, and are a common part of mobile device management (MDM) solutions. Using Microsoft Intune, you can create and configure shared devices.

For example, schools have devices that are typically used by many students. School Intune admins can turn on the Shared PC feature to allow one user at a time. Students can't switch between different signed-in accounts on the device. When the student signs out, you also choose to remove all user-specific settings.

With this feature:

- End users can sign in to these shared devices with a guest account. After users sign in, the credentials are cached.
- You control if the guest account deletes when the user signs off, or delete inactive accounts when a threshold is reached.
- As end users use the device, they only get access to features you allow. For example, you:

    - Choose when the device goes in to sleep mode
    - Decide if users can see and save files locally
    - Can enable or disable power management settings

End users can sign in to these shared devices with a guest account. After users sign in, the credentials are cached. As they use the device, end-users only get access to features you allow.

For example, you choose when the device goes in to sleep mode, if users can see and save files locally, enable or disable power management settings, and more. You also control if the guest account deletes when the user signs-off, or delete inactive accounts when a threshold is reached.

This article shows you how to create a shared multi-user device configuration profile, and includes links to the available settings.

When you create the profile in Intune, you deploy or assign the profile to device groups in your organization. You can also assign this profile to device groups with mixed device types and operating system (OS) versions.

This feature applies to:

- Windows Professional
- Windows Enterprise
- Windows Holographic for Business, such as the HoloLens

Tip

For iOS/iPadOS shared devices, go to [shared device solutions for iOS/iPadOS](../../device-enrollment/apple/shared-device-solutions-ios).

## Prerequisites

- To create the policy, at a minimum, sign in with an account that has the **Policy and Profile Manager** Intune role. For more information, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Shared multi-user device**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Choose your platform for detailed settings:

    - [Windows](ref-shared-device-settings-windows)
    - [Windows Holographic for Business](ref-shared-device-settings-windows-holographic)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use role based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the devices group that receives your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.

    Note

    Be sure to assign the profile to device groups in your organization.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.