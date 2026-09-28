---
layout: Conceptual
title: Microsoft Intune Licensing Plans and Options - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/licensing
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection: M365-identity-device-management
ms.subservice: fundamentals
description: Microsoft Intune licensing options, plans, and the capabilities included with each Intune plan and Microsoft 365 license tier.
ms.date: 2026-05-13T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 35e4d27e-e2c0-75c1-1d85-fc84a2fd7968
document_version_independent_id: 35e4d27e-e2c0-75c1-1d85-fc84a2fd7968
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/licensing.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/licensing
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/licensing.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 2d9666c3-647c-7f12-f904-787714776bc5
---

# Microsoft Intune Licensing Plans and Options - Microsoft Intune | Microsoft Learn

Microsoft Intune is licensed through three plans and is included in several Microsoft 365 bundles. This article describes the plans, license requirements for users and administrators, and how to confirm your licenses.

## Microsoft Intune plans

Intune capabilities are organized into three plans. The Intune documentation and the Microsoft Intune admin center use these names to indicate which capabilities require which plan:

- **Microsoft Intune Plan 1**: the base service. Cloud-based unified endpoint management for devices and apps.
- **Microsoft Intune Plan 2**: additive to Plan 1. Advanced endpoint management capabilities, including Remote Help and Advanced Analytics.
- **Microsoft Intune Suite**: additive to Plan 1. Unifies advanced endpoint management and security capabilities. Includes Plan 2.

Most organizations get Intune as part of a Microsoft 365 bundle (such as Microsoft 365 E3, E5, or E7) rather than buying these plans directly. For what each bundle includes, current pricing, and how to buy, see:

- [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing)
- [Licensing options available with Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans)

Administrators don't always need an Intune license. For more information, see Unlicensed admin access.

## License requirements

An Intune license is required for any user or device that benefits directly or indirectly from the Microsoft Intune service, including access through a [Microsoft API](/en-us/legal/microsoft-apis/terms-of-use). Intune is included only with the licenses listed on the [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) page.

## Microsoft Intune for Education

Intune Plan 1 for Education is included in the following licenses:

- Microsoft 365 Education A5
- Microsoft 365 Education A3

For licensing information about Intune for Education, see [Microsoft 365 Education](/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-education).

## Device-only licenses

Intune offers a *device-only subscription* for managing devices that aren't affiliated with specific users, such as kiosks, dedicated devices, phone-room devices, IoT, and other single-use devices.

Assign device licenses based on your estimated usage. Device licenses apply when a device is enrolled through any of the following methods:

- [Windows Autopilot Self-Deploying mode](/en-us/autopilot/self-deploying)
- [Apple Device Enrollment Program without user affinity](../device-enrollment/apple/setup-automated-ios)
- [Apple School Manager without user affinity](../device-enrollment/apple/school-manager)
- [Apple Configurator without user affinity](../device-enrollment/apple/setup-configurator-ios)
- [Android Enterprise dedicated](../device-enrollment/android/setup-dedicated)
- [Using a device enrollment manager account](../device-enrollment/setup-enrollment-manager)

### Device-only management scenarios

- Devices managed through a Microsoft Intune device-only subscription support device-targeted management scenarios for eligible enrollment methods, including shared-device and no-user-affinity scenarios.
- A signed-in user without an Intune user license doesn't prevent device-targeted policies, applications, or management actions from being processed on a device managed through a device-only subscription.

### Device-only license limitations

When a device is enrolled by using a device license, the following Intune functions aren't supported:

- [Intune app protection policies](../app-management/protection/overview)
- [Conditional Access](../device-security/conditional-access-integration/overview)
- User-based management features, such as email and calendaring

## Unlicensed admin access

Administrators can sign in to and manage Microsoft Intune without an assigned Intune license. This access is enabled by default for tenants created after July 2021 and applies to all administrator roles, including Intune administrators and Microsoft Entra administrators. Tenants created before July 2021 can enable this option manually.

Unlicensed admin access grants sign-in and management access to the Microsoft Intune admin center. It doesn't replace license requirements for other features and services. For example, features that depend on Microsoft Entra ID P1 or P2 still require the appropriate license.

Whether you need to enable this setting depends on when your tenant was created:

- **Tenants created after July 2021**: Unlicensed administrator access is supported by default. No action is required.
- **Tenants created before July 2021**: Administrators require an Intune license unless the **Allow access to unlicensed admins** setting is enabled. This setting can't be undone after it's turned on.

Important

- Intune supports up to 1000 unlicensed admins per security group. If more than 1000 administrators are needed for a role assignment, use multiple security groups.
- Members of nested security groups aren't included in unlicensed admins access. If you keep nested security groups, admins in those nested groups still require an Intune license even when the unlicensed admins access is enabled.
- It can take up to 48 hours for access changes to take effect.

### Enable unlicensed admin access for pre-July 2021 tenants

Tenants created after July 2021 already have unlicensed admin access enabled by default. The following steps apply only to tenants created before July 2021.

To enable this setting, use an account assigned the [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) Microsoft Entra role. Because this role is privileged, use it only when necessary.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Roles** &gt; **Administrator Licensing**.
2. Select **Allow access to unlicensed admins**.
3. Select **Yes** to allow access to unlicensed admins.

After you enable this setting, users who sign in to the Microsoft Intune admin center don't require an Intune license. Roles assigned to users define their scope of access.

## Co-management with Configuration Manager

Most licenses that include Microsoft Intune also grant the rights to use Microsoft Configuration Manager, as long as the subscription remains active.

To enroll existing Configuration Manager-managed devices into Intune at scale without user interaction, co-management uses a Microsoft Entra feature called auto-enrollment. This scenario requires:

- **Microsoft Entra ID P1 or P2** assigned to each user.
- **Microsoft Intune Plan 1**: included automatically with Microsoft Intune. You no longer need to assign individual Intune licenses for this scenario.

You still need to assign Intune licenses for other enrollment scenarios.

## Confirm your licenses

A Microsoft Intune license is created for you when you sign up for the Intune free trial. As part of this trial, you also get a trial Enterprise Mobility + Security (EMS) subscription, which includes both Microsoft Entra ID P1 or P2 and Microsoft Intune.

Note

If you don't have an Intune license, sign up for the [Intune free trial](free-trial-sign-up).

To confirm your Microsoft Intune license or trial:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Tenant status**. Under the **Tenant details** tab, you can see the **MDM authority**, the **Total licensed users**, and the **Total Intune licenses**.
3. Select **Tenant administration** &gt; **Roles** &gt; **My permissions**.
4. Confirm that you're an **administrator** with **full** permissions to **all** Intune resources.

To confirm your Microsoft Entra ID P1 or P2 license:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **Microsoft Entra ID**.
3. Select **Overview**. On the **Overview** pane, select the **Overview** tab if it isn't already selected.
4. Under **Basic information**, view your license.

If you don't have a license for Microsoft Entra ID P1 or P2, see [Sign up for Microsoft Entra ID P1 or P2 editions](/en-us/azure/active-directory/fundamentals/active-directory-get-started-premium).