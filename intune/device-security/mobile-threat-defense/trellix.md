---
layout: Conceptual
title: Trellix Mobile Security connector with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trellix
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
description: How to set up Trellix Mobile Security with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-23T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 90c51b34-4c92-584f-3b46-fe29b90b9cf7
document_version_independent_id: 90c51b34-4c92-584f-3b46-fe29b90b9cf7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/trellix.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/trellix
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/trellix.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 88a19166-cc33-7c6c-5287-96df1cd1c4e8
---

# Trellix Mobile Security connector with Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on a risk assessment that's conducted by Trellix Mobile Security. Trellix Mobile Security is a Mobile Threat Defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the Trellix Mobile Security app.

You can configure Conditional Access policies that are based on Trellix Mobile Security risk assessment. These policies are enabled through Intune device compliance policies for enrolled devices, which you can use to allow or block noncompliant devices to access corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## Supported platforms

- **Android 6.0 and later**
- **iOS 11.0 and later**

## Prerequisites

- Microsoft Entra ID P1 or P2
- Microsoft Intune Plan 1 subscription
- Trellix Mobile Security subscription

For more information, see the documentation for Trellix Mobile Security.

## How do Intune and Trellix Mobile Security help protect your company resources?

The Trellix Mobile Security app for Android and iOS/iPadOS captures file system, network stack, device, and application telemetry where available. Trellis then sends the telemetry data to the Trellix Mobile Security cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for Mobile Threat Defense (MTD), which can use risk assessment information from Trellix Mobile Security. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources like Exchange Online and SharePoint Online. Users also receive guidance from the Trellix Mobile Security app installed in their devices to resolve the issue and regain access to corporate resources. To support using Trellix Mobile Security with enrolled devices:

    - [Add MTD apps to devices](assign-apps)
    - [Create a device compliance policy that supports MTD](create-compliance-policy)
    - [Enable the MTD connector in Intune](enable-connector)
- **Support for unenrolled devices** - Intune can use the risk assessment data from the Trellix Mobile Security app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a Microsoft Intune protected app, Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Trellix Mobile Security with unenrolled devices:

    - [Add the MTD app to unenrolled devices](add-apps-unenrolled-devices)
    - [Create a Mobile Threat Defense app protection policy](create-app-protection-policy)
    - [Enable the MTD connector in Intune for unenrolled devices](enable-unenrolled-devices)

## Sample scenarios

See below a few scenarios when integrating Trellix Mobile Security with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/trellix/trellix-malicious-apps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/trellix/trellix-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/trellix/trellix-network-wifi-blocked.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated.](media/trellix/trellix-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/trellix/trellix-network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/trellix/trellix-network-spo-unblocked.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Trellix Mobile Security mobile threat defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](media/trellix/trellix-mobile-app-policy-block.png)

Access is granted on remediation:

![ Product flow for App protection policies to grant access after malware is remediated.](media/trellix/trellix-mobile-app-policy-remediated.png)