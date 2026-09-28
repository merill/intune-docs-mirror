---
layout: Conceptual
title: View report details for encryption status of devices managed with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/monitor-encryption
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
description: Use the Microsoft Intune admin center to view reports for device encryption status across macOS FileVault and Windows BitLocker encrypted devices that you manage with Microsoft Intune.
ms.date: 2024-10-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: aanavath
locale: en-us
document_id: 7d463863-88f0-12d9-7725-a1ec1286e459
document_version_independent_id: 7d463863-88f0-12d9-7725-a1ec1286e459
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/monitor-encryption.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/monitor-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/monitor-encryption.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 1335ed2b-4936-20dc-d824-1046b549bb4f
---

# View report details for encryption status of devices managed with Microsoft Intune - Microsoft Intune | Microsoft Learn

The Microsoft Intune encryption report is a centralized location to view details about a device's encryption status and find options to manage device recovery keys. The recovery key options that are available depend on the type of device you're viewing.

Tip

To configure Intune policies to manage encryption on devices, see:

- [Manage BitLocker policy](../device-configuration/endpoint-security/encrypt-bitlocker-windows)
- [Manage FileVault policy](../device-configuration/endpoint-security/encrypt-filevault-macos)

To find the report, Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Select **Devices** &gt; **Manage devices** &gt; **Configuration**, select the *Monitor*\* tab, and then select **Device encryption status**.

## View encryption details

The encryption report shows common details across the supported devices you manage. The following sections provide details about the information that Intune presents in the report.

### Prerequisites

The encryption report supports reporting on devices that run the following operating system versions:

- macOS 10.13 or later
- Windows version 1607 or later

### Report details

The Encryption report pane displays a list of the devices you manage with high-level details about those devices. You can select a device from the list to drill-in and view more details from the devices Device encryption status pane.

