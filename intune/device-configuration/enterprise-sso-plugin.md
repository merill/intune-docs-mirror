---
layout: Conceptual
title: Single sign-on (SSO) for iOS/iPadOS and macOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/enterprise-sso-plugin
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
description: Overview of Microsoft Enterprise SSO plug-in in Microsoft Intune, Jamf Pro, and other MDM solution providers. The Enterprise SSO plug-in is available on iOS/iPadOS and macOS devices.
ms.date: 2026-02-10T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: beflamm, arnab
zone_pivot_groups: apple-enterprise-sso
locale: en-us
document_id: 4e498da8-73ee-856f-deaa-87bfb5b81f72
document_version_independent_id: 4e498da8-73ee-856f-deaa-87bfb5b81f72
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/enterprise-sso-plugin.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/enterprise-sso-plugin
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/enterprise-sso-plugin.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 59ce32e0-b563-b2c8-e78c-5b746b3f1b0a
---

# Single sign-on (SSO) for iOS/iPadOS and macOS - Microsoft Intune | Microsoft Learn

Apple devices can use single sign-on (SSO) to access devices, apps, and websites using their Microsoft Entra ID. SSO lets users sign in and get access without entering their credentials each time.

This feature applies to:

- iOS/iPadOS
- macOS

Devices and most apps, including Line of Business (LOB) apps, require some level of user authentication. In many cases, the authentication requires users to enter the same credentials repeatedly.

Admins can use Microsoft Intune to create and deploy SSO policies. Developers can create apps that support and use single sign-on (SSO). When you combine the Intune SSO policies with apps that support SSO, then the number of credential prompts for apps and websites is reduced.

To configure SSO for Apple devices in Intune, you have the following options:

- **Platform SSO** - Part of the [Microsoft Enterprise SSO plug-in](/en-us/entra/identity-platform/apple-sso-plugin) in Microsoft Entra ID and includes the SSO app extension. Applies to macOS devices.
- **SSO app extension** - Part of the [Microsoft Enterprise SSO plug-in](/en-us/entra/identity-platform/apple-sso-plugin) in Microsoft Entra ID. Applies to iOS/iPadOS and macOS devices.
- **Single sign-on template** - A template in Intune. Applies to iOS/iPadOS devices.

This article provides an overview of the SSO options available for Apple devices in Intune, and their supported platforms.

::: zone pivot="all,macos"

## Platform SSO

This feature applies to:

- macOS

The [Microsoft Enterprise SSO plug-in](/en-us/entra/identity-platform/apple-sso-plugin) includes two SSO features - **Platform SSO** and the **SSO app extension**. This section focuses on **Platform SSO**.

On macOS devices, users normally sign in with a local account. Then, they sign in to apps and websites with their Microsoft Entra ID.

With Platform SSO:

- Organizations can:

    - Choose the authentication method that meets your business need. Your options are Secure Enclave passwordless passkey authentication, Microsoft Entra user account & password, or smart card authentication.
    - Use the SSO app extension, as the SSO app extension is part of Platform SSO. Specifically, you:

        - Use the SSO app extension to sign in to apps and websites with Microsoft Entra ID.
        - Use Platform SSO to enhance your SSO configuration. You can configure different authentication methods, create new organizational users at sign in, and assign authorization modes for users.
- End users:

    - Get a more secure sign-in experience as Microsoft Entra ID integrates with the Microsoft Enterprise SSO plug-in.
    - Get a single sign-on experience when combined with the SSO app extension. The SSO app extension allows using Touch ID and passkeys with Microsoft Entra ID.
    - Can sign in with their Microsoft Entra user account and minimize the number of times they need to enter their Microsoft Entra credentials on their macOS devices.

For more information on Platform SSO and to get started, go to [Configure Platform SSO for macOS devices in Intune](settings-catalog/configure-platform-sso-macos).

### Platform SSO feature summary

The following table summarizes the Platform SSO features in Intune. Use this information to determine if Platform SSO is right for your organization.

