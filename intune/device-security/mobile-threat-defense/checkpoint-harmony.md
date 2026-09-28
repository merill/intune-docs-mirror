---
layout: Conceptual
title: Check Point Harmony Mobile Mobile Threat Defense Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/checkpoint-harmony
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
description: How to set up Check Point Harmony Mobile Threat Defense with Microsoft Intune control mobile device access to your corporate resources.
ms.date: 2024-08-22T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 60465931-d1fe-2ea3-5db4-36c7f34c8cfc
document_version_independent_id: 60465931-d1fe-2ea3-5db4-36c7f34c8cfc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/checkpoint-harmony.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/checkpoint-harmony
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/checkpoint-harmony.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b1a16895-2c60-6fc2-23e1-9196ee116def
---

# Check Point Harmony Mobile Mobile Threat Defense Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Check Point Harmony Mobile, a mobile threat defense solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Harmony Mobile Protect app.

You can configure Conditional Access policies based on Check Point Harmony Mobile risk assessment enabled through Intune device compliance policies, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats.

## Supported platforms

- **Android 8 and later**
- **iOS 12 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Check Point Harmony Mobile Threat Defense subscription

    - See the [CheckPoint Harmony website](https://www.checkpoint.com/harmony).

## How do Intune and Check Point Harmony Mobile help protect your company resources?

Check Point Harmony Mobile app for Android and iOS/iPadOS captures file system, network stack, and device and application telemetry where available, then sends the telemetry data to the Check Point Harmony cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for Check Point Harmony Mobile Threat Defense, which is based on the Check Point Harmony risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Harmony Mobile Protect app installed in their devices to resolve the issue and regain access to corporate resources.

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/checkpoint-harmony/checkpoint-mtd-2.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/checkpoint-harmony/checkpoint-mtd-3.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/checkpoint-harmony/checkpoint-mtd-4.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated.](media/checkpoint-harmony/checkpoint-mtd-5.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/checkpoint-harmony/checkpoint-mtd-6.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/checkpoint-harmony/checkpoint-mtd-7.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Check Point Harmony Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](media/checkpoint-harmony/harmony-app-policy-block.png)

Access is granted on remediation:

![ Product flow for App protection policies to grant access after malware is remediated.](media/checkpoint-harmony/harmony-app-policy-remediated.png)