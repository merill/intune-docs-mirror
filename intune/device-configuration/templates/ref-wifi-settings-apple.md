---
layout: Conceptual
title: Configure Wi-Fi Settings for Apple Devices in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple
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
description: Add or create a Wi-Fi configuration profile on iOS/iPadOS and macOS devices using Wi-Fi configuration settings in Microsoft Intune. Configure the connection details, authentication methods, SSIDs, security types, and proxy settings.
ms.date: 2026-06-23T00:00:00.0000000Z
ms.topic: article
ms.reviewer: wicale
zone_pivot_groups: platforms-apple
locale: en-us
document_id: 10a8caac-af1c-9c42-7e81-1eb9545db339
document_version_independent_id: 10a8caac-af1c-9c42-7e81-1eb9545db339
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-wifi-settings-apple.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-wifi-settings-apple
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-wifi-settings-apple.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 01536b7b-fbc2-4341-89f7-30aed41feb02
---

# Configure Wi-Fi Settings for Apple Devices in Intune - Microsoft Intune | Microsoft Learn

You can create a profile with specific Wi-Fi settings, and then deploy this profile to your iOS/iPadOS and macOS devices by using Intune. As part of your mobile device management (MDM) solution, use these settings to authenticate your network, add a PKCS (Public Key Cryptography Standards) or SCEP (Simple Certificate Enrollment Protocol) certificate, configure a proxy, and more.

These Wi-Fi settings are separated into two categories: **Basic settings** and **Enterprise settings**.

This article describes the settings you can configure. To learn more about Wi-Fi profiles in Intune, see [Wi-Fi device configuration profile](configure-wifi).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - iOS/iPadOS
> - macOS
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Create a [Wi-Fi device configuration profile](configure-wifi)
> - These settings are available for all enrollment types.
> 

## Basic profiles

Basic or personal profiles use WPA/WPA2 to secure the Wi-Fi connection on devices. Typically, WPA/WPA2 is used on home networks or personal networks. You can also add a preshared key to authenticate the connection.

- **Wi-Fi type**: Select **Basic**.

::: zone pivot="ios-ipados"

- **Network name**: Enter a name for this Wi-Fi connection. Users see this name when they browse the list of available connections on their device.

::: zone-end

- **SSID**: This **service set identifier** (SSID) property is the real name of the wireless network that devices connect to. However, users only see the network name you configured when they choose the connection.
- **Connect automatically**: **Enable** automatically connects to this network when the device is in range. **Disable** prevents devices from automatically connecting.
- **Hidden network**: **Enable** matches this device setting with the setting on the router Wi-Fi configuration. So if the network is set to hidden, then the network is also hidden in the Wi-Fi profile. Select **Disable** if the network SSID is broadcasted and visible.
- **Security type**: Select the security protocol to authenticate to the Wi-Fi network. Your options:

    - **Open (no authentication)**: Only use this option if the network is unsecured.
    - **WPA/WPA2 - Personal**: Enter the password in **Pre-shared key** (PSK). When your organization's network is set up or configured, a password or network key is also configured. Enter this password or network key for the PSK value.

::: zone pivot="ios-ipados"

    - **WPA2/WPA3 - Personal**: Enter the password in **Pre-shared key** (PSK). When your organization's network is set up or configured, a password or network key is also configured. Enter this password or network key for the PSK value.
    - **WPA3 - Personal**: Enter the password in **Pre-shared key** (PSK). When your organization's network is set up or configured, a password or network key is also configured. Enter this password or network key for the PSK value.

::: zone-end

    - **WEP**
- **Proxy settings**: Your options:

    - **None**: No proxy settings are configured.
    - **Manual**: Enter the **Proxy server address** as an IP address, and its **Port number**.
    - **Automatic**: Use a file to configure the proxy server. Enter the **Proxy server URL** that contains the configuration file. For example, enter `http://proxy.contoso.com`, `10.0.0.11`, or `http://proxy.contoso.com/proxy.pac`.

        For more information on PAC files, go to [Proxy Auto-Configuration (PAC) file](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_%28PAC%29_file) (opens a non-Microsoft site).

::: zone pivot="ios-ipados"