- **Device name** – The name of the device.
- **OS** – The device platform, such as Windows or macOS.
- **OS version** – The version of Windows or macOS on the device.
- **TPM version***(applies to Windows only)* – The version of the Trusted Platform Module (TPM) chip detected on the Windows device.

    For more information on how we query the TPM version, see [DeviceStatus CSP - TPM Specification](/en-us/windows/client-management/mdm/devicestatus-csp#devicestatus-tpm-specificationversion).
- **Encryption readiness** – An evaluation of the devices readiness to support an applicable encryption technology, like BitLocker or FileVault encryption. Devices are identified as:

    - **Ready**: The device can be encrypted by using MDM policy, which requires the device meet the following requirements:

        **For macOS devices**:

        - macOS version 10.13 or later

        **For Windows devices**:

        - Windows 10 version 1709 or later of *Business*, *Enterprise*, *Education*, Windows 10 version 1809 or later of *Pro*, and Windows 11.
        - The device must have a TPM chip

        Important

        On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

        For more information on Windows prerequisites for encryption, see the [BitLocker configuration service provider (CSP)](/en-us/windows/client-management/mdm/bitlocker-csp) in the Windows documentation.
    - **Not ready**: The device doesn't have full encryption capabilities, but might still support encryption.
    - **Not applicable**: There isn't enough information to classify this device.
- **Encryption status** – Whether the OS drive is encrypted.
- **User Principal Name** – The primary user of the device.

### Device encryption status

When you select a device from the Encryption report, Intune displays the **Device encryption status** pane. This pane provides the following details:

- **Device name** – The name of the device you're viewing.
- **Encryption readiness** – An evaluation of the device's readiness to support encryption through the MDM policy based on an activated TPM.

    When a Windows device has a readiness of *Not ready*, it might still support encryption. To have the *Ready* designation, the Windows device must have a TPM chip activated. However, TPM chips aren't required to support encryption, as the device can still be manually encrypted. or through a MDM/Group Policy setting that can be set to allow encrypting without a TPM.
- **Encryption status** – Whether the OS drive is encrypted. It can take up to 24 hours for Intune to report on a device's encryption status or a change to that status. This time includes time for the OS to encrypt, plus time for the device to report back to Intune.

    To speed up the reporting of FileVault encryption status before device check-in normally occurs, have users sync their devices after encryption completes.

    For Windows devices, this field doesn't look at whether other drives, such as fixed drives, are encrypted. *Encryption status* is coming from [DeviceStatus CSP - DeviceStatus/Compliance/EncryptionCompliance](/en-us/windows/client-management/mdm/devicestatus-csp).
- **Profiles** – A list of the *Device configuration* profiles that apply to this device and are configured with the following values:

    - macOS:

        - Profile type = *Endpoint protection*
        - Settings &gt; FileVault &gt; FileVault = *Enable*
    - Windows:

        - Profile type = *Endpoint protection*
        - Settings &gt; Windows Encryption &gt; Encrypt devices = *Require*

    You can use the list of profiles to identify individual policies for review should the *Profile state summary* indicate problems.
- **Profile state summary** – A summary of the profiles that apply to this device. The summary represents the least favorable condition across the applicable profiles. For example, if only one out of several applicable profiles results in an error, the *Profile state summary* displays *Error*.

    To view more details of a status in the Intune admin center, go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; select the profile. Optionally, select **Device status** and then select a device.
- **Status details** – Advanced details about the device's encryption state.

    This field displays information for each applicable error that can be detected. You can use this information to understand why a device might not be encryption ready.

    The following are examples of the status details Intune can report:

    **macOS**:

    - The recovery key hasn't been retrieved and stored yet. Most likely, the device hasn't been unlocked, or it hasn't checked in.

        *Consider: This result doesn't necessarily represent an error condition but a temporary state that could be because of timing on the device where escrow for recovery keys must be set up before the encryption request is sent to the device. This status might also indicate the device remains locked or hasn't checked in with Intune recently. Finally, because FileVault encryption doesn't start until a device is plugged in (charging), it's possible for a user to receive a recovery key for a device that isn't yet encrypted*.
    - The user is deferring encryption or is currently in the process of encryption.

        *Consider: Either the user hasn't yet logged out after receiving the encryption request, which is necessary before FileVault can encrypt the device, or the user has manually decrypted the device. Intune can't prevent a user from decrypting their device.*
    - The device is already encrypted. Device user must decrypt the device to continue.

        *Consider: Intune can't set up FileVault on a device that is already encrypted. However, after a device receives policy to enable FileVault, a user can [upload their personal recovery key to enable Intune to then manage encryption on that device](../device-configuration/endpoint-security/encrypt-filevault-macos#assume-management-of-existing-filevault-encryption). Alternately, the user can manually decrypt their device so it can then be encrypted by Intune policy at a later time. However, we don't recommend manual decryption as doing so can leave a device unencrypted for a time.*
    - FileVault needs the user to approve their management profile in macOS Catalina and higher.

        *Consider: Beginning with macOS version 10.15 (Catalina), user approved enrollment settings can result in the requirement that users manually approve FileVault encryption. For more information, see [User Approved enrollment](../device-enrollment/apple/methods-macos) in the Intune documentation*.
    - Unknown.

        *Consider: One possible cause for an unknown status is that the device is locked and Intune can't start the escrow or encryption process. After the device is unlocked, progress can continue*.

    **Windows**:

    For Windows devices, Intune only shows *Status details* for devices that run the *Windows 10 April 2019 Update* or later, or Windows 11. *Status details* are coming from [BitLocker CSP - Status/DeviceEncryptionStatus](/en-us/windows/client-management/mdm/bitlocker-csp).

    - The BitLocker policy requires user consent to launch the BitLocker Drive Encryption Wizard to start encryption of the OS volume but the user didn't consent.
    - The encryption method of the OS volume doesn't match the BitLocker policy.
    - The policy BitLocker requires a TPM protector to protect the OS volume, but a TPM isn't used.
    - The BitLocker policy requires a TPM-only protector for the OS volume, but TPM protection isn't used.
    - The BitLocker policy requires TPM+PIN protection for the OS volume, but a TPM+PIN protector isn't used.
    - The BitLocker policy requires TPM+startup key protection for the OS volume, but a TPM+startup key protector isn't used.
    - The BitLocker policy requires TPM+PIN+startup key protection for the OS volume, but a TPM+PIN+startup key protector isn't used.
    - The OS volume is unprotected.

        *Consider: A BitLocker policy to encrypt OS drives was applied on the machine but encryption was suspended or didn't complete for the OS drive.*
    - Recovery key backup failed.

        *Consider: Check the devices Event log to see why the recovery key backup failed. You might need to run the **manage-bde** command to manually escrow recovery keys.*
    - A fixed drive is unprotected.

        *Consider: A BitLocker policy to encrypt fixed drives was applied on the machine but encryption was suspended or didn't complete for the fixed drive.*
    - The encryption method of the fixed drive doesn't match the BitLocker policy.
    - To encrypt drives, the BitLocker policy requires either the user to sign in as an Administrator or, if the device is joined to Microsoft Entra ID, the AllowStandardUserEncryption policy must be set to `1`.
    - Windows Recovery Environment (WinRE) isn't configured.

        *Consider: Need to run command line to configure the WinRE on separate partition; as that wasn't detected. For more information, see [REAgentC command-line options](/en-us/windows-hardware/manufacture/desktop/reagentc-command-line-options).*
    - A TPM isn't available for BitLocker, either because it isn't present, it's been made unavailable in the Registry, or the OS is on a removable drive.

        *Consider: The BitLocker policy applied to this device requires a TPM, but on this device, the BitLocker CSP detects that the TPM might be disabled at the BIOS level.*
    - The TPM isn't ready for BitLocker.

        *Consider: The BitLocker CSP sees that this device has an available TPM, but the TPM might need to be initialized. Consider running **intialize-tpm** on the machine to initialize the TPM.*
    - The network isn't available, which is required for recovery key backup.

## Export report details

While viewing the Encryption report pane, you can select **Export** to create a *.csv* file download of the report details. This report includes the high-level details from the *Encryption report* pane and *Device encryption status* details for each device you manage.

![Export details](media/monitor-encryption/export.png)

This report can be of use in identifying problems for groups of devices. For example, you might use the report to identify a list of macOS devices that all report *FileVault is already enabled by the user*, which indicates devices that must be manually decrypted before Intune can manage their FileVault settings.

## Manage recovery keys

For details on managing recovery keys, see the following Intune documentation:

macOS FileVault:

- [Retrieve personal recovery key](../device-configuration/endpoint-security/encrypt-filevault-macos#recovery-key-access-locations)
- [Rotate recovery keys](../device-configuration/endpoint-security/encrypt-filevault-macos#recovery-key-rotation)
- [Recover recovery keys](../device-configuration/endpoint-security/encrypt-filevault-macos#recovery-key-access-locations)

Windows BitLocker:

- [Rotate BitLocker recovery keys](../device-configuration/endpoint-security/encrypt-bitlocker-windows#rotate-bitlocker-recovery-keys)