---
layout: Conceptual
title: Configure wired network settings for Apple devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wired-network-settings-macos
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
description: Create or add a wired network device configuration profile for Apple devices. See the different settings, add certificates, choose an EAP type, and select an authentication method in Microsoft Intune.
ms.date: 2026-06-04T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: wicale
zone_pivot_groups: platforms-apple
locale: en-us
document_id: 5712d0eb-99ee-41d9-5286-060c4d1bc2f6
document_version_independent_id: 5712d0eb-99ee-41d9-5286-060c4d1bc2f6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-wired-network-settings-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-wired-network-settings-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-wired-network-settings-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d846119e-9420-4137-bf72-48297f8603a6
---

# Configure wired network settings for Apple devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

You can create a profile with specific wired network settings, and then deploy this profile to your iOS/iPadOS and macOS devices. Microsoft Intune offers many features, including authenticating to your network, adding a Simple Certificate Enrollment Protocol (SCEP) certificate, and more.

This article describes the settings you can configure. To learn more about Wired Network profiles in Intune, see [wired network device configuration profile](configure-wired-networks).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - iOS/iPadOS
> - macOS
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> - Create a [wired network device configuration profile](configure-wired-networks).
> - These settings are available for all enrollment types.
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

## Wired Network

::: zone pivot="ios-ipados"

- **Network Interface**: Automatically set to **Any Ethernet**.

::: zone-end

::: zone pivot="macos"

- **Deployment channel**: Select how you want to deploy the profile. This setting also determines the keychain where the authentication certificates are stored, so it's important to select the proper channel. It's not possible to edit the deployment channel after you deploy the profile. To do so, you must create a new profile.

    Note

    When the linked authentication certificates are ready for renewal, confirm the deployment channel setting in existing profiles. This step makes sure the intended channel is selected. If it isn't, create a new profile with the correct deployment channel.

    You have two options:

    - **User channel**: Always select the user deployment channel in profiles with user certificates. This option stores certificates in the user keychain.
    - **Device channel**: Always select the device deployment channel in profiles with device certificates. This option stores certificates in the system keychain.
- **Network Interface**: Select the network interfaces on the device the profile applies to, based on service-order priority. Your options:

    - **First active Ethernet** (default)
    - **Second active Ethernet**
    - **Third active Ethernet**
    - **First Ethernet**
    - **Second Ethernet**
    - **Third Ethernet**
    - **Any Ethernet**

    Options with "active" in the title use interfaces that are actively working on the device. If there are no active interfaces, the next interface in service-order priority is configured. By default, **First active Ethernet** is selected, which is also the default setting configured by macOS.

::: zone-end

- **EAP type**: To authenticate secured wired connections, select the Extensible Authentication Protocol (EAP) type. Your options:

::: zone pivot="macos"

    - **EAP-FAST**: Enter the **Protected Access Credential (PAC) Settings**. This option uses protected access credentials to create an authenticated tunnel between the client and the authentication server. Your options:
        - **Do not use (PAC)**
        - **Use (PAC)**: If an existing PAC file exists, use it.
        - **Use and Provision PAC**: Create and add the PAC file to your devices.
        - **Use and Provision PAC Anonymously**: Create and add the PAC file to your devices without authenticating to the server.

::: zone-end

    - **EAP-TLS**: Also enter:

        - **Server Trust** - **Certificate server names**: Enter one or more common names used in the certificates issued by your trusted certificate authority (CA). When you enter this information, you can bypass the dynamic trust window shown on user devices when they connect to this network.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.
        - **Client Authentication** - **Certificates**: Select an existing SCEP client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection. Public Key Cryptography Standards (PKCS) certificates aren't supported.
        - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.
    - **EAP-TTLS**: Also enter:

        - **Server Trust** - **Certificate server names**: Enter one or more common names used in the certificates issued by your trusted certificate authority (CA). When you enter this information, you can bypass the dynamic trust window shown on user devices when they connect to this network.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.

::: zone pivot="ios-ipados"

        - **Client Authentication** - **Certificates**: Select an existing SCEP client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection. PKCS certificates aren't supported. Choose the certificate that aligns with your deployment channel selection. If you selected the user channel, your certificate options are limited to user certificate profiles. If you selected the device channel, you have both user and device certificate profiles to choose from. However, we recommend always selecting the certificate type that aligns with the selected channel. Storing user certificates in the system keychain increases security risks.

::: zone-end

::: zone pivot="macos"

        - **Client Authentication**: Select an **Authentication method**. Your options:

            - **Username and Password**: Prompts the user for a user name and password to authenticate the connection. Also enter:

                - **Non-EAP method (inner identity)**: Select how you authenticate the connection. Be sure you choose the same protocol that is configured on your network. Your options:
                    - **Unencrypted password (PAP)**
                    - **Challenge Handshake Authentication Protocol (CHAP)**
                    - **Microsoft CHAP (MS-CHAP)**
                    - **Microsoft CHAP Version 2 (MS-CHAP v2)**
            - **Certificates**: Select an existing SCEP client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection. PKCS certificates aren't supported. Choose the certificate that aligns with your deployment channel selection. If you selected the user channel, your certificate options are limited to user certificate profiles. If you selected the device channel, you have both user and device certificate profiles to choose from. However, we recommend always selecting the certificate type that aligns with the selected channel. Storing user certificates in the system keychain increases security risks.

::: zone-end

        - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.

::: zone pivot="macos"

    - **LEAP**

::: zone-end

    - **PEAP**: Also enter:

        - **Server Trust** - **Certificate server names**: Enter one or more common names used in the certificates issued by your trusted certificate authority (CA). When you enter this information, you can bypass the dynamic trust window shown on user devices when they connect to this network.
        - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.

::: zone pivot="ios-ipados"

        - **Client Authentication** - **Certificates**: Select an existing SCEP client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection. PKCS certificates aren't supported.

::: zone-end

::: zone pivot="macos"

        - **Client Authentication**: Select an **Authentication method**. Your options:

            - **Username and Password**: Prompts the user for a user name and password to authenticate the connection.
            - **Certificates**: Select an existing SCEP client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection. PKCS certificates aren't supported.

::: zone-end

        - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent. Then, the real identification is sent in a secure tunnel.