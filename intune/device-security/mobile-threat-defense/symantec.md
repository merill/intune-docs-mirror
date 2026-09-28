---
layout: Conceptual
title: Symantec Endpoint Protection Mobile connector with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/symantec
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
description: How to set up Symantec Endpoint Protection Mobile with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 35f328a2-ee01-621c-6b82-ac7aa2b3d61f
document_version_independent_id: 35f328a2-ee01-621c-6b82-ac7aa2b3d61f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/symantec.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/symantec
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/symantec.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5176328d-cae6-8adf-feda-3e80e7718101
---

# Symantec Endpoint Protection Mobile connector with Microsoft Intune - Microsoft Intune | Microsoft Learn

You can control mobile device access to corporate resources using Conditional Access based on risk assessment conducted by Symantec Endpoint Protection Mobile (SEP Mobile), a mobile threat defense solution that integrates with Microsoft Intune. Risk is assessed based on telemetry collected from devices running SEP Mobile, including:

- Physical defense
- Network defense
- Application defense
- Vulnerabilities defense

You can enable SEP Mobile risk assessment through Intune device compliance policies, and then use Conditional Access policies to allow or block noncompliant device access to corporate resources based on detected threats.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Supported platforms

- **Android 5.0 and later**
- **iOS 10 and later**

## Prerequisites

- Microsoft Entra ID P1
- Microsoft Intune Plan 1 subscription
- Symantec Endpoint Protection Mobile subscription

For more information, check [Symantec website](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection-mobile/1-0/integrations/integrating-microsoft-intune-with-v131237277-d4221e13845.html).

## How do Intune and SEP Mobile help protect your company resources?

SEP Mobile app for Android or iOS/iPadOS captures file system, network stack, device and application telemetry where available, then sends it to the Symantec cloud service to assess the device's risk for mobile threats.

The Intune device compliance policy includes a rule for SEP Mobile, which is based on the SEP Mobile risk assessment. When this rule is enabled, Intune evaluates device compliance with the policy that you enabled.

If the device is found noncompliant, access to resources like Exchange Online and SharePoint Online are blocked. Users on blocked devices receive guidance from the SEP Mobile app to resolve the issue and regain access to corporate resources.

Intune supports two modes of integration with SEP Mobile:

- **Basic setup** which is a read only mode that allows SEP Mobile visibility for devices in Intune.
- **Full integration** which allows SEP Mobile to report device risk and security incident details to Intune.

## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

- Connecting to corporate e-mail
- Syncing corporate files with the OneDrive for Work app
- Accessing company apps

*Block when malicious apps are detected:*

![Product flow for blocking access due to malicious apps.](media/symantec/symantec-arch-1.png)

*Access granted on remediation:*

![Product flow for granting access when malicious apps are remediated.](media/symantec/symantec-arch-2.png)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

*Block network access through Wi-Fi:*

![Product flow for blocking access through Wi-Fi due to an alert.](media/symantec/symantec-arch-3.png)

*Access granted on remediation:*

![ Product flow for granting access through Wi-Fi after the alert is remediated. ](media/symantec/symantec-arch-4.png)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

*Block SharePoint Online when network threats are detected:*

![Product flow for blocking access to the organizations files due to an alert.](media/symantec/symantec-arch-5.png)

*Access granted on remediation:*

![Product flow for granting access to the organizations files after the alert is remediated.](media/symantec/symantec-arch-6.png)

### Control access on unenrolled devices based on threats from malicious apps

When the Symantec Endpoint Protection Mobile Threat Defense solution considers a device to be infected:

![Product flow for App protection policies to block access due to malware.](media/symantec/symantec-app-policy-block.png)

Access is granted on remediation:

![ Product flow for App protection policies to grant access after malware is remediated.](media/symantec/symantec-app-policy-remediated.png)