---
layout: Conceptual
title: Trustd Mobile Threat Defense with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trustd-mobile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: Set up Trustd Mobile Threat Defense with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2026-06-24T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 6a5124ab-67f5-b01b-c40b-90bc3d91b55e
document_version_independent_id: 6a5124ab-67f5-b01b-c40b-90bc3d91b55e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/trustd-mobile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/trustd-mobile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/trustd-mobile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 0bd9b913-87ad-8303-093b-902814d9532f
---

# Trustd Mobile Threat Defense with Microsoft Intune - Microsoft Intune | Microsoft Learn

You can use Trustd Mobile as a Mobile Threat Defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Trustd Mobile app.

You can configure Conditional Access policies based on the Trustd Mobile risk assessment, enabled through Intune device compliance policies. These policies can allow or block noncompliant devices from accessing corporate resources based on detected threats.

## Prerequisites

Before setting up the Trustd Mobile connector, ensure you have the following subscriptions:

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Trustd Mobile subscription. See [Trustd Mobile](https://securitystore.microsoft.com/solutions/tracedltd1617114857192.trustd_mtd) in the Microsoft Security marketplace.

## Supported platforms

The Trustd Mobile connector supports the following device platforms:

- **Android 9.0 and later**
- **iOS/iPadOS 15.0 and later**

Devices must run the Trustd Mobile app:

- [Apple App Store](https://apps.apple.com/app/trustd-mobile-security/id1519403888)
- [Google Play](https://play.google.com/store/apps/details?id=app.traced)

## Integrate Trustd Mobile with Intune to help protect your company resources

Trustd Mobile integrates with Microsoft Intune to ensure corporate resources are accessed only by secure and compliant mobile devices. The Trustd Mobile app collects real-time telemetry to detect threats including operating system exploits, malicious applications, and network-level risks.

Trustd Mobile reports a risk score to Intune using the Intune Mobile Threat Defense connector. This score updates device compliance status. When a threat is detected, the device is marked noncompliant, and your Conditional Access policies block access to sensitive resources. The Trustd Mobile app guides users to remediate threats to restore compliance and access.

For step-by-step guidance on setting up and integrating Trustd Mobile with Intune, see [Integrate Trustd Mobile with Microsoft Intune](setup-trustd-mobile).

## Common scenarios

Here are some common scenarios:

### Control access based on threats from malicious applications

When an application behaves in a malicious way, such as stealing credentials or accessing sensitive APIs, you can block device access until the threat is resolved.

Block when malicious apps are detected:

![Product flow for blocking access due to malicious apps.](media/trustd-mobile/trustd-mobile-malicious-apps-blocked.png)

Access is granted on remediation:

![Product flow for granting access when malicious apps are remediated.](media/trustd-mobile/trustd-mobile-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and protect access to Wi-Fi networks based on the device risk.

Block network access through Wi-Fi:

![Product flow for blocking access through Wi-Fi due to an alert.](media/trustd-mobile/trustd-mobile-network-wifi-blocked.png)

Access is granted on remediation:

![Product flow for granting access through Wi-Fi after the alert is remediated.](media/trustd-mobile/trustd-mobile-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and prevent synchronization of corporate files based on the device risk.

Block SharePoint Online when network threats are detected:

![Product flow for blocking access to the organization's files due to an alert.](media/trustd-mobile/trustd-mobile-network-spo-blocked.png)

Access granted on remediation:

![Product flow for granting access to the organization's files after the alert is remediated.](media/trustd-mobile/trustd-mobile-network-spo-unblocked.png)