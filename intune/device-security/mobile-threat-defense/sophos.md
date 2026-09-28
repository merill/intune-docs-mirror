---
layout: Conceptual
title: Use Sophos Mobile with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/sophos
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
description: How to use the Sophos Mobile solution with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7f27e097-a86f-cd12-d3e8-d3db491fbe4a
document_version_independent_id: 7f27e097-a86f-cd12-d3e8-d3db491fbe4a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/sophos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/sophos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/sophos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 8423d692-5ea8-b5d4-565e-96b1a738cbf1
---

# Use Sophos Mobile with Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Sophos Mobile, a Mobile Threat Defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Sophos Mobile app. You can configure Conditional Access policies based on Sophos Mobile risk assessment enabled through Intune device compliance policies, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Supported platforms

- Android 7.0 and later
- iOS 14.0 and later

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Sophos Mobile Threat Defense subscription

For more information, see the [Sophos website](https://www.sophos.com/products/mobile-control.aspx).

## How do Intune and Sophos Mobile help protect your company resources?

Sophos Mobile app for Android and iOS/iPadOS captures file system, network stack, device, and application telemetry where available, and then sends the telemetry data to the Sophos Mobile cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for Sophos Mobile Threat Defense, which is based on the Sophos Mobile risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Sophos Mobile app installed in their devices to resolve the issue and regain access to corporate resources.

## Sample scenarios

Here are some common scenarios.

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices from the following actions until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected*:

![Product flow for blocking access due to malicious apps.](media/sophos/sophos-malicious-apps-blocked.png)

*Access granted on remediation*:

![Product flow for granting access when malicious apps are remediated.](media/sophos/sophos-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats to your network like Man-in-the-middle attacks, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi*:

![Product flow for blocking access through Wi-Fi due to an alert.](media/sophos/sophos-network-wifi-blocked.png)

*Access granted on remediation*:

![ Product flow for granting access through Wi-Fi after the alert is remediated. ](media/sophos/sophos-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats to your network like Man-in-the-middle attacks, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected*:

![Product flow for blocking access to the organizations files due to an alert.](media/sophos/sophos-network-spo-blocked.png)

*Access granted on remediation*:

![Product flow for granting access to the organizations files after the alert is remediated.](media/sophos/sophos-network-spo-unblocked.png)