- **Disable MAC address randomization**: Devices present a randomized MAC address instead of the physical MAC address when connecting to a network. Using randomized MAC addresses is recommended for privacy, as it's harder to track a device by its MAC address. However, randomized MAC addresses break functionality that relies on a static MAC address, including network access control (NAC).

    Your options:

    - **Not configured**: Intune doesn't change or update this setting. By default, when devices connect to a new network, devices present a randomized MAC address instead of the physical MAC address.
    - **Yes**: Forces devices to present their actual Wi-Fi MAC address instead of a random MAC address. **Yes** allows devices to be tracked by their MAC address. Only disable MAC address randomization when necessary, such as for network access control (NAC) support.
    - **No**: Enables MAC address randomization on devices. Users can't turn it off. When devices connect to a new network, devices present a randomized MAC address, instead of the physical MAC address.

    This setting applies to:

    - iOS 14.0 and newer
    - iPadOS 14.0 and newer

::: zone-end

## Enterprise profiles

Enterprise profiles use Extensible Authentication Protocol (EAP) to authenticate Wi-Fi connections. EAP is often used by enterprises, as you can use certificates to authenticate and secure connections, and configure more security options.

::: zone pivot="macos"

- **Deployment channel**: Select how you want to deploy the profile. This setting also determines the keychain where the authentication certificates are stored, so it's important to select the proper channel. It's not possible to edit the deployment channel after you deploy the profile. To do so, you must create a new profile.

    Note

    We recommend rechecking the deployment channel setting in existing profiles when the linked authentication certificates are up for renewal to ensure the intended channel is selected. If it isn't, create a new profile with the correct deployment channel.

    You have two options:

    - **User channel**: Always select the user deployment channel in profiles with user certificates. This option stores certificates in the user keychain.
    - **Device channel**: Always select the device deployment channel in profiles with device certificates. This option stores certificates in the system keychain.

::: zone-end

- **Wi-Fi type**: Select **Enterprise**.

::: zone pivot="ios-ipados"

- **Network name**: Enter a name for this Wi-Fi connection. Users see this name when they browse the list of available connections on their device.

::: zone-end

- **SSID**: Short for **service set identifier**. This property is the real name of the wireless network that devices connect to. However, users only see the network name you configured when they choose the connection.
- **Connect automatically**: **Enable** automatically connects to this network when the device is in range. **Disable** prevents devices from automatically connecting.
- **Hidden network**: **Enable** matches this device setting with the setting on the router Wi-Fi configuration. So if the network is set to hidden, then the network is also hidden in the Wi-Fi profile. Select **Disable** if the network SSID is broadcasted and visible.

::: zone pivot="ios-ipados"

- **Security type**: Select the security protocol to authenticate to the Wi-Fi network. Your options:
    - **WPA - Enterprise**
    - **WPA/WPA2 - Enterprise**

::: zone-end

- **EAP type**: Select the Extensible Authentication Protocol (EAP) type used to authenticate secured wireless connections. Your options:

    - **EAP-FAST**: Enter the **Protected Access Credential (PAC) Settings**. This option uses protected access credentials to create an authenticated tunnel between the client and the authentication server. Your options:

        - **Do not use (PAC)**
        - **Use (PAC)**: If an existing PAC file exists, use it.
        - **Use and Provision PAC**: Create and add the PAC file to your devices.
        - **Use and Provision PAC Anonymously**: Create and add the PAC file to your devices without authenticating to the server.
    - **EAP-SIM**
    - **EAP-TLS**: Also enter:

        - **Certificate server names**: **Add** one or more common names used in the certificates issued by your trusted certificate authority (CA) to your wireless network access servers. For example, add `mywirelessserver.contoso.com` or `mywirelessserver`. When you enter this information, you can bypass the dynamic trust window displayed on user's devices when they connect to this Wi-Fi network. If you have multiple Radius servers with the same DNS suffix in their fully qualified domain name, enter a wildcard suffix. For example, you can enter `*.contoso.com`.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, you don't need to include a root certificate. This certificate allows the client to trust the wireless network access server's certificate.

::: zone pivot="macos"

        - **Certificates**: Select the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity that the device presents to the server to authenticate the connection. Choose the certificates that align with your deployment channel selection. If you select the user channel, your certificate options are limited to user certificate profiles. If you select the device channel, you have both user and device certificate profiles to choose from. However, always select the certificate type that aligns with the selected channel. Storing user certificates in the system keychain increases security risks.
        - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.

