---
layout: Conceptual
title: Better Mobile Threat Defense with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/better-mobile
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
description: How to set up the Better Mobile Threat Defense with Microsoft Intune to control mobile device access to your corporate resources
ms.date: 2025-06-02T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: edf80b72-1393-9f0d-4eca-fa69c15007a5
document_version_independent_id: edf80b72-1393-9f0d-4eca-fa69c15007a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/better-mobile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/better-mobile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/better-mobile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 554c152c-8fa6-39a5-7577-6446ac886138
---

# Better Mobile Threat Defense with Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Better Mobile, a Mobile Threat Defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Better Mobile app.

You can configure Conditional Access policies based on Better Mobile risk assessment enabled through Intune device compliance policies for enrolled devices, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## How do Intune and Better Mobile help protect your company resources?

The Better Mobile app is installed and run on mobile devices. This app captures file system, network stack, device, and application telemetry where available, and then sends the data to the Better Mobile cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for Mobile Threat Defense (MTD), which can use risk assessment information from Better Mobile. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Better Mobile app installed in their devices to resolve the issue and regain access to corporate resources. To support using Better Mobile with enrolled devices:

    - [Add MTD apps to devices](assign-apps)
    - [Create a device compliance policy that supports MTD](create-compliance-policy)
    - [Enable the MTD connector in Intune](enable-connector)
- **Support for unenrolled devices** - Intune can use the risk assessment data from the Better Mobile app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a [Microsoft Intune protected app](../../app-management/ref-protected-apps), Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Better Mobile with unenrolled devices:

    - [Add the MTD app to unenrolled devices](add-apps-unenrolled-devices)
    - [Create a Mobile Threat Defense app protection policy](create-app-protection-policy)
    - [Enable the MTD connector in Intune for unenrolled devices](enable-unenrolled-devices)

## Supported platforms

- **Android 4.2.2 and later**
- **iOS 8.0 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Better Mobile Threat Defense subscription

    For more information, see the [Better Mobile website](https://better.mobi/).

## Sample scenarios

Here are some common scenarios.

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices from the following actions until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

Block when malicious apps are detected:

![Product flow for blocking access due to malicious apps.](media/better-mobile/better-mobile-maliciousapps-blocked.png)

Access is granted on remediation:

![Product flow for granting access when malicious apps are remediated.](media/better-mobile/better-mobile-maliciousapps-unblocked.png)

### Control access based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and protect access to Wi-Fi networks based on the device risk.

Block network access through Wi-Fi:

![Product flow for blocking access through Wi-Fi due to an alert.](media/better-mobile/better-mobile-network-wifi-blocked.png)

Access is granted on remediation:

![ Product flow for granting access through Wi-Fi after the alert is remediated.](media/better-mobile/better-mobile-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats to your network like **Man-in-the-middle** attacks, and prevent synchronization of corporate files based on the device risk.

Block SharePoint Online when network threats are detected:

![Product flow for blocking access to the organizations files due to an alert.](media/better-mobile/better-mobile-network-spo-blocked.png)

Access granted on remediation:

![Product flow for granting access to the organizations files after the alert is remediated.](media/better-mobile/better-mobile-network-spo-unblocked.png)

### Control access on unenrolled devices based on threats from malicious apps

When the BETTER Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](media/better-mobile/better-mobile-app-policy-block.png)

Access is granted on remediation:

![ Product flow for App protection policies to grant access after malware is remediated.](media/better-mobile/better-mobile-app-policy-remediated.png)