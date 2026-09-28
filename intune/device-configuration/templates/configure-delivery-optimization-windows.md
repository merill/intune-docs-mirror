---
layout: Conceptual
title: Windows Delivery Optimization settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-delivery-optimization-windows
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
description: Configure device configuration policy to manage Delivery Optimization settings on Windows devices you manage with Intune.
ms.date: 2025-04-23T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: juidaewo; davguy
locale: en-us
document_id: 05450d68-c319-1432-6f50-1a43ee922e81
document_version_independent_id: 05450d68-c319-1432-6f50-1a43ee922e81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-delivery-optimization-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-delivery-optimization-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-delivery-optimization-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 72278645-cb7d-5879-2305-d2703009a456
---

# Windows Delivery Optimization settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

With Intune, you can use Delivery Optimization settings for your Windows devices to reduce bandwidth consumption when those devices download applications and updates. This article describes how to configure Delivery Optimization settings as part of an Intune device configuration profile. After you create a profile, you then assign or deploy that profile to your Windows devices.

Important

In April 2025, the settings format of the Delivery Optimization template was updated. Profiles for this new platform use the settings format as found in the Settings Catalog. With this change you can no longer create new versions of the old profile. Your existing instances of the old profile remain available to use.

For more information about this change, see the Intune Customer Success blog at [Support tip: Windows device configuration policies migrating to unified settings platform in Intune](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-windows-device-configuration-policies-migrating-to-unified-settings-/4189665).

- Learn about [Delivery Optimization updates](/en-us/windows/deployment/update/waas-delivery-optimization) in the Windows documentation.

This feature applies to:

- Windows

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New Policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Delivery Optimization**.
4. Select **Create**.
5. On the **Basics** page, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. On the **Configuration settings** page, define how you want updates and apps to download. For information about the settings that are available in the template, drill in to the information icon and then select the *Learn more* link to view that settings Configuration Service Provider (CSP) details directly from Windows.

    When you're done configuring settings, select **Next**.
8. On the **Scope tags** page (optional), assign scope tags to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next** to continue.
9. On the **Assignments** page, select the groups that receive this profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
10. On the **Review + create** page, when you're done, choose **Create**. The profile is created and is shown in the list.

The next time each device checks in, the policy is applied.