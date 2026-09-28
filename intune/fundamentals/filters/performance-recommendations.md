---
layout: Conceptual
title: Assignment Filter Performance Tips for Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/filters/performance-recommendations
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
description: Optimize Microsoft Intune performance with assignment filters. Learn to use virtual groups, reuse groups, and apply filters effectively. Improve policy deployment speed with incremental group changes, and use assignment filters to include and exclude.
ms.date: 2026-06-30T00:00:00.0000000Z
ms.topic: article
ms.reviewer: mattcall
locale: en-us
document_id: b581ca5d-bc22-5020-3270-04fd1529b9e0
document_version_independent_id: b581ca5d-bc22-5020-3270-04fd1529b9e0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/filters/performance-recommendations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/filters/performance-recommendations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/filters/performance-recommendations.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 5c4a49ce-3385-24e7-2ac1-64bf53b3fe48
---

# Assignment Filter Performance Tips for Intune - Microsoft Intune | Microsoft Learn

When you create a policy, you can use [assignment filters](overview) to assign a policy based on rules you create. You can apply assignment filters to Intune-enrolled devices and Intune-managed apps. For an overview of assignment filters, go to [Use filters when assigning your apps, policies, and profiles in Microsoft Intune](overview).

When you create assignment filters, there are some performance recommendations you should consider.

This article lists and describes recommendations for Intune grouping, targeting, and filtering for your policies and apps. The goal is to help you make architecture and design decisions for Intune deployments in large environments.

These performance recommendations and their implementation can be different and depend on your own environment & other factors, including manageability and simplicity.

In this article:

- Get an overview of Intune grouping and targeting concepts
- Get some performance recommendations

For guidance on dynamic groups, go to [Create simpler, more efficient rules for dynamic groups in Microsoft Entra ID](/en-us/azure/active-directory/enterprise-users/groups-dynamic-rule-more-efficient).

## Overview of Intune grouping and targeting concepts

Let's review the grouping, targeting, and filtering features available in Intune.

### Microsoft Entra groups

Intune almost exclusively uses Microsoft Entra groups for grouping and targeting. When you select **Groups** in the Microsoft Intune admin center, you're looking at Microsoft Entra groups.

