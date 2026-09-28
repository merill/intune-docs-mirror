---
layout: Conceptual
title: Client event logs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/client-event-logs
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: A technical reference for the possible BitLocker (MBAM) client entries in the Windows event log
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 380585e6-836f-7ee3-64ca-fba20b81c7bb
document_version_independent_id: 3f140f42-261c-b73d-86c2-bac7808827ca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/tech-ref/bitlocker/client-event-logs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/tech-ref/bitlocker/client-event-logs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/tech-ref/bitlocker/client-event-logs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 8ad78847-ba20-c95f-332b-fd52238f3ffa
---

# Client event logs - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

On a Configuration Manager client to which you deploy a BitLocker management policy, use the Windows Event Viewer to view BitLocker client event logs. Go to **Applications and Services Logs**, **Microsoft**, **Windows**, **MBAM** for both Admin and Operational event logs.

## Admin

### 2: VolumeEnactmentFailed

An error occurred while applying MBAM policies.

#### Error code: -2144272219

Details: BitLocker Drive Encryption only supports Used Space Only encryption on thin provisioned storage.

This error occurs if you try to use BitLocker to encrypt a virtual machine that's running Windows 10 version 1803 or earlier. Earlier versions of Windows 10 don't support full disk encryption. BitLocker management policies enforce full disk encryption.

#### Error code: -2147024774

Details: The data area passed to a system call is too small.

To resolve this issue, restart the computer.

### 4: TransferStatusDataFailed

An error occurred while sending encryption status data.

### 8: SystemVolumeNotFound

The system volume is missing. SystemVolume is needed to encrypt the operating system drive.

### 9: TPMNotFound

The TPM hardware is missing. TPM is needed to encrypt the operating system drive with any TPM protector.

### 10: MachineHWExempted

The computer is exempted from Encryption. Machine's hardware status: Exempted

### 11: MachineHWUnknown

The computer is exempted from encryption. Machine's hardware status: Unknown

### 12: HWCheckFailed

Hardware exemption check failed.

### 13: UserIsExempted

The user is exempt from encryption.

### 14: UserIsWaiting

The user requested an exemption.

### 15: UserExemptionCheckFailed

User exemption check failed.

### 16: UserPostponed

The user postponed the encryption process.

### 17: TPMInitializationFailed

TPM initialization failed. The user rejected the BIOS changes.

### 18: CoreServiceDown

Unable to connect to the MBAM Recovery and Hardware service.

#### Error code: -2147024809

Details: The parameter is incorrect.

This error occurs if the website isn't HTTPS, or the client doesn't have a PKI cert.

### 20: PolicyMismatch

The BitLocker management policy is in conflict or corrupt.

### 21: ConflictingOSVolumePolicies

Detected OS volume encryption policies conflict. Check BitLocker policies related to OS drive protectors.

### 22: ConflictingFDDVolumePolicies

Detected fixed data drive volume encryption policies conflict. Check BitLocker policies related to fixed data drive protectors.

### 27: EncryptionFailedNoDra

An error occurred while encrypting. A data recovery agent (DRA) protector is required in FIPS mode for pre-Windows 8.1 machines.

### 34: TpmLockOutResetFailed

Failed to reset TPM lockout.

### 36: TpmOwnerAuthRetrievalFailed

Failed to retrieve TPM OwnerAuth from MBAM services.

### 37: WmiProviderDllSearchPathUpdateFailed

Failed to update the DLL search path for WMI provider.

### 38: TimedOutWaitingForWmiProvider

Agent stopping. Timed-out waiting for MBAM WMI provider instance.

## Operational

### 1: VolumeEnactmentSuccessful

The BitLocker management policies were applied successfully.

### 3: TransferStatusDataSuccessful

The encryption status data was sent successfully.

### 19: CoreServiceUp

Successfully connected to the MBAM Recovery and Hardware service.

### 28: TpmOwnerAuthEscrowed

The TPM OwnerAuth is escrowed.

### 29: RecoveryKeyEscrowed

The BitLocker recovery key for the volume is escrowed.

### 30: RecoveryKeyReset

The BitLocker recovery key for the volume is updated.

### 31: EnforcePolicyDateSet

The enforce policy date...is set for the volume

### 32: EnforcePolicyDateCleared

The enforce policy date...has been cleared for the volume.

### 33: TpmLockOutResetSucceeded

Successfully reset TPM lockout.

### 35: TpmOwnerAuthRetrievalSucceeded

Successfully retrieved TPM OwnerAuth from MBAM services.

### 39: RemovableDriveMounted

Removable drive was mounted.

### 40: RemovableDriveDismounted

Removable drive was unmounted.

### 41: FailedToEnactEndpointUnreachable

Failure to connect to the MBAM Recovery and Hardware service prevented BitLocker management policies from being applied successfully to the volume.

### 42: FailedToEnactLockedVolume

Locked volume state prevented BitLocker management policies from being applied successfully to the volume.

### 43: TransferStatusDataFailedEndpointUnreachable

Failure to connect to the MBAM Compliance and Status service prevented the transfer of encryption status data.