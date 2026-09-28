---
layout: Conceptual
title: Manage Windows quality updates - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-quality-updates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to manage Windows quality updates in Microsoft Intune using quality update policies, expedited updates, and hotpatch to keep devices secure and compliant.
ms.date: 2026-01-06T00:00:00.0000000Z
ms.reviewer: mobattul
ms.topic: how-to
locale: en-us
document_id: 9e5fce35-77ee-59bd-7183-11712616fcf6
document_version_independent_id: 9e5fce35-77ee-59bd-7183-11712616fcf6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/manage-quality-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/manage-quality-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/manage-quality-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7be3e648-7f89-c02d-a989-c707a6fe70ae
---

# Manage Windows quality updates - Microsoft Intune | Microsoft Learn

Windows quality updates are the regular Windows servicing updates that keep devices secure, reliable, and supported. These updates are released frequently—typically monthly—and include security fixes, non‑security improvements, and reliability enhancements. Because quality updates are cumulative, installing the latest update brings a device fully up to date for its currently installed Windows version.

In Microsoft Intune, you manage Windows quality updates through **quality update policies**. These policies provide a dedicated policy surface for targeting specific quality updates, and use cloud‑based update orchestration to deploy those updates to devices. Quality update policies work alongside other Windows update policies—such as **feature updates policies** and **driver updates policies**—and can be managed directly in Intune or automatically through **Windows Autopatch**, depending on your deployment model.

Quality update policies support targeted deployment scenarios for Windows quality updates. You can use them to **expedite updates** and accelerate the installation of critical or security updates when standard deployment timelines aren't acceptable. For eligible Windows editions and device configurations, you can also enable **hotpatch**, which installs certain security updates without requiring an immediate device restart—helping balance rapid protection, deployment control, and end‑user experience.

Client‑side update behavior—such as restart settings, deadlines, notifications, and deferral periods—continues to be configured through **update rings** and **Windows Update client policies**, which together with quality update policies complete the end‑to‑end update experience on devices.

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

## How quality update policies support different deployment scenarios

Quality update policies provide a single management surface for deploying Windows quality updates across different operational scenarios:

- **Standard deployment**: Use quality update policies to enable cloud‑based orchestration of regular monthly quality updates, while update rings and Windows Update client settings continue to control restarts, deadlines, and notifications.
- **Expedited deployment**: Use expedite policies to accelerate the installation of a specific security or critical update when faster remediation is required.
- **Restart‑optimized deployments**: On supported devices, enable hotpatch through quality update policies to apply qualifying security updates without requiring an immediate device restart.

These scenarios use cloud‑based update orchestration to control how updates are approved, timed, and applied, depending on the deployment model.

### Do I need a Windows quality update policy?

You don't need to create a Windows quality update policy for devices to continue receiving monthly Windows quality updates. Devices without a quality update policy continue to receive quality updates through standard Windows Update behavior, using update rings and Windows Update client policies to control deferrals, deadlines, restarts, and notifications.

Create a Windows quality update policy if you want to:

- Enable **cloud‑based orchestration** of Windows quality updates
- Use **Windows Autopatch-managed quality update deployments**
- Enable **hotpatch** for eligible devices
- View **policy‑based quality update reporting**

If you only need to **accelerate the installation of a specific quality update** for a limited set of devices, you can use an **expedite policy** without creating a quality update policy.

In most environments, you create a Windows quality update policy only when you need advanced deployment scenarios such as hotpatch or Windows Autopatch-managed update workflows.