| Feature | Details |
| --- | --- |
| **Platform support** | ![error-icon](../media/icons/16/error.svg) iOS/iPadOS ![check-icon](../media/icons/16/check.svg) macOS 13.0 and newer |
| **Supported enrollment types** | ![check-icon](../media/icons/16/check.svg) Device enrollment![check-icon](../media/icons/16/check.svg) Automated Device Enrollment (supervised) ![error-icon](../media/icons/16/error.svg) User enrollment ![check-icon](../media/icons/16/check.svg) Direct enrollment (Apple Configurator) |
| **Supported authentication types** | ![check-icon](../media/icons/16/check.svg) Secure Enclave (UserSecureEnclaveKey) ![check-icon](../media/icons/16/check.svg) Password (Microsoft Entra ID) ![check-icon](../media/icons/16/check.svg) Smartcard |
| **Supported app types** | ![check-icon](../media/icons/16/check.svg) Microsoft 365 apps![check-icon](../media/icons/16/check.svg) Apps, websites or services integrated with Microsoft Entra ID ![check-icon](../media/icons/16/check.svg) Apps, websites or services that support Apple Enterprise SSO and are integrated with on-premises Active Directory |
| **Intune admin center policy type** | **Settings catalog** policy at:**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **macOS** for platform &gt; **Settings catalog** for profile type &gt; **Authentication** &gt; **Extensible Single Sign On (SSO)** |
| **Recommendation** | ![check-icon](../media/icons/16/check.svg) Recommended.  Use Platform SSO, as it also includes the SSO app extension. You can use the SSO app extension on its own, but it's not preferred.  To use Platform SSO, you must use only Platform SSO. Don't create a separate SSO app extension policy. |

::: zone-end

::: zone pivot="all,ios-ipados,macos"

## SSO app extension

This feature applies to:

- iOS/iPadOS
- macOS

The [Microsoft Enterprise SSO plug-in](/en-us/entra/identity-platform/apple-sso-plugin) includes two SSO features - **Platform SSO** and the **SSO app extension**. This section focuses on the **SSO app extension**.

The SSO app extension provides SSO to apps, websites, and accounts that use Microsoft Entra ID for authentication, including:

- Microsoft 365 apps
- Apps that are developed to look for the user credential store in single sign-on on the device
- On-premises Active Directory accounts across all apps that support Apple's Enterprise SSO feature

![check-icon](../media/icons/16/check.svg)**For iOS/iPadOS devices**, the SSO app extension is available by itself. So, you can configure and use the SSO app extension for your apps & websites.

![check-icon](../media/icons/16/check.svg)**For macOS devices**, the SSO app extension is available by itself and is also included in Platform SSO. So, you can configure and use only the SSO app extension if you don't want to use Platform SSO. If you use Platform SSO, then you only configure Platform SSO, as it includes the SSO app extension.

The SSO app extension is a redirect-type SSO app extension. It's available for Intune, Jamf Pro, and other MDM solutions. In Intune, the SSO app extension uses a device configuration policy with Microsoft Entra ID as the SSO app extension type.

These settings configure redirect-type and credential-type SSO app extensions. Specifically:

