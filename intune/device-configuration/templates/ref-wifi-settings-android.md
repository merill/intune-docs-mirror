---
layout: Conceptual
title: Configure Wi-Fi settings for Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android
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
description: Create or add a WiFi device configuration profile for Android device administrator. See the different settings, including adding certificates, choosing an EAP type, and selecting an authentication method in Microsoft Intune.
ms.date: 2025-06-09T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: abalwan
locale: en-us
document_id: f5e1750a-35df-e236-d34b-04b67b40911f
document_version_independent_id: f5e1750a-35df-e236-d34b-04b67b40911f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-wifi-settings-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-wifi-settings-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-wifi-settings-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 01457059-7362-5e07-3090-518bdad9df04
---

# Configure Wi-Fi settings for Android DA devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

You can create a profile with specific WiFi settings, and then deploy this profile to your Android devices. Microsoft Intune offers many features, including authenticating to your network, adding a PKCS or SCEP certificate, and more.

This feature applies to:

- Android device administrator (DA)

These Wi-Fi settings are separated in to two categories: Basic settings and Enterprise-level settings. This article describes these settings.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- Create an [Android device administrator Wi-Fi device configuration profile](configure-wifi).

## Basic

- **Wi-Fi type**: Choose **Basic**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. However, users only see the **network name** you configured when they choose the connection.

    You can only deploy one Wi-Fi profile to the same device with the same SSID. If you try to deploy multiple Wi-Fi profiles to the same device with the same SSID, then the profile isn't deployed to the device.
- **Hidden network**: Choose **Enable** to hide this network from the list of available networks on the device. The SSID isn't broadcasted. Choose **Disable** to show this network in the list of available networks on the device.

## Enterprise

- **Wi-Fi type**: Choose **Enterprise**.
- **SSID**: Enter the **service set identifier**, which is the real name of the wireless network that devices connect to. However, users only see the **network name** you configured when they choose the connection.

    You can only deploy one Wi-Fi profile to the same device with the same SSID. If you try to deploy multiple Wi-Fi profiles to the same device with the same SSID, then the profile isn't deployed to the device.
- **Hidden network**: Choose **Enable** to hide this network from the list of available networks on the device. The SSID isn't broadcasted. Choose **Disable** to show this network in the list of available networks on the device.
- **EAP type**: Choose the Extensible Authentication Protocol (EAP) type used to authenticate secured wireless connections. Your options:

    - **EAP-TLS**: Also enter:

        - **Server Trust** - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.
        - **Client Authentication** - **Client certificate for client authentication (Identity certificate)**: Choose the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection.
        - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent, and then followed by the real identification sent in a secure tunnel.​
    - **EAP-TTLS**: Also enter:

        - **Server Trust** - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.

            Note

            For Android 11 and newer, Google requires a Trusted root certificate.
        - **Client Authentication**: Choose an **Authentication method**. Your options:

            - **Username and Password**: Prompt the user for a user name and password to authenticate the connection. Also enter:

                - **Non-EAP method (inner identity)**: Choose how you authenticate the connection. Be sure you choose the same protocol that's configured on your Wi-Fi network. Your options:

                    - **Unencrypted password (PAP)**
                    - **Challenge Handshake Authentication Protocol (CHAP)**
                    - **Microsoft CHAP (MS-CHAP)**
                    - **Microsoft CHAP Version 2 (MS-CHAP v2)**
            - **Certificates**: Choose the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection.
            - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent, and then followed by the real identification sent in a secure tunnel.
    - **PEAP**: Also enter:

        - **Server Trust** - **Root certificate for server validation**: Select one or more existing trusted root certificate profiles. When the client connects to the network, these certificates are used to establish a chain of trust with the server. If your authentication server uses a public certificate, then you don't need to include a root certificate.
        - **Client Authentication**: Choose an **Authentication method**. Your options:

            - **Username and Password**: Prompt the user for a user name and password to authenticate the connection. Also enter:

                - **Non-EAP method for authentication (inner identity)**: Choose how you authenticate the connection. Be sure you choose the same protocol that's configured on your Wi-Fi network. Your options:

                    - **None**
                    - **Microsoft CHAP Version 2 (MS-CHAP v2)**
            - **Certificates**: Choose the SCEP or PKCS client certificate profile that is also deployed to the device. This certificate is the identity presented by the device to the server to authenticate the connection.
            - **Identity privacy (outer identity)**: Enter the text sent in the response to an EAP identity request. This text can be any value, such as `anonymous`. During authentication, this anonymous identity is initially sent, and then followed by the real identification sent in a secure tunnel.