---
layout: Conceptual
title: Windows Hello for Business settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/identity-protection/ref-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: View details for Windows Hello for Business settings you configure in an Intune identity protection profile for device groups in Intune.
ms.date: 2024-07-09T00:00:00.0000000Z
ms.topic: reference
ms.collection:
- M365-identity-device-management
- identity-protection
- sub-secure-endpoints
ms.reviewer: mattcall
locale: en-us
document_id: 7ce3baad-3d9f-fab4-cfbf-25d0cb2b663a
document_version_independent_id: 7ce3baad-3d9f-fab4-cfbf-25d0cb2b663a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/identity-protection/ref-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/identity-protection/ref-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/identity-protection/ref-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/798bd9d1-9cc5-4fc7-b0e5-8699d1f6ce2a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b5dc5f65-34a8-4bfc-9917-97d1e20c88b2
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f44dbe1f-44e1-ad3b-82d8-2abbaa5884d9
---

# Windows Hello for Business settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

In July 2024, the following Intune profiles for identity protection and account protection were deprecated and replaced by a new consolidated profile named *Account protection*. This newer profile is found in the account protection policy node of endpoint security, and is the only profile template that remains available to create new policy instances for identity and account protection. The settings from this new profile are also available through the settings catalog.

Any instances of the following older profiles that you have created remain available to use and edit:

- **Identity protection** – previously available from *Devices* &gt; *Configuration* &gt; *Create* &gt; *New Policy* &gt; *Windows 10 and later* &gt; *Templates* &gt; *Identity Protection*
- **Account protection (Preview)** – previously available from *Endpoint Security* &gt; *Account protection* &gt; *Windows 10 and later* &gt; *Account protection ( Preview)*

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../../device-configuration/settings-catalog/).

This article describes Windows Hello for Business settings you can manage with an Identity protection profile. Identity protection profiles are part of device configuration policy in Microsoft Intune. However, as of July 2024, device configuration profiles for *Identity protection* are replaced by endpoint security profiles for *Account protection*. While you can continue to use identity protection profiles that you previously created, Intune no longer supports creating new instances. Instead, to manage settings for identity protection, use an endpoint security [account protection policy](../../device-configuration/endpoint-security/account-protection).

With an Identity protection profile, you can configure settings on discrete groups of Windows devices. To configure Windows Hello for Business tenant-wide, as part of *device enrollment*, see [Create a Windows Hello for Business policy](configure-tenant-wide-policy) in *Integrate Windows Hello for Business with Microsoft Intune*.

This article describes the settings for the enrollment policy.

You can find additional information about these settings in [Configure Windows Hello for Business Policy settings](/en-us/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings), in the Windows Hello documentation.

## Windows Hello for Business

*The following settings details apply only to the device configuration profile template for Identity protection, which was deprecated in July 2024.*

- **Configure Windows Hello for Business**:

    - **Not configured** (*default*) - Select this setting if you don't want to use Intune to control Windows Hello for Business settings. Any existing Windows Hello for Business settings on Windows devices isn't changed. All other settings on the pane are unavailable.
    - **Disable** - If you don't want to use Windows Hello for Business, select this setting. All other settings on the screen are then unavailable.
    - **Enable** - Select this setting if you want to configure Windows Hello for Business settings.

    When set to *Enable*, the following settings are available:

    - **Minimum PIN length** Specify a minimum PIN length for devices, from 4 to 127 characters. By default, this setting is *Not configured*.
    - **Maximum PIN length** Specify a maximum PIN length for devices, from four to 127 characters. By default, this setting is *Not configured*.
    - **Lowercase letters in PIN** If required, user PIN must include at least one lowercase letter. By default, this setting is *Not configured*.

        - **Not allowed** - Block users from using lowercase letters in the PIN. This behavior also occurs if the setting isn't configured.
        - **Allowed** - Allow users to use lowercase letters in the PIN, but it's not required.
        - **Required** - Users must include at least one lowercase letter in the PIN. For example, it's common practice to require at least one uppercase letter and one special character.
    - **Uppercase letters in PIN** If required, user PIN must include at least one uppercase letter. By default, this setting is *Not configured*.

        - **Not allowed** - Block users from using uppercase letters in the PIN. This behavior also occurs if the setting isn't configured.
        - **Allowed** - Allow users to use uppercase letters in the PIN, but it's not required.
        - **Required** - Users must include at least one uppercase letter in the PIN. For example, it's common practice to require at least one uppercase letter and one special character.
    - **Special characters in PIN** If required, user PIN must include at least one special character. Special characters include: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`

        - **Not allowed** (*default*) - Block users from using special characters in the PIN. This behavior also occurs if the setting isn't configured.
        - **Allowed** - Allow users to use uppercase letters in the PIN, but it's not required.
        - **Required** - Users must include at least one uppercase letter in the PIN. For example, it's common practice to require at least one uppercase letter and one special character.
    - **PIN expiration (days)** If configured, the user will be forced to change their PIN after the set number of days. The user can still proactively change their PIN before expiration. By default, this setting is *Not configured*.
    - **Remember PIN history** If configured, the user will not be able to reuse this number of previous PINs. By default, this setting is *Not configured*.
    - **Enable PIN recovery** Allows user to use the Windows Hello for Business PIN recovery service.

        - **Enable** - The PIN recovery secret is stored on the device and the user can change their PIN if needed.
        - **Not configured** (*default*) - The recovery secret isn't created or stored.
    - **Use a Trusted Platform Module (TPM)** A TPM chip provides an additional layer of data security.

        - **Enable** - Only devices with an accessible TPM can provision Windows Hello for Business.
        - **Not configured** (*default*) - Devices first attempt to use a TPM. If a TPM isn't available, they can use software encryption.
    - **Allow biometric authentication** If allowed, Windows Hello for Business can authenticate using gestures, such as face and fingerprint. Users must still configure a PIN in case of failure.

        - **Enable** - Windows Hello for Business allows biometric authentication.
        - **Not configured** (*default*) - Windows Hello for Business prevents biometric authentication (for all account types).
    - **Use enhanced anti-spoofing, when available** If enabled, devices use enhanced anti-spoofing, when available (for example, detecting a photograph of a face instead of a real face).

        - **Enable** - Windows requires all users to use anti-spoofing for facial features when that is supported.
        - **Not configured** (*default*) - Windows honors the anti-spoofing configurations on the device.
    - **Certificate for on-premise resources**

        - **Enable** - Allows Windows Hello for Business to use certificates to authenticate to resources on-premises.
        - **Not configured** (*default*) - Prevents Windows Hello for Business from using certificates to authenticate to resources on-premises. Instead, devices use the default behavior of *key-trust on-premises authentication*. For more information, see [User certificate for on-premises authentication](/en-us/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) in the Windows Hello documentation.
- **Use security keys for sign-in** This setting is available for devices that run Windows 10 version 1903 or later, or Windows 11. Use it to manage support for using Windows Hello security keys for sign-in.

    - **Enable** - Users can use a Windows Hello security key as a sign-in credential for PCs targeted with this policy.
    - **Not configured** - Security keys are disabled and users can't use them to sign in to PCs.

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.