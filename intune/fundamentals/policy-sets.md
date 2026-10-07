---
layout: Conceptual
title: Policy Sets - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/policy-sets
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Use policy sets to group collections of management objects in Microsoft Intune.
ms.date: 2024-04-10T00:00:00.0000000Z
ms.topic: article
ms.reviewer: DaGerrit
locale: en-us
document_id: 2f6a9513-12ac-8fa6-571d-2f2db92660bc
document_version_independent_id: 2f6a9513-12ac-8fa6-571d-2f2db92660bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/policy-sets.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/policy-sets
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/policy-sets.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: e0108355-577b-4269-f52c-a98aeeff1407
---

# Policy Sets - Microsoft Intune | Microsoft Learn

Policy sets allow you to create a bundle of references to already existing management entities that need to be identified, targeted, and monitored as a single conceptual unit. A policy set is an assignable collection of apps, policies, and other management objects you've created. Creating a policy set enables you to select many different objects at once, and assign them from a single place. As your organization changes, you can revisit a policy set to add or remove its objects and assignments. You can use a policy set to associate and assign existing objects, such as apps, policies, and VPNs in a single package.

Important

For a list of known issues related to policy sets, [Policy sets known issues](policy-sets#policy-sets-known-issues).

Policy sets don't replace existing concepts or objects. You can continue to assign individual objects and you can also reference individual objects as part of a policy set. Therefore, any changes to those individual objects will be reflected in the policy set.​

You can use policy sets to:

- Group objects that need to be assigned together
- Assign your organization's minimum configuration requirements on all managed devices
- Assign commonly used or relevant apps to all users

You can include the following management objects in a policy set:

- Apps
- App configuration policies
- App protection policies
- Device configuration profiles
- Device compliance policies
- Windows autopilot deployment profiles
- Enrollment status page
- Settings catalog policies

Important

As of September 2021, enrollment restrictions based on device type can no longer be included in policy sets. For more information about how to create enrollment restrictions, see [Set enrollment restrictions](../device-enrollment/restrictions).

When you create a policy set, you create a single unit of assignment, and manage associations between different objects. A policy set will be a reference to objects external to it. Any changes in the included objects will affect the policy set as well. After you create a policy set, you can repeatedly view and edit its objects and assignments.

Note

Policy sets support Windows, Android, macOS, and iOS/iPadOS settings, and can be assigned cross-platform.

## How to create a policy set

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Policy Sets** &gt; **Policy sets** &gt; **Create**.
3. On the **Basics** page, add the following values:

    - **Policy set name** - Provide a name for this policy set.
    - **Description** - Optionally, provide a description for the policy set.

    ![Create policy set - Basics](media/policy-sets/policy-sets-01.png)
4. Click **Next: Application management**. On the **Application management** page you can optionally [add apps](../app-management/deployment/), [app configuration policies](../app-management/configuration/overview), and [app protection policies](../app-management/protection/overview) to your policy set. For information about app management, see [What is Microsoft Intune app management?](../app-management/overview).
5. Click **Next: Device management**. The **Device management** page allows you to add device management objects to your policy set, such as [device configuration profiles](../device-configuration/overview) and [device compliance policies](../device-security/compliance/overview). Be sure to include all associated objects, such as other policies, certificates, and security baseline profiles.
6. Click **Next: Device enrollment**. The **Device enrollment** page allows you to add device enrollment objects to your policy set, such as [Windows Autopilot deployment profiles](/en-us/autopilot/enrollment-autopilot), and [enrollment status page profiles](../device-enrollment/windows/setup-status-page).
7. Click **Next: Assignments**. The **Assignments** page allows you can assign the policy set to users and devices. It's important to note that you can assign a policy set to a device whether or not the device is managed by Intune.
8. Click **Next: Review + create** to review the values you entered for the profile.
9. When you're done, click **Create** to create the policy set in Intune.

## Policy sets known issues

Policy sets, new to 1910, have the following known issues.

- When creating a policy set, if a scoped admin tries to create a policy set without any scope tags selected, upon reaching the **Review + Create** page, validation will fail and an error will be displayed on the status bar. The admin must switch to a different page in the process, then return to the **Review + Create** page. This will enable the **Create** option.
- The following app types are currently supported by policy sets:

    - iOS/iPadOS store app
    - iOS/iPadOS line-of-business app
    - Managed iOS/iPadOS line-of-business app
    - Android store app
    - Android line-of-business app
    - Managed Android line-of-business app
    - Microsoft 365 Apps
    - Microsoft 365 Apps (macOS)
    - Microsoft Edge
    - Microsoft Edge (macOS)
    - Microsoft Defender ATP (macOS)
    - Windows MSI line-of-business app
    - Web link
    - Built-In iOS/iPadOS app
    - Built-In Android app

Note

Policy sets supports a subset of Intune App, Policy and Platform types. If an app or policy type is not available in the Policy Set picker experience, it is not officially supported.

- Setting a policy set assignment of **All Users** to **Autopilot Profile** is unsupported.
- Policy sets have the following enrollment restrictions and Enrollment Status Page (ESP) issues:

    - Restrictions and ESP don't support virtual group assignments.
    - Restrictions and ESP don't strictly support exclusion group assignments.
    - Restrictions and ESP use priority-based conflict resolution. Restrictions and ESP might not be applied to the same users as the rest of a policy set's payloads if the restrictions and ESP are also targeted by a higher priority restriction and ESP.
    - The default restrictions and ESP can't be added to a policy set.
- MAM policy types that support policy sets include the following:

    - MAM iOS/iPadOS targeted managed app protection
    - MAM Android targeted managed app protection
    - MAM iOS/iPadOS targeted managed app configuration
    - MAM Android targeted managed app configuration
- MAM processes policy set assignments as direct assignments for the following policy types:

    - MAM iOS/iPadOS targeted managed app protection
    - MAM Android targeted managed app protection
    - MAM iOS/iPadOS targeted managed app configuration
    - MAM Android targeted managed app configuration

        If a policy is added to a policy set that is deployed to a group, the group would show as directly assigned in the workload, not "assigned via the policy set". As a result of this, MAM doesn't process group assignment deletions coming from policy sets.
- MAM doesn't support deployment to **All Users** and **All Devices** virtual groups for any policy types.