::: zone-end

::: zone pivot="ios-ipados"

        - **Authentication method**: Select the authentication method used by your device clients. Your options:

            - **Derived credential**: Use a certificate that's derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one. For more information, see [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).

                - **Certificates**: Select the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity that the device presents to the server to authenticate the connection.
            - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.

::: zone-end
    - **EAP-TTLS**: Also enter:

        - **Certificate server names**: **Add** one or more common names used in the certificates issued by your trusted certificate authority (CA) to your wireless network access servers. For example, add `mywirelessserver.contoso.com` or `mywirelessserver`. When you enter this information, you can bypass the dynamic trust window displayed on user's devices when they connect to this Wi-Fi network.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, you don't need to include a root certificate. This certificate allows the client to trust the wireless network access server's certificate.
        - **Authentication method**: Select the authentication method used by your device clients. Your options:

::: zone pivot="ios-ipados"

            - **Derived credential**: Use a certificate that's derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one. For more information, see [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).

::: zone-end

            - **Username and Password**: Prompt the user for a user name and password to authenticate the connection. Also enter:

                - **Non-EAP method (inner identity)**: Choose how you authenticate the connection. Be sure you choose the same protocol that is configured on your Wi-Fi network.

                    Your options: **Unencrypted password (PAP)**, **Challenge Handshake Authentication Protocol (CHAP)**, **Microsoft CHAP (MS-CHAP)**, or **Microsoft CHAP Version 2 (MS-CHAP v2)**

                    - **Certificates**: Select the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity that the device presents to the server to authenticate the connection.
            - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.
    - **LEAP**
    - **PEAP**: Also enter:

        - **Certificate server names**: **Add** one or more common names used in the certificates issued by your trusted certificate authority (CA) to your wireless network access servers. For example, add `mywirelessserver.contoso.com` or `mywirelessserver`. When you enter this information, you can bypass the dynamic trust window displayed on user's devices when they connect to this Wi-Fi network.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, you don't need to include a root certificate. This certificate allows the client to trust the wireless network access server's certificate.
        - **Authentication method**: Select the authentication method used by your device clients. Your options:

::: zone pivot="ios-ipados"

            - **Derived credential**: Use a certificate that's derived from a user's smart card. If no derived credential issuer is configured, Intune prompts you to add one. For more information, see [Use derived credentials in Microsoft Intune](../../device-security/certificates/derived-credentials).

::: zone-end

            - **Username and Password**: Prompt the user for a user name and password to authenticate the connection.

                - **Certificates**: Select the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity that the device presents to the server to authenticate the connection.
            - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.
- **Proxy settings**: Select a proxy configuration. Your options:

    - **None**: No proxy settings are configured.
    - **Manual**: Enter the **Proxy server address** as an IP address, and its **Port number**.
    - **Automatic**: Use a file to configure the proxy server. Enter the **Proxy server URL** that contains the configuration file. For example, enter `http://proxy.contoso.com`, `10.0.0.11`, or `http://proxy.contoso.com/proxy.pac`.

        For more information on PAC files, go to [Proxy Auto-Configuration (PAC) file](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_%28PAC%29_file) (opens a non-Microsoft site).

::: zone pivot="ios-ipados"

- **Disable MAC address randomization**: Devices present a randomized MAC address instead of the physical MAC address when connecting to a network. Using randomized MAC addresses is recommended for privacy, as it's harder to track a device by its MAC address. Randomized MAC addresses also break functionality that relies on a static MAC address, including network access control (NAC).

    Your options:

    - **Not configured**: Intune doesn't change or update this setting. By default, when connecting to a network, devices can present a randomized MAC address instead of the physical MAC address.
    - **Yes**: Forces devices to present their actual Wi-Fi MAC address instead of a random MAC address. **Yes** allows devices to be tracked by their MAC address. Only disable MAC address randomization when necessary, such as for network access control (NAC) support.
    - **No**: Enables MAC address randomization on devices. Users can't turn it off. When devices connect to a network, devices present a randomized MAC address, instead of the physical MAC address.

    This setting applies to:

    - iOS 14.0 and newer
    - iPadOS 14.0 and newer

::: zone-end