---
layout: Conceptual
title: Use VPN settings for Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: See all the settings to create VPN connections on Android device administrator devices in Microsoft Intune. Enter the connection name, IP address, or FQDN of the VPN server. Choose how users authenticate, and choose Citrix, SonicWall, Check Point Capsule, and Pulse Secure connection types.
ms.date: 2025-06-09T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: abalwan
locale: en-us
document_id: 79c3a3ff-6766-78ac-7ca2-ae5dbacaf951
document_version_independent_id: 79c3a3ff-6766-78ac-7ca2-ae5dbacaf951
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-vpn-settings-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-vpn-settings-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-vpn-settings-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
platformId: f40016d2-0152-021c-6674-48b1606d6b75
---

# Use VPN settings for Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article describes the different VPN connection settings you can control on Android devices. As part of your mobile device management (MDM) solution, use these settings to create a VPN connection, choose how the VPN authenticates, select a VPN server type, and more.

This feature applies to:

- Android device administrator (DA)

As an Intune administrator, you can create and assign VPN settings to Android devices. To learn more about VPN profiles in Intune, go to [VPN profiles](configure-vpn).

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- Create an [Android device administrator VPN device configuration profile](configure-vpn).
- Some Microsoft 365 services, such as Outlook, might not perform well using third party or partner VPNs. If you're using a third party or partner VPN, and experience a latency or performance issue, then remove the VPN.

    If removing the VPN resolves the behavior, then you can:

    - Work with the third party or partner VPN for possible resolutions. Microsoft doesn't provide technical support for third party or partner VPNs.
    - Don't use a VPN with Outlook traffic.
    - If you need to use a VPN, then use a split-tunnel VPN. And, allow the Outlook traffic to bypass the VPN.

    For more information, go to:

    - [Overview: VPN split tunneling for Microsoft 365](/en-us/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
    - [Using third-party network devices or solutions with Microsoft 365](/en-us/troubleshoot/microsoft-365-apps/office-suite-issues/office-365-third-party-network-devices)
    - [Microsoft 365 network connectivity principles](/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

## Base VPN

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address**: Enter the IP address or fully qualified domain name (FQDN) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Select how devices authenticate to the VPN server. Your options:

    - **Certificates**: Select an existing SCEP or PKCS certificate profile to authenticate the connection. [Configure certificates](../../fundamentals/certificates/overview) lists the steps to create a certificate profile.
    - **Username and password**: When users sign in to the VPN server, they're prompted to enter their user name and password.

        For more information, go to [Use derived credentials in Intune](../../device-security/certificates/derived-credentials).
- **Connection type**: Select the VPN connection type. Your options:

    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Access**
    - **Pulse Secure**
    - **Citrix SSO**
- **Fingerprint** (Check Point Capsule VPN only): Enter the fingerprint string given to you by the VPN vendor, like `Contoso Fingerprint Code`. This fingerprint verifies that the VPN server can be trusted.

    When authenticating, a fingerprint is sent to the client so the client knows to trust any server that has the same fingerprint. If the device doesn't have the fingerprint, it prompts the user to trust the VPN server while showing the fingerprint. The user manually verifies the fingerprint, and chooses to trust to connect.