---
layout: Conceptual
title: Configure endpoint protection on macOS devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-endpoint-protection-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- endpoint-protection
- sub-secure-endpoints
ms.subservice: configuration
description: Use Intune to configure macOS devices use the built-in firewall to allow or block specific apps or to use stealth mode, to use Gatekeeper to determine where apps install, and to use FileVault disk encryption.
ms.date: 2024-10-25T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
locale: en-us
document_id: 6ab64b73-6197-54fb-4d29-bad082f7da46
document_version_independent_id: 6ab64b73-6197-54fb-4d29-bad082f7da46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-endpoint-protection-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-endpoint-protection-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-endpoint-protection-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 9413c989-030e-109d-2a23-aff214c48ad4
---

# Configure endpoint protection on macOS devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

The macOS endpoint protection template has been deprecated. Existing policies remain unchanged, but you can no longer create new policies using this template. &gt; Instead, use one of the following options:

- Use Endpoint security policies like [disk encryption](disk-encryption) for Filevault, or [Firewall](firewall) policy.
- Use the Settings catalog to create new configuration policies for FileVault, Firewall, and System Policy Control (Gatekeeper) payloads. For more information, see [macOS settings catalog](../settings-catalog/).

This article shows you the endpoint protection settings that you can configure for devices that run macOS. You configure these settings by using a macOS device configuration profile for [endpoint protection](configure-endpoint-protection) in Intune.

## Before you begin

[Create a macOS endpoint protection profile](configure-endpoint-protection).

## FileVault

For more information about Apple FileVault settings, see [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) in the Apple developer content.

Important

As of macOS 10.15, FileVault configuration requires user approved MDM enrollment.

- **Enable FileVault**

    You can *enable* Full Disk Encryption using XTS-AES 128 with FileVault on devices that run macOS 10.13 and later.

    - **Not configured** (*default*)
    - **Yes**

    When *Enable FileVault* is set to *Yes*, a personal recovery key is generated for the device during encryption, and the following settings apply to that key:

    - **Escrow location description of personal recovery key**

        Specify a short message to the user that explains how and where they can retrieve their personal recovery key. This text is inserted into the message the user sees on their sign-in screen when prompted to enter their personal recovery key if a password is forgotten.
    - **Personal recovery key rotation**

        Specify how frequently the personal recovery key for a device will rotate. You can select the default of **Not configured**, or a value of **1** to **12** months.
    - **Hide recovery key**

        Choose to hide the personal key from a device user during FileVault 2 encryption.

        - **Not configured** (*default*) – The personal key is visible to the device user during encryption.
        - **Yes** - The personal key is hidden from the device user during encryption.

        After encryption, device users can view their personal recovery key for an encrypted macOS device from the following locations:

        - iOS/iPadOS company portal app
        - Intune app
        - company portal website
        - Android company portal app

        To view the key, from the app or website, go to device details of the encrypted macOS device and select *get recovery key*.
    - **Disable prompt at sign out**

        Prevent the prompt to the user that requests they enable FileVault when they sign out. When set to Disable, the prompt at sign-out is disabled and instead, the user is prompted when they sign in.

        - **Not configured** (*default*)
        - **Yes** - Disable the prompt at sign-out.
    - **Number of times allowed to bypass**

        Set the number of times a user can ignore prompts to enable FileVault before FileVault is required for the user to sign in.

        - **Not configured** - Encryption on the device is required before the next sign-in is allowed.
        - **0** - Require devices to encrypt the next time a user signs in to the device.
        - **1** to **10** - Allow a user to ignore the prompt from 1 to 10 times before requiring encryption on the device.
        - **No limit, always prompt** - The user is prompted to enable FileVault but encryption is never required.
        - **Disable** - Disables the feature.

        The default for this setting depends on the configuration of *Disable prompt at sign out*. When *Disable prompt at sign out* is set to **Not configured**, this setting defaults to **Not configured**. When *Disable prompt at sign out* is set to **Yes**, this setting defaults to **1** and a value of **Not configured** isn't an option.

## Firewall

Use the firewall to control connections per-application, rather than per-port. Using per-application settings makes it easier to get the benefits of firewall protection. It also helps prevent undesirable apps from taking control of network ports that are open for legitimate apps.

- **Enable Firewall**

    Turn use of Firewall on macOS and then configure how incoming connections are handled in your environment.

    - **Not configured** (*default*)
    - **Yes**
- **Block all incoming connections**

    Block all incoming connections except the connections required for basic Internet services, such as DHCP, Bonjour, and IPSec. This feature also blocks all sharing services, such as File Sharing and Screen Sharing. If you're using sharing services, then keep this setting as *Not configured*.

    - **Not configured** (*default*)
    - **Yes**

    When you set *Block all incoming connections* to *Not configured*, you can then configure which apps can or can't receive incoming connections.

    **Apps allowed**: Configure a list of apps that are allowed to receive incoming connections.

    - **Add apps by bundle ID**: Enter the *bundle ID* of the app.

        To get the app bundle ID:

        - Use the Terminal app and AppleScript: `osascript -e 'id of app "AppName"`.
        - Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT211833).
        - For apps added to Intune, [you can use the Intune admin center](../../app-management/collect-bundle-ids).
    - **Add store app**: Select a store app you previously added in Intune. For more information, see [Add apps to Microsoft Intune](../../app-management/deployment/).

    **Apps blocked**: Configure a list of apps that have incoming connections blocked.

    - **Add apps by bundle ID**: Enter the *bundle ID* of the app.

        To get the app bundle ID:

        - Use the Terminal app and AppleScript: `osascript -e 'id of app "AppName"`.
        - Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT211833).
        - For apps added to Intune, [you can use the Intune admin center](../../app-management/collect-bundle-ids).
    - **Add store app**: Select a store app you previously added in Intune. For more information, see [Add apps to Microsoft Intune](../../app-management/deployment/).
- **Enable stealth mode**

    To prevent the computer from responding to probing requests, enable stealth mode. The device continues to answer incoming requests for authorized apps. Unexpected requests, such as ICMP (ping), are ignored.

    - **Not configured** (*default*)
    - **Yes**

## Gatekeeper

- **Allow apps downloaded from these locations**

    Limit the apps a device can launch, depending on where the apps were downloaded from. The intent is to protect devices from malware, and allow apps from only the sources you trust.

    - **Not configured** (*default*)
    - **Mac App Store**
    - **Mac App Store and identified developers**
    - **Anywhere**
- **Do not allow user to override Gatekeeper**

    Prevents users from overriding the Gatekeeper setting, and prevents users from Control-clicking to install an app. When enabled, users can't Control-click any app to install it.

    - **Not configured** (*default*) - Users can Control-click to install apps.
    - **Yes** - Prevents users from using Control-click to install apps.