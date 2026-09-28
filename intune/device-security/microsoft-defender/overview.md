---
layout: Conceptual
title: Integrate Microsoft Defender for Endpoint with Intune for Device Compliance - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: laarrizz
ms.subservice: protect
description: Integrate Microsoft Defender for Endpoint with Microsoft Intune as a Mobile Threat Defense (MTD) solution to enforce device compliance and prevent security breaches.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: article
ai-usage: ai-assisted
locale: en-us
document_id: 8c8d583a-82c8-364a-1169-fd7b79de092b
document_version_independent_id: 8c8d583a-82c8-364a-1169-fd7b79de092b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-defender/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-defender/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-defender/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b8167bbe-01a9-e96a-63e8-78471532001b
---

# Integrate Microsoft Defender for Endpoint with Intune for Device Compliance - Microsoft Intune | Microsoft Learn

Integrating Microsoft Defender for Endpoint with Microsoft Intune lets you assess device risk in real time and block compromised devices from corporate resources by automatically marking them as noncompliant.

For example, if malware compromises a user's device, Microsoft Defender for Endpoint flags that device as high-risk and Intune can automatically cut off its access to corporate resources.

This article explains how the integration works, what capabilities it enables for device compliance, and when to use each option. For step-by-step configuration, see [Configure Microsoft Defender for Endpoint in Intune](configure-integration).

## Integration workflow

At a high level, the integration for devices enrolled with Intune works as follows. For detailed instructions, see [Configure Microsoft Defender for Endpoint in Intune](configure-integration):

1. [Establish a service-to-service connection](configure-integration#connect-defender-for-endpoint-to-intune) between Intune and Microsoft Defender for Endpoint.
2. [Onboard devices](configure-integration#onboard-devices) with Microsoft Defender for Endpoint using Intune policy.
3. [Create a device compliance policy](configure-integration#create-and-assign-compliance-policy-to-set-device-risk-level) to set acceptable risk levels.
4. [Configure Conditional Access policy](configure-integration#create-a-conditional-access-policy) to block noncompliant devices.

**Extend the integration:** Once configured, you can [use Microsoft Defender Vulnerability Management](remediate-vulnerabilities) to remediate endpoint weaknesses identified by Defender.

## Additional integration options

The following options extend the integration beyond traditional device compliance and may be useful in mixed enrollment or unenrolled environments.

**App protection policies**: You can use [app protection policies](configure-integration#create-and-assign-app-protection-policy-to-set-device-risk-level) to set device risk levels for both enrolled and unenrolled devices. This provides app-level protection based on Defender threat assessments.

**Unenrolled devices**: For devices that aren't or can't enroll in Intune, use Intune's [security management for Microsoft Defender for Endpoint](security-settings-management) to manage Defender settings via endpoint security policies without requiring full device enrollment.

## Prerequisites

### Role-based access control

To configure this integration end-to-end, you need permissions to manage the Intune–Defender connection, device onboarding, and compliance policies. Specifically, your Intune role-based access control (RBAC) role must include:

- **Mobile Threat Defense**: *Modify* and *Read* – Required to establish the service-to-service connection between Intune and Defender.
- **Endpoint Detection and Response**: *Assign*, *Create*, *Read*, and *Update* – Required to onboard devices using Intune EDR policy.
- **Device compliance policies**: *Assign*, *Create*, *Read*, and *Update* – Required to configure risk-level compliance policies.

You can add these permissions to a [custom Intune role](../../fundamentals/role-based-access-control/create-custom-role), or use the built-in **Endpoint Security Manager** role, which is the least-privileged built-in Intune role that includes all required permissions. For details, see [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

Note

Conditional Access policies are configured in Microsoft Entra ID and require a separate Entra ID role, such as [Conditional Access Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).

### Intune requirements

**Subscription**: Microsoft Intune Plan 1 subscription provides access to Intune and the Microsoft Intune admin center.

For licensing options, see [Microsoft Intune licensing](../../fundamentals/licensing).

**Supported platforms**:

| Platform | Requirements |
| --- | --- |
| Android | Intune-managed devices |
| iOS/iPadOS | Intune-managed devices |
| Windows | Microsoft Entra ID hybrid joined or Microsoft Entra ID joined |

### Microsoft Defender for Endpoint requirements

**Subscription**: Microsoft Defender for Endpoint subscription provides access to the [Microsoft Defender XDR portal](https://go.microsoft.com/fwlink/p/?linkid=2077139).

For licensing and system requirements, see [Minimum requirements for Microsoft Defender for Endpoint](/en-us/defender-endpoint/minimum-requirements).

## Example: Automatic threat containment

The following example shows how the integration automatically contains a threat, assuming it's already configured:

1. **Detection**: Microsoft Defender for Endpoint detects threat activity on a device and classifies it as high-risk.
2. **Compliance enforcement**: Intune receives the risk signal and automatically marks the device as noncompliant based on your compliance policy thresholds.
3. **Access blocking**: Conditional Access policies immediately block the noncompliant device from accessing corporate resources.
4. **Containment**: The threat is contained while your security team investigates and remediates in the Microsoft Defender XDR portal.

## Platform-specific capabilities

Different platforms offer unique configuration options when integrating with Microsoft Defender for Endpoint:

**Android**: Deploy Defender for Endpoint to Android devices through Managed Google Play using Intune app deployment and app configuration policies. See [Deploy Microsoft Defender for Endpoint on Android](deploy-android) for the complete deployment guide. After deployment, use Intune device configuration policies to configure [Microsoft Defender for Endpoint web protection](configure-web-protection-android) settings, including the ability to enable or disable VPN-based scanning.

**iOS/iPadOS**: Enable [vulnerability assessment of apps](/en-us/defender-endpoint/ios-configure-features#configure-vulnerability-assessment-of-apps) to allow Defender to scan installed apps for known vulnerabilities.

**Windows**: Benefit from automatic onboarding capabilities and use [Microsoft Defender for Endpoint security baselines](../security-baselines/overview) for comprehensive, prescriptive security configurations.