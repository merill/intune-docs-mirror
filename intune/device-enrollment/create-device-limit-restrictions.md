---
layout: Conceptual
title: Create device limit restrictions - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/create-device-limit-restrictions
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
description: Restrict the number of devices allowed to enroll in Microsoft Intune.
ms.date: 2025-05-15T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: maholdaa
locale: en-us
document_id: 716b3981-92db-3764-db08-93ab3f2d5ea4
document_version_independent_id: 716b3981-92db-3764-db08-93ab3f2d5ea4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/create-device-limit-restrictions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/create-device-limit-restrictions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/create-device-limit-restrictions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 41d5c44a-3b09-a83b-476d-1c1c12cd12c1
---

# Create device limit restrictions - Microsoft Intune | Microsoft Learn

Create a device limit enrollment restriction policy to limit the number of devices a user can enroll in Microsoft Intune. Device limit restrictions work on devices that meet the following criteria:

- Microsoft Intune-managed
- Established contact with Intune within last 90 days
- Not in a registration-pending state for more than 24 hours
- Hasn't failed Apple enrollment
- Hasn't been deleted from Microsoft Intune
- Enrollment type is not in shared mode (check DeviceCountsForDeviceCap for detail)

You can create a new device limit-enrollment restriction policy in the Microsoft Intune admin center or use the default policy that's already available. You can have up to 25 device limit restriction policies.

This article describes how to create and configure a device limit-enrollment restriction policy in the admin center.

## Default policy

Microsoft Intune provides one default policy for device limit restrictions that you can edit and customize as needed. Intune applies the default policy to all user and userless enrollments until you assign a higher-priority policy.

## Requirements

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Device limit restrictions are available for the following platforms:
> 
> - Android
> - iOS/iPadOS
> - macOS
> - Windows
> 

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To create device limit restrictions, you must be assigned the **Intune Service Administrator** role, which is built-in to Microsoft Entra ID. This role can create, edit, delete, and reprioritize device limit restrictions.
> 
> Other built-in Intune roles have read-only access to device limit restrictions. If you once assigned your users custom permissions that permitted them to manage device limit restrictions, those permissions are now limited to read-only access. You can apply scope tags to a device limit restriction to further limit access. For more information, see [RBAC with Microsoft Intune](../fundamentals/role-based-access-control/overview).

## Create a device limit restriction

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Windows**, **macOS**, **Apple mobile**, or **Android** tab.
4. Select **Device limit restriction**.
5. Choose **Create restriction**.
6. On the **Basics** page, give the restriction a **Name** and optional **Description**.
7. Choose **Next** to go to the **Device limit** page.
8. For **Device limit**, select the maximum number of devices that a user can enroll. ![Screenshot that shows how to choose a device limit.](media/restrictions/choose-device-limit.png)
9. Choose **Next** to go to the **Scope tags** page.
10. On the **Scope tags** page, optionally add the scope tags you want to apply to this restriction. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).
11. Choose **Next** to go to the **Assignments** page.
12. Choose **Select groups to include** and then use the search box to find groups that you want to include in this restriction. The restriction applies only to groups to which it's assigned. If you don't assign a restriction to at least one group, it won't have any effect. Then choose **Select**. ![Screenshot that shows selecting groups.](media/restrictions/select-groups-device-limit.png)
13. Select **Next** to go to the **Review + create** page.
14. Select **Create** to create the restriction. The new restriction appears in your list of restrictions and is given a higher priority than the default policy. For information about changing the priority level, see [Change restriction priority](create-device-limit-restrictions#change-restriction-priority) (in this article).

## Edit enrollment restrictions

Edits are applied to new enrollments and don't affect devices that are already enrolled.

1. Go to **Device limit restrictions** to see the list of your restrictions.
2. Select the name of the restriction you want to change.
3. Select **Properties**.
4. Select **Edit**.
5. Make your changes and select **Review + save**.
6. Review your changes and select **Save**.

## Change restriction priority

When a group is assigned multiple restrictions, the priority level determines which policy gets applied. The restriction with highest priority (*1* being the highest priority position) is applied and the other restrictions are disregarded. For example:

1. Joe belongs to two user groups in Intune: Group A and Group B.
2. Group A is assigned a restriction policy. Its priority level is 5.
3. Group B is assigned a restriction policy. The priority level is 2.
4. Joe is subject only to the priority 2 restrictions.

When you create a restriction, it's added to the list just above the default. You can change the priority of non-default restrictions.

1. Go to **Device limit restrictions**.
2. Select **Device limit restrictions** to bring up the list of your policies.
3. Hover over the policy in the **Priority** column, and then select and drag the priority to the desired position in the list.

## Device user experience

BYOD users who reach their device limit receive a message during enrollment explaining the restriction. To continue enrolling, the device user must unenroll an existing device. Alternatively, as the admin you can increase the device limit in the admin center. For more information about troubleshooting enrollment errors such as this one, see [Troubleshoot device enrollment](/en-us/troubleshoot/mem/intune/troubleshoot-device-enrollment-in-intune#device-cap-reached).

![Example image of device limit notification which reads, &quot;Couldn't add your device. You have added the maximum number of devices allowed by your IT support. You must remove a device before you can add a new one.](media/restrictions/enrollment-restrictions-ios-set-limit-notification.png)