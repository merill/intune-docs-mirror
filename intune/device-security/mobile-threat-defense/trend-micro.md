---
layout: Conceptual
title: Trend Micro Mobile Security and Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/trend-micro
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
description: How to set up Trend Micro Mobile Threat Defense with with Microsoft Intune to control mobile device access to your corporate resources
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 28b13baa-2d94-b2f8-5e3c-e64dcd01d64b
document_version_independent_id: 28b13baa-2d94-b2f8-5e3c-e64dcd01d64b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/trend-micro.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/trend-micro
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/trend-micro.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 297efa97-8e6d-427e-440b-b5fc66e9c29a
---

# Trend Micro Mobile Security and Microsoft Intune - Microsoft Intune | Microsoft Learn

Control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Trend Micro Mobile Security as a Service, a mobile threat defense (MTD) solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices protected by the Trend Micro Mobile Security as a Service, including:

- Malicious apps installed
- Malicious network behavior and profiles
- Operating system vulnerabilities
- Device misconfiguration

You can configure Conditional Access policies based on Trend Micro Mobile Security as a Service's risk assessment, enabled through Intune device compliance policies for enrolled devices. You can set up your policies to allow or block noncompliant devices from accessing corporate resources based on detected threats.

For more information about how to integrate Trend Micro with Microsoft Intune, see [Setting up Intune integration](https://docs.trendmicro.com/documentation/article/trend-vision-one-setting-up-intune-integration) in the Trend Micro Mobile Security documentation.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Supported platforms

- **Android 7.0 and later**
- **iOS 11.0 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Trend Micro account with administrative access to the Trend Micro Vision One console

## How do Intune and the Trend Micro MTD connector help protect your company resources?

The Trend Micro Mobile Security as a Service mobile agent app for Android and iOS/iPadOS captures file system, network stack, device, and application telemetry where available, then sends the telemetry data to Trend Micro Mobile Security as a Service to assess the device's risk for mobile threats.

- **Support for enrolled devices** - Intune device compliance policy includes a rule for MTD, which can use risk assessment information from Trend Micro. When the MTD rule is enabled, Intune evaluates device compliance with the policy that you enabled. If the device is found noncompliant, users are blocked access to corporate resources, such as Exchange Online and SharePoint Online. Users also receive guidance from the Trend Micro Mobile Security as a Service mobile agent app installed on their devices to resolve the issue and regain access to corporate resources. To support using Trend Micro with enrolled devices:

    - [Add MTD apps to devices](assign-apps) (This is done automatically when setting up Trend Micro Mobile Security as a Service integration)
    - [Create a device compliance policy that supports MTD](create-compliance-policy)
    - [Enable the MTD connector in Intune](enable-connector)

## Sample scenarios

The following scenarios demonstrate the use of Trend Micro MTD when integrated with Intune:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/trend-micro/trend-micro-malicious-apps-blocked.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/trend-micro/trend-micro-malicious-apps-unblocked.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/trend-micro/trend-micro-network-wifi-blocked.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated. ](media/trend-micro/trend-micro-network-wifi-unblocked.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/trend-micro/trend-micro-network-spo-blocked.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/trend-micro/trend-micro-network-spo-unblocked.png)