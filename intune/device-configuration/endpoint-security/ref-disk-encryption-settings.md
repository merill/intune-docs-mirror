---
layout: Conceptual
title: Intune endpoint security disk encryption policy settings - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-disk-encryption-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: View the list of settings that are available in Microsoft Intune endpoint security disk encryption policy settings for BitLocker and FileVault.
ms.date: 2024-08-19T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: aanavath
locale: en-us
document_id: 9d9b479d-3028-be69-c4cd-f8216d5f754d
document_version_independent_id: 9d9b479d-3028-be69-c4cd-f8216d5f754d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-disk-encryption-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-disk-encryption-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-disk-encryption-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 36442c0d-4ace-2221-a657-d3f513858161
---

# Intune endpoint security disk encryption policy settings - Microsoft Intune | Microsoft Learn

View the settings you can configure in profiles for *Disk Encryption* policy in the Endpoint security node of Intune as part of an [Endpoint security policy](manage-policies).

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

Beginning on June 19, 2023, the BitLocker profile for Windows was updated to use the settings format as found in the Settings Catalog. The new profile format includes the same settings as the older profile, but due to the new format, settings names in the Intune admin center have updated. With this change you can no longer create new versions of the old profile. Your existing instances of the old profile remain available to use and edit.

The settings details in this article apply only to BitLocker profiles created before June 19, 2023.

With the new profile format, we no longer publish a dedicated list of settings as found in the profile. Instead, use the *Learn more* link in the UI while viewing information for a setting, to open [BitLocker CSP](/en-us/windows/client-management/mdm/bitlocker-csp) in the Windows documentation, where the setting is detailed in full.

Applies to:

- macOS
- Windows

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Supported platforms and profiles:

- **macOS**:
    - Profile: **FileVault**
- **Windows**:
    - Profile: **BitLocker**

## FileVault

### Encryption

**Enable FileVault**

- **Not configured** (*default*)
- **Yes** - Enable Full Disk Encryption using XTS-AES 128 with FileVault on devices that run macOS 10.13 and later. FileVault is enabled when the user signs off of the device.

    When set to *Yes*, you can configure more settings for FileVault.

    - **Recovery key type***Personal key* recovery keys are created for devices. Configure the following settings for the personal key:

        - **Personal recovery key rotation** Specify how frequently the personal recovery key for a device will rotate. You can select the default of **Not configured**, or a value of **1** to **12** months.
        - **Escrow location description of personal recovery key** Specify a short message to the user that explains how they can retrieve their personal recovery key. The user sees this message on their sign in screen when prompted to enter their personal recovery key if a password is forgotten.
    - **Number of times allowed to bypass** Set the number of times a user can ignore prompts to enable FileVault before FileVault is required for the user to sign in.

        - **Not configured** (*default*) - Encryption on the device is required before the next sign-in is allowed.
        - **1** to **10** - Allow a user to ignore the prompt from 1 to 10 times before requiring encryption on the device.
        - **No limit, always prompt** - The user is prompted to enable FileVault, but encryption is never required.
    - **Allow deferral until sign out**

        - **Not configured** (*default*)
        - **Yes** - Defer the prompt to enable FileVault until the user signs out.
    - **Disable prompt at sign out** Prevent the prompt to the user that requests they enable FileVault when they sign out. When set to Disable, the prompt at sign-out is disabled and instead, the user is prompted when they sign in.

        - **Not configured** (*default*)
        - **Yes** - Disable the prompt to enable FileVault that appears at sign-out.
    - **Hide recovery key** Hide the personal recovery key from the user of the macOS device during encryption. After the disk is encrypted, a user can use any device to view their personal recovery key through the Intune Company Portal website, or company portal app on a supported platform.

        - **Not configured** (*default*)
        - **Yes** - Hide the personal recovery key during device encryption.

## BitLocker

Note

This article details the settings you can find in BitLocker profiles created before June 19, 2023, for the *Windows 10 and later* platform for endpoint security Disk encryption policy. On June 19, 2023, the *Windows 10 and later* profile was updated to use a new settings format as found in the Settings Catalog. With this change you can no longer create new versions of the old profile and they are no longer being developed. Although you can no longer create new instances of the older profile, you can continue to edit and use instances of it that you previously created.

For profiles that use the new settings format, Intune no longer maintains a list of each setting by name. Instead, the name of each setting, its configuration options, and its explanatory text you see in the Microsoft Intune admin center are taken directly from the settings authoritative content. That content can provide more information about the use of the setting in its proper context. When viewing a settings information text, you can use its *Learn more* link to open that content.

The following settings details for Windows profiles apply to those deprecated profiles.

### BitLocker – Base Settings

