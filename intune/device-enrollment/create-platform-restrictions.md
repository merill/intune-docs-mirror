---
layout: Conceptual
title: Create device platform restrictions - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/create-platform-restrictions
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
description: Restrict personally owned devices, and specific device platforms and OS versions from enrolling in Intune.
ms.date: 2024-07-01T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: maholdaa
locale: en-us
document_id: 5e1fba37-a3e1-181c-66a4-42d811517c3a
document_version_independent_id: 5e1fba37-a3e1-181c-66a4-42d811517c3a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/create-platform-restrictions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/create-platform-restrictions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/create-platform-restrictions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 06bd1c4c-6c11-2cc1-b0ac-df6a2a08c3c6
---

# Create device platform restrictions - Microsoft Intune | Microsoft Learn

Create a device platform enrollment restriction policy to restrict devices from enrolling in Intune. Available restrictions include:

- Device platform
- OS version
- Manufacturer
- Ownership (personally owned)

You can create a new device platform restriction policy in the Microsoft Intune admin center or use the default policy that's already available. You can have up to 25 device platform restriction policies.

This article describes the device platform restrictions supported in Microsoft Intune and how to configure them in the admin center.

## Requirements

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Device platform restrictions are available for the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - Windows
> 

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To create device platform restrictions, you must be signed in as [**Intune Administrator**](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator), a role built-in to Microsoft Entra ID. This role can create, edit, delete, and reprioritize device platform restrictions.
> 
> All other built-in Intune roles have read-only access to device platform restrictions. You can apply scope tags to a device platform restriction to further limit access. For more information, see [RBAC with Microsoft Intune](../fundamentals/role-based-access-control/overview).

## Default policy

Microsoft Intune provides one default policy for device platform restrictions that you can edit and customize as needed. Intune applies the default policy to all user and userless enrollments until you assign a higher-priority policy.

## Best practice - Android platform restrictions

Since Intune supports two Android platforms, it's important to understand how OS version restrictions work when you use them with device platform restrictions:

- If you allow both platforms for the same group, and then refine it for specific and nonoverlapping versions, Intune looks at the version to determine the Android enrollment flow devices go through.
- If you allow both platforms, but block the same versions, devices running blocked versions can't enroll. Users on these devices are sent through the Android device administrator enrollment flow before they're blocked and prompted to sign out.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Create a device platform restriction

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices**.
2. Under **Device onboarding**, select **Enrollment**.
3. Under **Enrollment options**, select **Device platform restriction**.
4. Select the tab along the top of the page that corresponds with the platform you're configuring. Your options:

    - **Windows restrictions**
    - **Android restrictions**
    - **macOS restrictions**
    - **iOS/iPadOS restrictions**
    - **tvOS restrictions**
    - **visionOS restrictions**
5. Select **Create restriction**.
6. On the **Basics** page, give the restriction a name and optional description.
7. Select **Next**.
8. On the **Platform settings** page, configure the restrictions for your selected platform. Your options:

    - **Platform** (Android): Select **Allow** to permit a platform to enroll, and **Block** to restrict it.
    - **MDM** (Windows, macOS, iOS/iPadOS, tvOS, and visionOS): Select **Allow** to permit a platform to enroll, and **Block** to restrict it.
    - **Personally-owned**: Select **Allow** to permit devices to enroll and operate as personal devices.
    - **Device manufacturer** (Android): Enter a comma-separated list of the manufacturers that you want to block.
    - **Allow min/max range** (Android, Windows, iOS/iPadOS): Enter the minimum and maximum OS versions allowed to enroll. Supported version formats include:

        - Windows supports major.minor.build.rev for Windows. Intune doesn't receive the revision number during enrollment so enter **0** for revision number.
        - Android device administrator and Android Enterprise work profile support major.minor.rev.build.
        - iOS/iPadOS supports major.minor.rev.

            Tip

            The min/max range isn't applicable to Apple devices that enroll with the Device Enrollment Program, Apple School Manager, or the Apple Configurator app. Although Intune doesn't block ADE enrollments that use Company Portal to authenticate, not meeting OS requirements impacts registration because devices can't create the Microsoft Entra device record used to evaluate Conditional Access policies. You can tell that this is the case if a device user receives an error message that says "Couldn't map device record with a user" after they sign in to Company Portal.