[![Screenshot of the Intune admin center, groups, and all groups in Microsoft Intune.](media/performance-recommendations/admin-center-all-groups.png)](media/performance-recommendations/admin-center-all-groups.png#lightbox)

Microsoft Entra groups are an important part of Intune because these groups are:

- The objects used for assigning apps, policies, and other workloads to users and devices
- Used to define the devices that admins can view and manage in the Intune admin center, like [scope groups](../role-based-access-control/overview#about-intune-role-assignments) in role-based access control (RBAC)

### Virtual groups

The **All users** and **All devices** assignments are Intune "virtual" groups. These virtual groups are available by default in all Intune tenants and don't come with any management overhead. For example, you don't need to create or adjust any Microsoft Entra ID rules to keep their members populated.

The **All users** and **All devices** groups are also highly scalable and optimized, mainly because they don't need to be synced from Microsoft Entra ID in the same way that other groups do.

### Assignment filters

After the app or policy is assigned to a Microsoft Entra ID or virtual group, you can use [assignment filters](overview) to narrow the assignment scope of these apps and policies to specific user or device groups.

Your assignment filter filters devices in (or out) of that assignment based on device properties.

[![Screenshot of the Intune admin center, the Microsoft Entra groups, virtual groups, and some filter properties in Microsoft Intune.](media/performance-recommendations/filters-azuread-virtual-groups.png)](media/performance-recommendations/filters-azuread-virtual-groups.png#lightbox)

Filtering is high performance, low latency applicability evaluation at device check-in without any need to precompute group membership.

## Performance recommendations

This section includes some recommendations that can improve performance when assigning your policies in Microsoft Intune.

These recommendations focus on improving performance and reducing latency in workload assignment. They have the most impact when working in large Intune environments, like environments with &gt;100,000 devices. These recommendations should be considered with other design aspects, like manageability, ease of use, role-based administration, and simplicity.

### Use the built-in virtual groups

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Use the **All users** and **All devices** virtual groups instead of creating your own version of all users/all devices using Microsoft Entra dynamic groups. | ![](../../media/icons/16/error.svg) Don't create your own "All users" or "All devices" dynamic groups for policy and app targeting in Intune. |

Larger groups take longer to sync membership updates between Microsoft Entra ID and Intune. The **All users** and **All devices** are usually the largest groups you have. If you assign Intune workloads to large Microsoft Entra groups that have many users or devices, then synchronization backlogs can happen in your Intune environment. This backlog impacts policy and app deployments, which take longer to reach managed devices.

The update from Microsoft Entra to Intune typically happens within 5 minutes. It's not instant. This time can affect enrollment assignments. Admins should enroll devices after several minutes, not immediately after adding the enrolling users to a group.

The built-in **All users** and **All devices** groups are Intune-only grouping objects that don't exist in Microsoft Entra ID. There isn't a continuous sync between Microsoft Entra ID and Intune. So, group membership is instant.

Note

For information on Intune check-in policy refresh intervals, go to [Intune Policy refresh intervals](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

You can also apply this optimization to other large and frequently changing groups you might have, like "All windows devices" or "all iOS devices". Instead of creating and targeting these groups, use the existing "All users" or "All devices" virtual groups, since Intune policies and applications are automatically scoped by platform.

When using very large groups in Intune (over 100,000 members), expect some initial delay in targeting. There's a first time setup process that happens between Microsoft Entra ID and Intune. The first full sync always takes longer than subsequent incremental syncs.

### Reuse groups

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Reuse the same group objects for assigning multiple policies. | ![](../../media/icons/16/error.svg) Don't create duplicate copies of the same group to target different policies. ![](../../media/icons/16/error.svg) Don't create dedicated "App groups" or "Policy groups". |

Behind the scenes, Intune converts Microsoft Entra group members to assignment targeting messages for each user and device. This process is highly optimized when the group objects are the same.

For example, Intune grouping and targeting works best when the "Engineering" user group is targeted with 10 policies. It doesn't work best when the Engineering users are members of 10 different groups, with each group assigned to a different policy.

We've seen a few designs not using this guidance. For example, IT admins create an "Install\_Edge" group, create a "Deploy\_Edge\_Config\_Policy" group, and then put the same devices in each group, which isn't recommended for performance.

A similar and not recommended pattern is creating "App groups". An app group is when each app has several Microsoft Entra groups created for it. For example, to manage the Microsoft Edge application, an admin creates the following groups:

- Edge\_Required
- Edge\_Available
- Edge\_Uninstall

The admin adds individual user or devices into these groups. These app groups dramatically increase the number of Microsoft Entra groups that Intune must subscribe to and monitor for membership updates, which is less efficient. Inefficient group sync design impacts how fast new assignments are created and delivered to devices.

### Make incremental group changes

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Be careful with large group nesting changes in Microsoft Entra ID. | ![](../../media/icons/16/error.svg) Don't make large group nesting changes all at once. |

A large group membership change in Microsoft Entra ID can generate bursts of targeting changes in Intune. These bursts can delay targeting of other assignments in your environment.

If a set of admins manage your groups and another set manages Microsoft Entra ID, then you should communicate the impact Microsoft Entra ID changes can have on Intune targeting.

For example, if a Microsoft Entra admin nests new large groups within an existing group that Intune uses for targeting, then Intune begins syncing all groups and group memberships. The time it takes to process all memberships depends on the number and size of group changes made in Microsoft Entra ID.

This recommendation also applies when groups are "unnested". For more information on nested groups, go to [Manage Microsoft Entra groups and group membership](/en-us/azure/active-directory/fundamentals/how-to-manage-groups).

### Use assignment filters to include and exclude

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Use assignment filters to achieve the correct user+device combination for targeting. | ![](../../media/icons/16/error.svg) Don't mix user groups and device groups when using Include and Exclude groups. |

This recommendation is also a support statement. We don't recommend or support creating assignments to user groups and excluding a device group from that assignment, or vice-versa.

This recommendation exists due to the timing/latency characteristic of dynamic groups. **Excluded groups** membership isn't instant, which can result in cases where devices incorrectly receive app or policy assignments. To understand more, go to [Assign policies and profiles - support matrix](../../device-configuration/assign-device-profile#support-matrix).

Instead of mixed exclusions, we recommend assigning to a user group. Then, use assignment filters to dynamically include or exclude the appropriate devices.

### Use assignment filters instead of dynamic groups for device property targeting

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Use filters for simple device properties (OS type, manufacturer, model, ownership, device category). | ![](../../media/icons/16/error.svg) Don't use dynamic groups for simple device properties when the group is only used by Intune. |

Dynamic device groups that use simple property rules (like `device.deviceOSType -eq "Windows"` or `device.deviceOwnership -eq "Company"`) introduce additional processing steps without benefit when the group is only consumed by Intune. Assignment filters evaluate the same properties at device check-in — directly, without requiring group membership evaluation.

For example, instead of creating a dynamic group with the rule `device.deviceOSType -eq "Windows"` and assigning a policy to that group, you can assign the policy to *All devices* and apply a filter with the rule `operatingSystemSKU -eq "Windows"`. The result is the same — but the filter is evaluated at check-in without depending on group membership processing.

Consider migrating dynamic device groups to assignment filters when:

- The group is **only used for Intune policy or app assignments** (not Conditional Access, licensing, or other services).
- The group rule uses device properties that assignment filters [support](ref-device-properties), like OS version, manufacturer, model, ownership, or category.
- You want to **simplify your targeting architecture** and reduce dependencies on group membership evaluation.

Note

Dynamic groups remain necessary for Autopilot profile targeting, cross-workload scenarios (Conditional Access, licensing), and user-based grouping. For guidance on dynamic groups, go to [Create simpler, more efficient rules for dynamic groups in Microsoft Entra ID](/en-us/azure/active-directory/enterprise-users/groups-dynamic-rule-more-efficient).

### Avoid `memberOf` in dynamic group rules

| DO | DON'T |
| --- | --- |
| ![](../../media/icons/16/check.svg) Use direct property comparisons (`-eq`, `-startsWith`, `-in`) in dynamic group rules. | ![](../../media/icons/16/error.svg) Don't use the `memberOf` operator in dynamic group rules for Intune targeting. |

The `memberOf` operator triggers transitive group membership lookups, which adds significant processing complexity. In large environments, `memberOf`-based rules can cause long evaluation times and produce unexpected membership results due to the recursive nature of the lookup.

If you need to target devices based on their membership in another group, evaluate whether the scenario can be redesigned using a direct device property or an assignment filter. For example, instead of `device.memberOf -any (group.objectId -in ['<groupId>'])`, consider whether the devices share a common attribute (like enrollment profile name, device category, or manufacturer) that can be used in a simpler rule or filter.

Note

For more information on optimizing rules for dynamic groups, see [Optimize rule efficiency](/en-us/entra/identity/users/manage-dynamic-group#optimize-rule-efficiency).

## Summary

When creating and managing assignments in Intune, incorporate some of these recommendations. Use groups or virtual groups, and apply assignment filters to help refine the targeting scope. Keep the best practices in mind:

- Don't create your own version of "All users" or "All devices" groups. Use the Intune virtual groups, as they don't require Microsoft Entra ID syncing when a new user or device is added to the environment.
- To optimize your targeting, reuse groups as much as possible.
- Take care when making large nesting changes to Intune groups. Intune needs to process all these changes and calculate effective changes for all the members of all the groups impacted by that change.
- Intune doesn't support mixed group exclusions. So, use assignment filters to dynamically include and exclude devices in addition to group or virtual group assignments.
- Use assignment filters instead of dynamic device groups when the group is only consumed by Intune.
- Avoid `memberOf` in dynamic group rules. Use direct property comparisons instead.

For guidance on choosing between targeting methods (virtual groups, static groups, dynamic groups, assignment filters, and enrollment time grouping), go to [Choose the right targeting method in Microsoft Intune](../choose-targeting-method).