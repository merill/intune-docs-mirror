---
layout: Conceptual
title: Scenarios for using Conditional Access with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/scenarios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- conditional-access
- sub-device-compliance
ms.reviewer: ilwu
ms.subservice: protect
description: Learn how Conditional Access is commonly used with Intune compliance policy for devices and apps
ms.date: 2025-03-19T00:00:00.0000000Z
ms.topic: article
locale: en-us
document_id: 5f0e130e-ebd3-d661-f26d-f310a88a97d2
document_version_independent_id: 5f0e130e-ebd3-d661-f26d-f310a88a97d2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/conditional-access-integration/scenarios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/conditional-access-integration/scenarios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/conditional-access-integration/scenarios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: d93af7e5-657a-1af2-40ec-cec5259f642c
---

# Scenarios for using Conditional Access with Microsoft Intune - Microsoft Intune | Microsoft Learn

There are two types of Conditional Access policies you can use with Intune: device-based and app-based. This article covers common scenarios for both types.

The information in this article can help you understand how to use both the Intune mobile device compliance capabilities and the Intune mobile application management (MAM) capabilities.

Note

Conditional Access is a Microsoft Entra capability that is included with a Microsoft Entra ID P1 or P2 license. The Conditional Access node accessed from the Microsoft Intune admin center is the same node as accessed from Microsoft Entra ID.

## Applications available in Conditional Access for controlling Microsoft Intune

When you configure Conditional Access in the Microsoft Entra admin center, you have two applications to choose from:

- **Microsoft Intune** - This application controls access to the Microsoft Intune admin center and data sources. Configure grants/controls on this application when you want to target the Microsoft Intune admin center and data sources.
- **Microsoft Intune Enrollment** - This application controls the enrollment workflow. Configure grants/controls on this application when you want to target the enrollment process. For more information, see [Require multifactor authentication for Intune device enrollments](../../device-enrollment/configure-multifactor-authentication).

## Device-based Conditional Access

Intune and Microsoft Entra ID work together to make sure only managed and compliant devices can access your organization's email, Microsoft 365 services, software as a service (SaaS) apps, and [on-premises apps](/en-us/entra/identity/app-proxy). Additionally, you can set a policy in Microsoft Entra ID to only enable domain-joined computers or mobile devices that are enrolled in Intune to access Microsoft 365 services.

With Intune, you deploy device compliance policies to determine if a device meets your expected configuration and security requirements. The compliance policy evaluation determines the device's compliance status, which is reported to both Intune and Microsoft Entra ID. It's in Microsoft Entra ID that Conditional Access policies can use a device's compliance status to make decisions on whether to allow or block access to your organization's resources from that device.

Device-based Conditional Access policies for Exchange online and other Microsoft 365 products are configured through the [Microsoft Intune admin center](../../fundamentals/what-is-intune).

- Learn more about [Require managed devices with Conditional Access in Microsoft Entra ID](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance).
- Learn more about [Intune device compliance](../compliance/overview).
- Learn more about [Supported browsers with Conditional Access in Microsoft Entra ID](/en-us/entra/identity/conditional-access/concept-conditional-access-conditions#supported-browsers).

The following scenarios build on device-based Conditional Access to show how it applies in specific contexts.

### Conditional Access based on network access control

Intune integrates with partners like Cisco ISE, Aruba Clear Pass, and Citrix NetScaler to provide access controls based on the Intune enrollment and the device compliance state.

Users can be allowed or denied access to corporate Wi-Fi or VPN resources based on whether the device they're using is managed and compliant with Intune device compliance policies.

- Learn more about the [NAC integration with Intune](../integrate-network-access-control).

### Conditional Access based on device risk

Intune partners with mobile threat defense vendors that provide a security solution to detect malware, Trojans, and other threats on mobile devices. When mobile devices have the mobile threat defense agent installed, the agent sends compliance state messages back to Intune reporting when a threat is found. This integration plays a factor in Conditional Access decisions based on device risk.

- Learn more about [Intune mobile threat defense](../mobile-threat-defense/overview).

### Conditional Access for Windows PCs

Conditional Access for PCs provides capabilities similar to those available for mobile devices. The following options are available when managing PCs with Intune.

#### Corporate-owned

- **Microsoft Entra hybrid joined:** This option is commonly used by organizations that are reasonably comfortable with how they're already managing their PCs through AD group policies or Configuration Manager.
- **Microsoft Entra domain joined and Intune management:** This scenario is for organizations that want to be cloud-first (that is, primarily use cloud services, with a goal to reduce use of an on-premises infrastructure) or cloud-only (no on-premises infrastructure). Microsoft Entra join works well in a hybrid environment, enabling access to both cloud and on-premises apps and resources. The device joins to the Microsoft Entra ID and gets enrolled to Intune, which can be used as a Conditional Access criteria when accessing corporate resources.

#### Bring your own device (BYOD)

- **Workplace join and Intune management:** Here the user can join their personal devices to access corporate resources and services. You can use Workplace join and enroll devices into Intune MDM to receive device-level policies, which are another option to evaluate Conditional Access criteria.

Learn more about [Device Management in Microsoft Entra ID](/en-us/entra/identity/devices/overview).

## App-based Conditional Access

App-based Conditional Access protects access at the app level rather than the device level, making it well-suited for unenrolled devices. The following articles cover app-based Conditional Access scenarios for Intune:

- [Use app-based Conditional Access policies with Intune](app-based-policies)
- [Require approved app or app protection policy (Microsoft Entra)](/en-us/entra/identity/conditional-access/policy-all-users-approved-app-or-app-protection)