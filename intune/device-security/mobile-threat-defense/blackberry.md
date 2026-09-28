---
layout: Conceptual
title: BlackBerry Protect Mobile MTD and Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/blackberry
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
description: How to set up CylancePROTECT Mobile (BlackBerry) with Microsoft Intune to control mobile device access to your corporate resources
ms.date: 2024-10-14T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c2220f0f-6c8f-29f9-8d43-f26044b1b50c
document_version_independent_id: c2220f0f-6c8f-29f9-8d43-f26044b1b50c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/blackberry.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/blackberry
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/blackberry.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2d475856-5760-5cdb-1fe0-92da3a319660
---

# BlackBerry Protect Mobile MTD and Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by BlackBerry Protect Mobile (powered by Cylance AI), a mobile threat defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running the BlackBerry Protect Mobile app.

You can configure Conditional Access policies based on a BlackBerry Protect risk assessment, enabled through Intune device compliance policies for enrolled devices. You can set up your policies to allow or block noncompliant devices from accessing corporate resources based on detected threats. For unenrolled devices, you can use app protection policies to enforce a block or selective wipe based on detected threats.

## Supported platforms

- **Android 9.0 and later**
- **iOS 13.0 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- BlackBerry UES account with access to UES management console

## How do Intune and the BlackBerry MTD connector help protect your company resources?

For Android and iOS/iPadOS, the CylancePROTECT app captures file system, network stack, device, and application telemetry where available, then sends the data to the Cylance AI Protection cloud service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for MTD, which can use risk assessment information from CylancePROTECT (BlackBerry). When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources, such as Exchange Online and SharePoint Online. Users also receive guidance from the BlackBerry Protect app installed on their devices to resolve the issue and regain access to corporate resources. To support using BlackBerry Protect with enrolled devices:

    - [Add MTD apps to devices](assign-apps)
    - [Create a device compliance policy that supports MTD](create-compliance-policy)
    - [Enable the MTD connector in Intune](enable-connector)
- **Support for unenrolled devices** - Intune can use the risk assessment data from the CylancePROTECT (BlackBerry) app on unenrolled devices when you use Intune app protection policies. Admins can use this combination to help protect corporate data within a [Microsoft Intune protected app](../../app-management/ref-protected-apps), Admins can also issue a block or selective wipe for corporate data on those unenrolled devices. To support using Better Mobile with unenrolled devices:

    - [Add the MTD app to unenrolled devices](add-apps-unenrolled-devices)
    - [Create a Mobile Threat Defense app protection policy](create-app-protection-policy)
    - [Enable the MTD connector in Intune for unenrolled devices](enable-unenrolled-devices)

## Sample scenarios

The following scenarios demonstrate the use of CylancePROTECT (BlackBerry) MTD when integrated with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Diagram of product flow for blocking access due to malicious apps.](media/blackberry/blackberry-malicious-apps-blocked.png)

*Access granted on remediation:*

![Diagram of product flow for granting access when malicious apps are remediated.](media/blackberry/blackberry-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Diagram of product flow for blocking access through Wi-Fi due to an alert.](media/blackberry/blackberry-network-wifi-blocked.png)

*Access granted on remediation:*

![ Diagram of product flow for granting access through Wi-Fi after the alert is remediated. ](media/blackberry/blackberry-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Diagram of product flow for blocking access to the organizations files due to an alert.](media/blackberry/blackberry-network-spo-blocked.png)

*Access granted on remediation:*

![Diagram of product flow for granting access to the organizations files after the alert is remediated.](media/blackberry/blackberry-network-spo-unblocked.png)

## Control access on unenrolled devices based on threats from malicious apps

When the BlackBerry Mobile Threat Defense solution considers a device to be infected:

![Diagram of product flow for App protection policies to block access due to malware.](media/blackberry/blackberry-mobile-app-policy-block.png)

Access is granted on remediation:

![ Diagram of product flow for App protection policies to grant access after malware is remediated.](media/blackberry/blackberry-mobile-app-policy-remediated.png)