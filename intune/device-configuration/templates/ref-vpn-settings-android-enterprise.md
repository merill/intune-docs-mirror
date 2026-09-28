---
layout: Conceptual
title: Use VPN settings for Android Enterprise in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise
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
description: See all the settings to create VPN connections on Android Enterprise devices in Microsoft Intune, including COBO, COSU, COPE, and BYOD. Enter the connection name, IP address, or FQDN of the VPN server. Choose how users authenticate and choose Citrix, SonicWall, Check Point Capsule, and Pulse Secure connection types.
ms.date: 2024-06-26T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: abalwan
locale: en-us
document_id: 304a95d8-025a-53b6-45ed-4d434c211d3d
document_version_independent_id: 304a95d8-025a-53b6-45ed-4d434c211d3d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-vpn-settings-android-enterprise.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-vpn-settings-android-enterprise
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-vpn-settings-android-enterprise.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
platformId: 385640bb-d9c0-112d-dd94-a416ee5c26bd
---

# Use VPN settings for Android Enterprise in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article describes the different VPN connection settings you can control on Android Enterprise devices. As part of your mobile device management (MDM) solution, use these settings to create a VPN connection, choose how the VPN authenticates, select a VPN server type, and more.

This feature applies to:

- Android Enterprise personally owned devices with a work profile (BYOD)
- Android Enterprise corporate-owned work profile (COPE)
- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)

As an Intune administrator, you can create and assign VPN settings to Android Enterprise devices. To learn more about VPN profiles in Intune, see [VPN profiles](configure-vpn).

Note

To configure always-on VPN, you need to:

1. Create a VPN profile with your connection info, as described in this article.
2. Create an [Android Enterprise device restrictions](ref-device-restrictions-android-enterprise) &gt; **Corporate-owned** &gt; **Connectivity** profile with the Always-on VPN setting configured.
3. Assign both profiles to your groups.

## Before you begin

- Create an [Android Enterprise VPN device configuration profile](configure-vpn):

    - Fully managed, dedicated, and corporate-owned work profile
    - Personally owned work profile
