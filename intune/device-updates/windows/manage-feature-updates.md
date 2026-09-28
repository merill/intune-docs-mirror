---
layout: Conceptual
title: Manage Windows Feature Updates - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-feature-updates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to use Microsoft Intune policies to manage Windows feature updates.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davidmeb; bryanke; davguy
locale: en-us
document_id: 091f3d04-5676-a5a5-9d55-105608db84ac
document_version_independent_id: 091f3d04-5676-a5a5-9d55-105608db84ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/manage-feature-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/manage-feature-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/manage-feature-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b40952c-786c-399f-f597-bbbd9d7a2740
---

# Manage Windows Feature Updates - Microsoft Intune | Microsoft Learn

Windows feature updates are periodic releases that introduce new Windows capabilities, improvements, and changes to existing functionality. These updates typically ship once per year and represent a full operating system upgrade, such as moving a device from one Windows version to a newer release. Because feature updates can affect user experience, application compatibility, and device readiness, organizations often deploy them using controlled and phased rollouts.

In Microsoft Intune, Windows feature updates are managed through **feature update policies**, which provide a dedicated policy surface for controlling which Windows version devices are offered and when that version can install. This policy uses cloud‑based update orchestration and can be used alongside other Windows update policies, such as quality updates and driver updates. Depending on your deployment model, feature updates may be managed manually through Intune or automatically through Windows Autopatch. Client‑side update behavior—such as restart experience and installation timing—continues to be influenced by standard Windows Update policy settings, including [update rings](manage-update-rings) and [Windows Update client policies](/en-us/windows/deployment/update/waas-configure-wufb).

Feature update policies allow you to **lock devices to a specific Windows release** or **target an upgrade to a newer version** while preventing devices from moving beyond that version. This approach helps ensure version compliance, reduce unexpected upgrades, and coordinate OS updates with application readiness and organizational rollout plans.

## Prerequisites

![](../../media/icons/16/network-connectivity.svg)**Network and connectivity requirements**

> 
> Devices must have internet access and be able to reach required Microsoft endpoints:
> 
> - [Intune service endpoints](../../fundamentals/endpoints#access-for-managed-devices)
> - [Windows Update endpoints](/en-us/windows/privacy/manage-windows-1809-endpoints#windows-update)
> - [Windows Autopatch endpoints](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-configure-network)
> 

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> This feature is supported in the following cloud environments:
> 
> - Public cloud
> - Government Community Cloud (GCC)
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> To enable reporting for this feature, ensure your organization allows Intune to access Windows diagnostic data collected from enrolled devices.
> 
> For details, see [Enable use of Windows diagnostic data](../../privacy/enable-windows-diagnostic-data).

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> To use this feature, the following licenses are required:
> 
> - [Microsoft Intune Plan 1](../../fundamentals/licensing)
> - A Windows license that includes the [Autopatch entitlement](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites#licenses-and-entitlements).
> 

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following Windows editions:
> 
> - Pro
> - Pro Education
> - Enterprise
> - Education
> 
> 
> Note
> 
> Windows Enterprise LTSC (Long Term Service Channel) isn't supported. Use update ring policies instead.

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> This policy type supports devices that are:
> 
> - Managed by Intune
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 
> 
> Devices must also meet the following requirements:
> 
> - Telemetry must be turned on, with a minimum setting of [**Required**](../../device-configuration/templates/ref-device-restrictions-windows#reporting-and-telemetry).
> - The *Microsoft Account Sign-In Assistant* service (`wlidsvc`) must be enabled and running.
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To manage this feature, use an account with at least one of the following roles:
> 
> - [Policy and Profile manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)
> - [Custom role](../../fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The **Device configurations** permissions **Assign**,**Create**,**Delete**,**View Reports**,**Update**, and **Read**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 
> 
> To view the reports for this feature, use an account with at least one of the following roles:
> 
> - [Endpoint Security Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Read Only Operator](../../fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator)
> - [Help Desk Operator](../../fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Custom role](../../fundamentals/role-based-access-control/create-custom-role) with the **Managed devices**/**View Reports** permission.
> 

## Plan feature update deployments

When planning feature update deployments, consider how feature update policies interact with other Windows update settings and services in your tenant.

### Interaction with update rings

If a device is targeted by both a feature update policy and an update ring policy, review the update ring configuration to avoid unintended delays:

- Set **Feature update deferral period (days)** to **0** so deferrals in update rings don't delay feature updates controlled by the feature update policy. For more information, see [Move from update ring deferrals to feature update policies](configure-feature-update-policy#move-from-update-ring-deferrals-to-feature-update-policies).
- Ensure feature updates in the update ring aren't paused.
- Client‑side behaviors such as restart experience, deadlines, and active hours continue to be governed by update rings and Windows Update client settings.

### Deployment timing and enforcement

Feature update policies don't apply during Windows Autopilot out‑of‑box experience (OOBE). Instead, they take effect at the first Windows Update scan after provisioning is complete.

When devices check in with the Windows Update service, group membership is evaluated against the security groups assigned to feature update policies. Any configured holds are enforced during this evaluation.

Feature update policies also support scheduled and gradual deployments using rollout options. For details on configuring rollout timing, see [Rollout options for Windows Updates](configure-rollout-options).

### Working with Windows Autopatch

Feature update policies can be used on their own or as part of Windows Autopatch. In Autopatch‑managed environments, the service uses feature update policies to coordinate controlled and phased OS upgrades.

If a device managed by Autopatch is no longer targeted by a feature update policy, the device remains enrolled in Autopatch. This behavior helps prevent unintended upgrades while administrators adjust policy targeting or deployment plans.

As a result, when a feature update policy no longer applies to a device, that device isn't offered any feature update until one of the following happens:

- The device is assigned to a new feature update profile.
- The device is unenrolled from Intune, which unenrolls the device from feature update management by Autopatch.
- You use the [Windows Autopatch graph API](/en-us/graph/windowsupdates-enroll) to [remove the device](/en-us/graph/api/windowsupdates-updatableasset-unenrollassets) from feature update management.