---
layout: Conceptual
title: Use CrowdStrike Falcon for Mobile with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/crowdstrike-falcon
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
description: How to set up CrowdStrike Falcon Threat Defense with Microsoft Intune control mobile device access to your corporate resources.
ms.date: 2025-02-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: d917ee3f-6702-d24e-f770-69560dcaaa30
document_version_independent_id: d917ee3f-6702-d24e-f770-69560dcaaa30
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/crowdstrike-falcon.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/crowdstrike-falcon
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/crowdstrike-falcon.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 4e904c9d-2722-12e5-0e9e-0446c5699ba6
---

# Use CrowdStrike Falcon for Mobile with Microsoft Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by CrowdStrike Falcon for Mobile. CrowdStrike Falcon is a mobile threat defense solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the CrowdStrike Falcon app.

You can configure Conditional Access policies based on CrowdStrike Falcon for Mobile risk assessment enabled through Intune device compliance policies. These policies can allow or block noncompliant devices to access corporate resources based on detected threats.

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- CrowdStrike Falcon for Mobile subscription. See the [CrowdStrike Falcon for Mobile](https://www.crowdstrike.com/products/endpoint-security/falcon-for-mobile/) website.

## Supported platforms

- **Android 9.0 and later**
- **iOS 15.0 and later**

## How do Intune and CrowdStrike Falcon for Mobile help protect your company resources?

CrowdStrike Falcon app for Android and iOS/iPadOS captures available telemetry for the file system, network stack, device, and applications. The captured telemetry data is then sent to the CrowdStrike Falcon for Mobile cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for CrowdStrike Falcon for Mobile Threat Defense, which is based on the CrowdStrike Falcon for Mobile risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the CrowdStrike Falcon app installed in their devices to resolve the issue and regain access to corporate resources.

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/crowdstrike-falcon/crowdstrike-malicious-apps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/crowdstrike-falcon/crowdstrike-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/crowdstrike-falcon/crowdstrike-network-wifi-blocked.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated.](media/crowdstrike-falcon/crowdstrike-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/crowdstrike-falcon/crowdstrike-network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/crowdstrike-falcon/crowdstrike-network-spo-unblocked.png)