- Some Microsoft 365 services, such as Outlook, might not perform well using third party or partner VPNs. If you're using a third party or partner VPN, and experience a latency or performance issue, then remove the VPN.

    If removing the VPN resolves the behavior, then you can:

    - Work with the third party or partner VPN for possible resolutions. Microsoft doesn't provide technical support for third party or partner VPNs.
    - Don't use a VPN with Outlook traffic.
    - If you need to use a VPN, then use a split-tunnel VPN. And, allow the Outlook traffic to bypass the VPN.

    For more information, go to:

    - [Overview: VPN split tunneling for Microsoft 365](/en-us/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
    - [Using third-party network devices or solutions with Microsoft 365](/en-us/troubleshoot/microsoft-365-apps/office-suite-issues/office-365-third-party-network-devices)
    - [Microsoft 365 network connectivity principles](/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)
- If you need these devices to access on-premises resources using modern authentication and Conditional Access, then you can use the [Microsoft Tunnel](../../device-security/microsoft-tunnel/overview), which supports split tunneling.

## Fully Managed, Dedicated, and Corporate-Owned Work Profile

- **Connection type**: Select the VPN connection type. Your options:

    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Access**
    - **Pulse Secure**
    - **Microsoft Tunnel** (Not supported on Android Enterprise dedicated devices.)

The available settings depend on the VPN client you choose. Some settings are only available for specific VPN clients.

### Base VPN (fully managed, dedicated, and corporate-owned work profile)

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address or FQDN**: Enter the IP address or fully qualified domain name (FQDN) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Choose how devices authenticate to the VPN server. Your options:

    - **Certificates**: Select an existing SCEP or PKCS certificate profile that authenticates the connection. [Configure certificates](../../fundamentals/certificates/overview) lists the steps to create a certificate profile.
    - **Username and password**: When end users sign in to the VPN server, users are prompted to enter their user name and password.
    - **Derived credential**: Use a certificate that is derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one.

        For more information, see [Use derived credentials in Intune](../../device-security/certificates/derived-credentials).
- **Enter key and value pairs for the NetMotion Mobility VPN attributes**: Add or import **Keys** and **Values** that customize your VPN connection. These values are typically supplied by your VPN provider.
- **Microsoft Tunnel site** (Microsoft Tunnel only): Select an existing site. The VPN client connects to the public IP address or FQDN of this site.

    For more information, see [Microsoft Tunnel for Intune](../../device-security/microsoft-tunnel/overview).

### Per-app VPN (fully managed, dedicated, and corporate-owned work profile)

- **Add**: Select managed apps from the list. When users start the apps you add, traffic automatically routes through the VPN connection.

For more information, see [Use a VPN and per-app VPN policy on Android Enterprise devices](../../app-management/configuration/configure-vpn-android).

### Always-on VPN (fully managed, dedicated, and corporate-owned work profile)

- **Always-on VPN**: **Enable** turns on always-on VPN so VPN clients automatically connect and reconnect to the VPN when possible. When set to **Not configured**, Intune doesn't change or update this setting. By default, always-on VPN might be disabled for all VPN clients.

    Only one VPN client can be configured for always-on VPN on a device. Be sure to have no more than one always-on VPN policy deployed to a single device.

### Proxy (fully managed, dedicated, and corporate-owned work profile)

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the proxy server URL that includes the configuration file. For example, enter `http://proxy.contoso.com/pac`.
- **Address**: Enter the IP address or fully qualified host name of the proxy server. For example, enter `10.0.0.3` or `vpn.contoso.com`.
- **Port number**: Enter the port number associated with the proxy server. For example, enter `8080`.

## Personally owned work profile

- **Connection type**: Select the VPN connection type. Your options:

    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**

        Note

        With Cisco AnyConnect in the personally owned work profile, there may be some extra steps for end users to complete the VPN connection. For more information, go to [VPN profiles - What successful VPN profiles look like](/en-us/troubleshoot/mem/intune/device-configuration/troubleshoot-vpn-profiles?tabs=android#what-successful-vpn-profiles-look-like).
    - **SonicWall Mobile Connect**
    - **F5 Access**
    - **Pulse Secure**
    - **NetMotion Mobility**
    - **Microsoft Tunnel**

The available settings depend on the VPN client you choose. Some settings are only available for specific VPN clients.

### Base VPN (personally owned work profile)

- **Connection name**: Enter a name for this connection. End users see this name when they browse their device for the available VPN connections. For example, enter `Contoso VPN`.
- **VPN server address**: Enter the IP address or fully qualified domain name (FQDN) of the VPN server that devices connect. For example, enter `192.168.1.1` or `vpn.contoso.com`.
- **Authentication method**: Choose how devices authenticate to the VPN server. Your options:

    - **Certificates**: Select an existing SCEP or PKCS certificate profile that authenticates the connection. [Configure certificates](../../fundamentals/certificates/overview) lists the steps to create a certificate profile.
    - **Username and password**: When end users sign in to the VPN server, users are prompted to enter their user name and password.
    - **Derived credential**: Use a certificate that is derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one.

        For more information, see [Use derived credentials in Intune](../../device-security/certificates/derived-credentials).
- **Fingerprint** (Check Point Capsule VPN only): Enter the fingerprint string given to you by the VPN vendor, such as `Contoso Fingerprint Code`. This fingerprint verifies that the VPN server can be trusted.

    When authenticating, a fingerprint is sent to the client so the client knows to trust any server that has the same fingerprint. If the device doesn't have the fingerprint, it prompts the user to trust the VPN server while showing the fingerprint. The user manually verifies the fingerprint, and chooses to trust to connect.
- **Enter key and value pairs for the NetMotion Mobility VPN attributes**: Add or import **Keys** and **Values** that customize your VPN connection. These values are typically supplied by your VPN provider.
- **Microsoft Tunnel site** (Microsoft Tunnel only): Select an existing site. The VPN client connects to the public IP address or FQDN of this site.

    For more information, see [Microsoft Tunnel for Intune](../../device-security/microsoft-tunnel/overview).

### Per-app VPN (personally owned work profile)

- **Add**: Select managed apps from the list. When users start the apps you add, traffic automatically routes through the VPN connection.

For more information, see [Use a VPN and per-app VPN policy on Android Enterprise devices](../../app-management/configuration/configure-vpn-android).

### Always-on VPN (personally owned work profile)

- **Always-on VPN**: **Enable** turns on always-on VPN so VPN clients automatically connect and reconnect to the VPN when possible. When set to **Not configured**, Intune doesn't change or update this setting. By default, always-on VPN might be disabled for all VPN clients.

    Only one VPN client can be configured for always-on VPN on a device. Be sure to have no more than one always-on VPN policy deployed to a single device.

### Proxy (personally owned work profile)

- **Automatic configuration script**: Use a file to configure the proxy server. Enter the proxy server URL that includes the configuration file. For example, enter `http://proxy.contoso.com/pac`.
- **Address**: Enter the IP address or fully qualified host name of the proxy server. For example, enter `10.0.0.3` or `vpn.contoso.com`.
- **Port number**: Enter the port number associated with the proxy server. For example, enter `8080`.