- **Enable full disk encryption for OS and fixed data drives** CSP: [BitLocker - RequireDeviceEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#requiredeviceencryption)

    If the drive was encrypted before this policy applied, no extra action is taken. If the encryption method and options match that of this policy, configuration should return success. If an in-place BitLocker configuration option doesn't match this policy, configuration will likely return an error.

    To apply this policy to a disk already encrypted, decrypt the drive and reapply the MDM policy. Windows default is to not require BitLocker drive encryption. However, on Microsoft Entra join and Microsoft Account (MSA) registration/login automatic encryption can apply enabling BitLocker at XTS-AES 128-bit encryption.

    - **Not configured** (*default*) - No BitLocker enforcement takes place.
    - **Yes** - Enforce use of BitLocker.
- **Require storage cards to be encrypted (mobile only)** CSP: [BitLocker - RequireStorageCardEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#requirestoragecardencryption)

    This setting only applies to Windows Mobile and Mobile Enterprise SKU devices.

    - **Not configured** (*default*) - The setting returns to the OS default, which is to not require storage card encryption.
    - **Yes** - Encryption on storage cards is required for mobile devices.

    Note

    Support for [Windows 10 Mobile](https://support.microsoft.com/help/4485197/windows-10-mobile-end-of-support-faq) and [Windows Phone 8.1](https://support.microsoft.com/help/4036480/windows-phone-8-1-end-of-support-faq) ended in August of 2020.
- **Hide prompt about third-party encryption** CSP: [BitLocker - AllowWarningForOtherDiskEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption)

    If BitLocker is enabled on a system that's already encrypted by a third-party encryption product, it might render the device unusable. Data loss can occur and you might need to reinstall Windows. It's highly suggested to never enable BitLocker on a device that has third-party encryption installed or enabled.

    By default, the BitLocker setup wizard prompts users to confirm that no third-party encryption is in place.

    - **Not configured** (*default*) – The BitLocker setup wizard displays a warning and prompts users to confirm no third-party encryption is present.
    - **Yes** - Hide the BitLocker setup wizards prompt from users.

    If BitLocker silent enable features are required, the third-party encryption warning must be hidden as any required prompt breaks silent enablement workflows.

    When set to *Yes*, you can then configure the following setting:

    - **Allow standard users to enable encryption during Autopilot** CSP: [BitLocker - AllowStandardUserEncryption](/en-us/windows/client-management/mdm/bitlocker-csp)

        - **Not configured** (*default*) – The setting is left as client default, which is to require local admin access to enable BitLocker.
        - **Yes** - During Microsoft Entra join silent enable scenarios, users don't need to be local administrators to enable BitLocker.

        For non-silent enablement and Windows Autopilot scenarios, the user must be a local admin to complete the BitLocker setup wizard.
- **Configure client-driven recovery password rotation** CSP: [BitLocker - ConfigureRecoveryPasswordRotation](/en-us/windows/client-management/mdm/bitlocker-csp)

    Add Work Account (AWA, formally Workplace Joined) devices aren't supported for key rotation.

    - **Not configured** (*default*) – The client won’t rotate BitLocker recovery keys.
    - **Disabled**
    - **Microsoft Entra joined devices**
    - **Microsoft Entra hybrid joined devices**

### BitLocker - Fixed Drive Settings

- **BitLocker fixed drive policy** CSP: [BitLocker - EncryptionMethodByDriveType](/en-us/windows/client-management/mdm/bitlocker-csp#encryptionmethodbydrivetype)

    - **Fixed drive recovery** CSP: [BitLocker - FixedDrivesRecoveryOptions](/en-us/windows/client-management/mdm/bitlocker-csp#fixeddrivesrecoveryoptions)

        Control how BitLocker-protected fixed data-drives are recovered in the absence of the required startup key information.

        - **Not configured** (*default*) - The default recovery options are supported including the data recovery agent (DRA). The end user can specify recovery options and recovery information isn't backed up to Microsoft Entra.
        - **Configure** – Enable access to configure various drive recovery techniques.

        When set to *Configure* the following settings are available:

        - **User creation of recovery key**

            - **Blocked** (*default*)
            - **Required**
            - **Allowed**
        - **Configure BitLocker recovery package**

            - **Password and Key** (*default*) - Include both the BitLocker recovery password that's used by admins and users to unlock protected drives, and recovery key packages that are used by admins for data recovery purposes in Active Directory.
            - **Password only** - The recovery key packages might not be accessible when needed.
        - **Require device to back up recovery information to Microsoft Entra**

            - **Not configured** (*default*) - BitLocker enablement will complete even if recovery key backup to Microsoft Entra ID fails. This can result in no recovery information being stored externally.
            - **Yes** - BitLocker won't complete enablement until recovery keys have been successfully saved to Microsoft Entra.
        - **User creation of recovery password**

            - **Blocked** (*default*)
            - **Required**
            - **Allowed**
        - **Hide recovery options during BitLocker setup**

            - **Not configured** (*default*) - Allow the user to access extra recovery options.
            - **Yes** - Block the end user from choosing extra recovery options such as printing recovery keys during the BitLocker setup wizard.
        - **Enable BitLocker after recovery information to store**

            - **Not configured** (*default*)
            - **Yes** - By setting this to *Yes*, BitLocker recovery information will be saved to Active Directory Domain Services.
        - **Block the use of certificate-based data recovery agent (DRA)**

            - **Not configured** (*default*) - Allow the use of DRA to be set up. Setting up DRA requires an enterprise PKI and Group Policy Objects to deploy the DRA agent and certificates.
            - **Yes** - Block the ability to use Data Recovery Agent (DRA) to recover BitLocker enabled drives.
    - **Block write access to fixed data-drives not protected by BitLocker** CSP: [BitLocker - FixedDrivesRequireEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#fixeddrivesrequireencryption) This setting is available when *BitLocker fixed drive policy* is set to *Configure*.

        - **Not configured** (*default*) - Data can be written to non-encrypted fixed drives.
        - **Yes** - Windows won't allow any data to be written to fixed drives that aren't BitLocker protected. If a fixed drive isn't encrypted, the user will need to complete the BitLocker setup wizard for the drive before write access is granted.
    - **Configure encryption method for fixed data-drives** CSP: [BitLocker - EncryptionMethodByDriveType](/en-us/windows/client-management/mdm/bitlocker-csp#encryptionmethodbydrivetype)

        Configure the encryption method and cipher strength for fixed data-drives disks. *XTS- AES 128-bit* is the Windows default encryption method and the recommended value.

        - **Not configured** (*default*)
        - **AES 128bit CBC**
        - **AES 256bit CBC**
        - **AES 128bit XTS**
        - **AES 256bit XTS**

### BitLocker - OS Drive Settings

- **BitLocker system drive policy** CSP: [BitLocker - EncryptionMethodByDriveType](/en-us/windows/client-management/mdm/bitlocker-csp#encryptionmethodbydrivetype)

    - **Configure** (*default*)
    - **Not configured**

    When set to *Configure* you can configure the following settings:

    - **Startup authentication required** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

        - **Not configured** (*default*)
        - **Yes** - Configure the additional authentication requirements at system startup, including the use of Trusted Platform Module (TPM) or startup PIN requirements.

        When set to *Yes* you can configure the following settings:

        - **Compatible TPM startup** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

            It's recommended to require a TPM for BitLocker. This setting only applies when first enabling BitLocker and has no effect if BitLocker is already enabled.

            - **Blocked** (*default*) - BitLocker doesn’t use the TPM.
            - **Required** - BitLocker enables only if a TPM is present and usable.
            - **Allowed** - BitLocker uses the TPM if it's present.
        - **Compatible TPM startup PIN** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

            - **Blocked** (*default*) - Block the use of a PIN.
            - **Required** - Require a PIN and TPM be present to enable BitLocker.
            - **Allowed** - BitLocker uses the TPM if it's present and allows a startup PIN to be configured by the user.

            For silent enable scenarios, you must set this to *Blocked*. Silent enable scenarios (including Windows Autopilot) won't be successful when user interaction is required.
        - **Compatible TPM startup key** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

            - **Blocked** (*default*) - Block the use of startup keys.
            - **Required** - Require a startup key and TPM be present to enable BitLocker.
            - **Allowed** - BitLocker uses the TPM if it's present and allows a startup key (such as a USB drive) be present to unlock the drives.

            For silent enable scenarios, you must set this to *Blocked*. Silent enable scenarios (including Windows Autopilot) won't be successful when user interaction is required.
        - **Compatible TPM startup key and PIN** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

            - **Blocked** (*default*) - Block the use of a startup key and PIN combination.
            - **Required** - Require BitLocker have a startup key and PIN present to become enabled.
            - **Allowed** - BitLocker uses the TPM if it's present and allows a startup key) and PIN combination.

            For silent enable scenarios, you must set this to *Blocked*. Silent enable scenarios (including Windows Autopilot) won't be successful when user interaction is required.
        - **Disable BitLocker on devices where TPM is incompatible** CSP: [BitLocker - SystemDrivesRequireStartupAuthentication](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrequirestartupauthentication)

            If no TPM is present, BitLocker requires a password or USB drive for startup.

            This setting only applies when first enabling BitLocker and has no effect if BitLocker is already enabled.

            - **Not configured** (*default*)
            - **Yes** - Block BitLocker from being configured without a compatible TPM chip.
        - **Enable preboot recovery message and url** CSP: [BitLocker - SystemDrivesRecoveryMessage](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrecoverymessage)configure

            - **Not configured** (*default*) – Use the default BitLocker pre-boot recovery information.
            - **Yes** – Enable the configuration of a custom pre-boot recovery message and URL to help your users understand how to find their recovery password. The pre-boot message and URL are seen by users when they're locked out of their PC in recovery mode.

            When set to *Yes* you can configure the following settings:

            - **Preboot recovery message** Specify a custom pre-boot recovery message.
            - **Preboot recovery url** Specify a custom pre-boot recovery URL.
        - **System drive recovery** CSP: [BitLocker - SystemDrivesRecoveryOptions](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesrecoveryoptions)

            - **Not configured** (*default*)
            - **Configure** - Enable the configuration of additional settings.

            When set to *Configure* the following settings are available:

            - **User creation of recovery key**

                - **Blocked** (*default*)
                - **Required**
                - **Allowed**
            - **Configure BitLocker recovery package**

                - **Password and Key** (*default*) - Include both the BitLocker recovery password that's used by admins and users to unlock protected drives, and recovery key packages that are used by admins for data recovery purposes) in Active Directory.
                - **Password only** - The recovery key packages might not be accessible when needed.
            - **Require device to back up recovery information to Microsoft Entra**

                - **Not configured** (*default*) - BitLocker enablement will complete even if recovery key backup to Microsoft Entra ID fails. This can result in no recovery information being stored externally.
                - **Yes** - BitLocker won't complete enablement until recovery keys have been successfully saved to Microsoft Entra.
            - **User creation of recovery password**

                - **Blocked** (*default*)
                - **Required**
                - **Allowed**
            - **Hide recovery options during BitLocker setup**

                - **Not configured** (*default*) - Allow the user to access extra recovery options.
                - **Yes** - Block the end user from choosing extra recovery options such as printing recovery keys during the BitLocker setup wizard.
            - **Enable BitLocker after recovery information to store**

                - **Not configured** (*default*)
                - **Yes** - By setting this to *Yes*, BitLocker recovery information will be saved to Active Directory Domain Services.
            - **Block the use of certificate-based data recovery agent (DRA)**

                - **Not configured** (*default*) - Allow the use of DRA to be set up. Setting up DRA requires an enterprise PKI and Group Policy Objects to deploy the DRA agent and certificates.
                - **Yes** - Block the ability to use Data Recovery Agent (DRA) to recover BitLocker enabled drives.
        - **Minimum PIN length** CSP: [BitLocker - SystemDrivesMinimumPINLength](/en-us/windows/client-management/mdm/bitlocker-csp#systemdrivesminimumpinlength)

            Specify the minimum startup PIN length when TPM + PIN is required during BitLocker enablement. The PIN length must be between 4 and 20 digits.

            If you don't configure this setting, users can configure a startup PIN of any length (between 4 and 20 digits)

            This setting only applies when first enabling BitLocker and has no effect if BitLocker is already enabled.
    - **Configure encryption method for Operating System drives** CSP: [BitLocker - EncryptionMethodByDriveType](/ https:/go.microsoft.com/fwlink?linkid=872526)

        Configure the encryption method and cipher strength for OS drives. *XTS- AES 128-bit* is the Windows default encryption method and the recommended value.

        - **Not configured** (*default*)
        - **AES 128bit CBC**
        - **AES 256bit CBC**
        - **AES 128bit XTS**
        - **AES 256bit XTS**

### BitLocker - Removable Drive Settings

- **BitLocker removable drive policy** CSP: [BitLocker - EncryptionMethodByDriveType](/en-us/windows/client-management/mdm/bitlocker-csp#encryptionmethodbydrivetype)

    - **Not configured** (*default*)
    - **Configure**

    When set to *Configure* you can configure the following settings.

    - **Configure encryption method for removable data-drives** CSP: [BitLocker - EncryptionMethodByDriveType](/en-us/windows/client-management/mdm/bitlocker-csp#encryptionmethodbydrivetype)

        Select the desired encryption method for removable data-drives disks.

        - **Not configured** (*default*)
        - **AES 128bit CBC**
        - **AES 256bit CBC**
        - **AES 128bit XTS**
        - **AES 256bit XTS**
    - **Block write access to removable data-drives not protected by BitLocker** CSP: [BitLocker - RemovableDrivesRequireEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#removabledrivesrequireencryption)

        - **Not configured** (*default*) - Data can be written to non-encrypted removable drives.
        - **Yes** - Windows doesn’t allow data to be written to removable drives that aren't BitLocker protected. If an inserted removable drive isn't encrypted, the user must complete the BitLocker setup wizard before write access is granted to drive.
    - **Block write access to devices configured in another organization** CSP: [BitLocker - RemovableDrivesRequireEncryption](/en-us/windows/client-management/mdm/bitlocker-csp#removabledrivesrequireencryption)

        - **Not configured** (*default*) - Any BitLocker encrypted drive can be used.
        - **Yes** - Block write access to removable drives unless they were encrypted on a computer owned by your organization.