- The **redirect** type is designed for modern authentication protocols, such as OpenID Connect, OAuth, and SAML2. You can choose between the Microsoft Entra SSO extension ([Microsoft Enterprise SSO plug-in](/en-us/entra/identity-platform/apple-sso-plugin) and a generic redirect extension.
- The **credential** type is designed for challenge-and-response authentication flows. You can choose between a Kerberos-specific credential extension provided by Apple, and a generic credential extension.

    The SSO app extension should work with any non-Microsoft or partner MDM. The extension must be deployed as a kerberos SSO extension, or deployed as a custom configuration profile with all the required properties configured.

For more information on the SSO app extension, go to:

- iOS/iPadOS:

    - [Use the SSO app extension on iOS/iPadOS devices in Intune](settings-catalog/configure-enterprise-sso-plugin-ios)
    - [SSO app extension settings list - iOS/iPadOS in Intune](templates/ref-device-features-apple)
- macOS:

    - [Use the SSO app extension on macOS devices in Intune](templates/configure-enterprise-sso-plugin-macos)
    - [SSO app extension settings list - macOS in Intune](templates/ref-device-features-apple)

### SSO app extension feature summary

The following table summarizes the SSO app extension features in Intune. Use this information to determine if this SSO option is right for your organization.

| Feature | Details |
| --- | --- |
| **Platform support** | ![check-icon](../media/icons/16/check.svg) iOS/iPadOS 13.0 and newer ![check-icon](../media/icons/16/check.svg) macOS 10.15 and newer |
| **Supported enrollment types** | iOS/iPadOS:![check-icon](../media/icons/16/check.svg) Device enrollment![check-icon](../media/icons/16/check.svg) Automated Device Enrollment (supervised) ![check-icon](../media/icons/16/check.svg) User enrollment ![check-icon](../media/icons/16/check.svg) Direct enrollment (Apple Configurator) macOS: ![check-icon](../media/icons/16/check.svg) User approved device enrollment ![check-icon](../media/icons/16/check.svg) Automated Device Enrollment (supervised)![check-icon](../media/icons/16/check.svg) Direct enrollment (Apple Configurator) |
| **Supported authentication types** | ![check-icon](../media/icons/16/check.svg) Redirect-type SSO app extension, including Microsoft Entra ID ![check-icon](../media/icons/16/check.svg) Credential app extension ![check-icon](../media/icons/16/check.svg) Apple's built-in Kerberos extension |
| **Supported app types** | ![check-icon](../media/icons/16/check.svg) Microsoft 365 apps![check-icon](../media/icons/16/check.svg) Apps, websites or services integrated with Microsoft Entra ID ![check-icon](../media/icons/16/check.svg) Apps, websites or services that support Apple's Enterprise SSO and are integrated with on-premises Active Directory |
| **Intune admin center policy type** | **Device Features** template at: **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **iOS/iPadOS** or **macOS** for platform &gt; **Templates** &gt; **Device features** for profile type &gt; **Single sign-on app extension** |
| **Recommendation** | ![check-icon](../media/icons/16/check.svg) Recommended on iOS/iPadOS. ![error-icon](../media/icons/16/error.svg) Not preferred on macOS devices.  On macOS devices, you can use the SSO app extension by itself. But, we recommend you use Platform SSO instead. If you're also using Platform SSO for macOS, then don't create a separate SSO app extension policy. The SSO app extension is included in the Platform SSO configuration. |

::: zone-end

::: zone pivot="all,ios-ipados"

## Single sign-on template

Note

Instead of these SSO settings, Apple recommends you use the SSO app extension (in this article).

Applies to:

- iOS 7.0 and newer
- iPadOS 13.0 and newer

This single sign-on policy is based on Kerberos. Kerberos is a network authentication protocol that uses secret key cryptography to authenticate client-server applications. The Intune policy settings define Kerberos account information when accessing servers or specific apps, and handle Kerberos challenges for web pages and native apps.

For a list of the settings you can configure in Intune, go to [Single sign-on on iOS/iPadOS](templates/ref-device-features-apple).

To use single sign-on, be sure you have:

- An app that's developed to look for the user credential store in single sign-on on the device.
- Intune configured for iOS/iPadOS device single sign-on.

### Single sign-on feature summary

The following table summarizes the Single sign-on features in Intune. Use this information to determine if this SSO option is right for your organization.

| Feature | Details |
| --- | --- |
| **Platform support** | ![check-icon](../media/icons/16/check.svg) iOS 7.0 and newer![check-icon](../media/icons/16/check.svg) iPadOS 13.0 and newer ![error-icon](../media/icons/16/error.svg) macOS |
| **Supported enrollment types** | ![check-icon](../media/icons/16/check.svg) Device enrollment![check-icon](../media/icons/16/check.svg) Automated Device Enrollment (supervised) ![error-icon](../media/icons/16/error.svg) User enrollment ![error-icon](../media/icons/16/error.svg) Direct enrollment (Apple Configurator) |
| **Supported authentication types** | Can only use Kerberos SSO authentication.  - Enter Kerberos account information for when users access servers or apps. - Isn't an Apple implementation of Kerberos. - Handles Kerberos challenges for web pages and apps |
| **Supported app types** | Website and native apps that support Kerberos authentication. App must be coded to look for the user credential store in single sign-on on the device. |
| **Intune admin center policy type** | **Device Features** template at: **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **iOS/iPadOS** for platform &gt; **Templates** &gt; **Device features** for profile type &gt; **Single sign-on** |
| **Recommendation** | ![error-icon](../media/icons/16/error.svg) Not recommended. Instead, Microsoft recommends using the SSO app extension (in this article). |

::: zone-end

## SSO app extension vs SSO template

The **Single sign-on app extension** feature is different than the **Single sign-on** feature. Use the following table to compare.

| - | Single sign-on app extension | Single sign-on |
| --- | --- | --- |
| **Supported platforms** | ![check-icon](../media/icons/16/check.svg) iOS/iPadOS 13.0 and newer ![check-icon](../media/icons/16/check.svg) macOS 10.15 and newer | ![check-icon](../media/icons/16/check.svg) iOS 7.0 and newer ![check-icon](../media/icons/16/check.svg) iPadOS 13.0 and newer ![error-icon](../media/icons/16/error.svg) macOS |
| **Description** | Define extensions for use by identity providers or organizations to deliver a seamless enterprise sign-on experience. It uses the Apple operating system to authenticate. | Define Kerberos account information for when users access servers or apps. |
| **Authentication** | From an app development perspective, can use any type of redirect SSO or credential SSO authentication. | From an app development perspective, can only use Kerberos SSO authentication. |
| **Apple implementation** | Developed by Apple and built into the iOS/iPadOS 13.0+ and macOS 10.15+ platforms. The built-in Kerberos extension can be used to sign users into native apps and websites that support Kerberos authentication. | Not an Apple implementation of Kerberos. |
| **Recommendation** | Recommended. Provides an improved end-user experience. It handles Kerberos challenges for web pages, supports password changes, and behaves better in enterprise networks.  When deciding to use Kerberos in the **SSO app extension** or **Single sign-on** template, we recommend using the SSO app extension due to improved performance and capabilities. | Not recommended. It does handle Kerberos challenges for web pages. |