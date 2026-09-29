---
layout: Conceptual
title: Create and assign device categories in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/create-device-categories
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Create device categories in Microsoft Intune, use them to populate dynamic Microsoft Entra security groups, and assign a category to a device.
ms.date: 2026-07-05T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mattcall
locale: en-us
document_id: cbc26d2f-193a-7668-e6da-6500555c678d
document_version_independent_id: cbc26d2f-193a-7668-e6da-6500555c678d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/create-device-categories.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/create-device-categories
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/create-device-categories.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 33f7b1c4-1e5e-7e16-a791-5d833417c9b2
---

# Create and assign device categories in Microsoft Intune - Microsoft Intune | Microsoft Learn

A **device category** is a label you assign to a device—such as *sales* or *accounting*—to help organize the devices you manage. Device categories are separate from Microsoft Entra security groups, but you can use them together: when you create a dynamic security group based on a category, Intune automatically adds any device assigned that category to the group.

This article explains how to create device categories, build dynamic Microsoft Entra security groups from them, and assign a category to a device.

## Requirements

Device categories are available for these platforms:

- Android
- iOS/iPadOS
- macOS
- Windows

To configure device categories, you must be an [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

## Before you begin

Decide if it's necessary to show the device category selection prompt to end users when they visit the Company Portal app or website. If you don't want the prompt to be visible, block it in a [customization profile](../app-management/configuration/configure-company-portal#device-categories) first, and then create your categories.

If Multi Admin Approval access policies are enabled for device actions, creating new categories, editing existing ones, and deleting device categories might require approval from a second administrator. To learn more, see [Use Access policies to require Multi Admin Approval](../fundamentals/role-based-access-control/multi-admin-approval).

## Step 1: Create device category in Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Manage devices**, and then select **Device categories**.
4. Choose **Create** to add a new category.
5. Enter the name of the new category, such as `HR` and an optional description.
6. Select **Next**.
7. Optionally, assign a scope tag, like `US-NC IT Team` or `JohnGlenn_ITDepartment`, to limit management of the category to specific IT groups. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).
8. Select **Next**.
9. Select **Create**. The new category is added to your **Device categories** list.

You'll use the device category name when you create Microsoft Entra security groups in the next step.

## Step 2: Create Microsoft Entra security groups

To enable automatic grouping, you must create a dynamic group using attribute-based rules in Microsoft Entra ID. For instructions, see [Using attributes to create advanced rules](/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) in the Microsoft Entra documentation. Create an advanced rule for your group using the **deviceCategory** attribute and the category name you created in Step 1 of this article.

For example, to create a rule that automatically groups devices belonging in the HR category, use the following rule syntax: `device.deviceCategory -eq "HR"`

Tip

If you only use device category groups for Intune policy and app targeting, you can use [assignment filters](../fundamentals/filters/overview) with the `deviceCategory` property instead of creating dynamic groups. Filters evaluate at check-in without depending on group membership processing. Dynamic groups remain necessary if the category groups are also used for Conditional Access, licensing, or other cross-workload scenarios.

## View categories of all devices

To view the device category assigned to each device, go to **Devices** &gt; **All devices**. The category is listed in the **Device category** column. To add the column to your table, select **Columns**, and then choose **Category** &gt; **Apply**.

When you delete a category, devices assigned to it appear as **Unassigned**.

## Change the category of a device

If you edit a category, be sure to update any Microsoft Entra security groups that reference the category in their rules.

1. Go to **Devices** &gt; **All devices**.
2. Select a device.
3. Select **Properties**.
4. Change the category listed under **Device category**.
5. Select **Save**.

## Best practices

Device categories are supported on devices running Android, iOS/iPadOS, macOS, and Windows. People with Windows devices must use the Company Portal website to select their category. The category prompt appears for all other platforms when the user signs in to the Company Portal app. Regardless of platform, any device user can sign in to portal.manage.microsoft.com at anytime and go to **My devices** to select a category.

If an iOS/iPadOS or Android device is already enrolled before you configure categories, the user will receive a notification about the device the user owns on the Company Portal website. The notification informs them that they need to select a category the next time they're in the Company Portal app.