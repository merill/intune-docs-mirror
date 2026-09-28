---
layout: Conceptual
title: Lookout Mobile Endpoint with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/lookout
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
description: How to set up Lookout Mobile Threat Defense (MTD) How to set up to control mobile device access to your corporate resources.
ms.date: 2024-07-31T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b60df350-3673-ec2b-a7cc-e18a443937b7
document_version_independent_id: b60df350-3673-ec2b-a7cc-e18a443937b7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/lookout.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/lookout
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/lookout.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 044c0fa6-013b-6837-d963-65e7d07e94b7
---

# Lookout Mobile Endpoint with Microsoft Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources based on risk assessment conducted by Lookout, a Mobile Threat Defense solution integrated with Microsoft Intune. Risk is assessed based on telemetry collected from devices by the Lookout service including:

- Operating system vulnerabilities
- Malicious apps installed
- Malicious network profiles

You can configure Conditional Access policies based on Lookout's risk assessment enabled through Intune compliance policies for enrolled devices, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## How do Intune and Lookout Mobile Endpoint Security help protect company resources?

Lookout's mobile app, **Lookout for work**, is installed and run on mobile devices. This app captures file system, network stack, and device and application telemetry where available, then sends it to the Lookout cloud service to assess the device's risk for mobile threats. You can change risk level classifications for threats in the Lookout console to suit your requirements.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for Mobile Threat Defense (MTD), which can use risk assessment information from Lookout for work. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Lookout for work app installed in their devices to resolve the issue and regain access to corporate resources. To support using Lookout for work with enrolled devices:

    - [Add MTD apps to devices](assign-apps)
    - [Create a device compliance policy that supports MTD](create-compliance-policy)
    - [Enable the MTD connector in Intune](enable-connector)
- **Support for unenrolled devices** - Intune can use the risk assessment data from the Lookout for work app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a [Microsoft Intune protected app](../../app-management/ref-protected-apps), Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Lookout for work with unenrolled devices:

    - [Add the MTD app to unenrolled devices](add-apps-unenrolled-devices)
    - [Create a Mobile Threat Defense app protection policy](create-app-protection-policy)
    - [Enable the MTD connector in Intune for unenrolled devices](enable-unenrolled-devices)

## Supported platforms

The following platforms are supported for Lookout when enrolled in Intune:

- **Android 5.0 and later**
- **iOS 12 and later**

## Prerequisites

- Lookout Mobile Endpoint Security enterprise subscription
- Microsoft Intune Plan 1 subscription
- Microsoft Entra ID P1
- Enterprise Mobility and Security (EMS) E3 or E5, with licenses assigned to users.

For more information, see [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## Sample scenarios

Here are the common scenarios when using Mobile Endpoint Security with Intune.

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices from the following until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/lookout/malicious-apps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/lookout/malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats to your network such as man-in-the-middle attacks and protect access to WiFi networks based on the device risk.

*Block network access through WiFi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/lookout/network-wifi-blocked.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated.](media/lookout/network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats to your network such as Man-in-the-middle attacks, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/lookout/network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/lookout/network-spo-unblocked.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Lookout Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](media/lookout/lookout-app-policy-block.png)

Access is granted on remediation:

![ Product flow for App protection policies to grant access after malware is remediated.](media/lookout/lookout-app-policy-remediated.png)