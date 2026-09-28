---
layout: Conceptual
title: Manage Windows Driver Updates - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-driver-updates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to manage Windows driver updates using Intune driver update policies to keep Windows devices current and stable.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davguy; davidmeb; bryanke
locale: en-us
document_id: 1120ccbf-5371-1fe7-f4df-90331abb6cf1
document_version_independent_id: 1120ccbf-5371-1fe7-f4df-90331abb6cf1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/manage-driver-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/manage-driver-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/manage-driver-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fa542627-7f9d-64c3-bcf4-34795eba140f
---

# Manage Windows Driver Updates - Microsoft Intune | Microsoft Learn

Windows driver updates provide updated device drivers and firmware that help ensure hardware compatibility, stability, and performance. These updates are released by device manufacturers and can include fixes for reliability issues, security vulnerabilities, and support for new hardware capabilities. Because driver updates can vary by device model and hardware configuration, organizations often prefer a more controlled approval process.

In Microsoft Intune, Windows driver updates are managed through **driver update policies**, which provide a dedicated policy surface for reviewing, approving, and deploying driver updates to managed devices. This policy is built on cloud‑based update orchestration and works alongside other Windows update policies, such as feature updates and quality updates. Driver update policies can be used independently or as part of Windows Autopatch. Client‑side install behavior—such as restarts and user notifications—continues to be governed by standard Windows Update policy settings.

Driver update policies support **automatic or manual approval workflows**, allowing you to choose whether recommended drivers are deployed automatically or require administrator review before installation. This approach helps organizations balance hardware stability, risk management, and operational efficiency while maintaining visibility into which drivers are approved for deployment.

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

## Architecture

The following diagram illustrates the high‑level architecture for managing Windows driver updates by using Microsoft Intune and Windows Autopatch.

[![A conceptual diagram of Windows driver update management.](media/manage-driver-updates/update-management-architecture.png)](media/manage-driver-updates/update-management-architecture.png#lightbox)

1. **Microsoft Intune** provides device identity, assignment, and driver update approval information. Intune sends policy settings, approved drivers, and pause commands to Windows Autopatch.
2. **Windows Autopatch** uses this information to configure Windows Update behavior for managed devices and to coordinate driver update deployment.
3. **Windows Update** evaluates device and hardware information to determine which driver updates are applicable, and installs only approved updates during regular update scans.
4. **Reporting data** collected during update operations is sent through Windows Autopatch and surfaced in Intune reporting.

This architecture allows administrators to approve and control driver updates centrally in Intune while relying on Windows Update and Autopatch to determine applicability and handle installation.