9. Select **Next**.
10. Optionally, add scope tags to the restriction. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).

    Note

    If you apply scope tags to a restriction, only Intune users within scope can view and manage the policy. Only people in scope can view and reorder a restriction, or change its priority level. They can also see the relative priority of the restriction, even if they can't see all restrictions.
11. Select **Next**.
12. On the **Assignments** page, select **Add groups** and then use the search box to find and select groups. To assign the restriction to all device users, select **Add all users**. If you don't assign a restriction to at least one group, the restriction won't take effect.
13. Optionally, after you assign groups, select **Edit filter** to restrict the policy assignment further with filters. Filters are available for macOS, iOS, and Windows policies. For more information, see [Apply assignment filters](create-platform-restrictions#apply-assignment-filters) in this article.
14. Select **Next**.
15. Review your policy, and then select **Create** to create it.

You can view the new restriction policy and access its properties in the **Enrollment device platform restrictions** &gt; **Device type restrictions** table. Select and drag the restriction to reposition it in the table and change its priority.

## Apply assignment filters

You can use assignment filters to include and exclude additional devices from certain group-targeted policies. Enrollment restrictions and ESP policies both support the use of assignment filters.

For example, you can use a filter to allow personal Windows devices to enroll while blocking devices that run a specific operating system SKU. To achieve this outcome, apply a preconfigured filter to your enrollment restriction assignments. The filter needs to have the `operatingSystemSKU` property in its rules. Example steps:

1. Create a platform enrollment restriction policy for Windows.
2. In the platform settings, select the option that allows personal devices to enroll.
3. In the assignments settings, select the groups you want to assign.
4. Select **Edit filter** and then apply your preconfigured filter that contains the `operatingSystemSKU` property. The applied property blocks devices running Windows 10 Home edition.

For more information about creating filters, see [Create a filter](../fundamentals/filters/overview).

Note

It takes extra time to process assignment filters during enrollment. The update between Microsoft Entra and Intune that processes user, group, and filter assignments typically happens within 15 minutes. It's not instant. This amount of time can affect enrollment assignments. You should wait and enroll devices several minutes after adding the enrolling users to a group, not immediately after.

### Supported filter properties

Enrollment restrictions support fewer filter properties than other group-targeted policies. This is because devices aren't yet enrolled, so Intune doesn't have the device info to support all properties. The limited selection of properties become available when you:

- Configure a device platform restriction policy for Apple and Windows devices.
- Configure an enrollment status page (ESP) policy for Windows.
- Edit a filter that's in-use in an enrollment restriction or ESP policy.

The following filter properties are always available to use with enrollment policies:

**Windows**

- Manufacturer - For Windows 11, version 22H2 and later with [KB5035942 (OS Builds 22621.3374 and 22631.3374)](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df).
- Model - For Windows 11, version 22H2 and later with [KB5035942 (OS Builds 22621.3374 and 22631.3374)](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df).
- OS version
- Operating system SKU
- Ownership
- Enrollment policy name

**iOS/iPadOS and macOS**

- Manufacturer
- Model
- OS version
- Ownership
- Enrollment policy name

For more information about these properties, see [device properties](../fundamentals/filters/ref-device-properties#available-properties). Filters can't be used with Android enrollment restrictions.

## Edit enrollment restrictions

Edits are applied to new enrollments and don't affect devices that are already enrolled.

1. Return to **Devices** &gt; **Enrollment**.
2. Select **Device platform restrictions** and then select the OS platform the restriction belongs to.
3. In the **Device type restrictions** table, select the name of the policy you want to change.
4. Select **Properties**.
5. Select **Edit**.
6. Make your changes and select **Review + save**.
7. Review your changes and select **Save**.