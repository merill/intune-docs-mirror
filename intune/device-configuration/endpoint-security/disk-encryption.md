---
layout: Conceptual
title: Microsoft Intune endpoint security disk encryption policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/disk-encryption
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
description: Configure and deploy Microsoft Intune endpoint security policy disk encryption policies for BitLocker and FileVault.
ms.date: 2024-09-23T00:00:00.0000000Z
ms.topic: article
ms.reviewer: aanavath
locale: en-us
document_id: 0c619a58-c97a-30cd-0897-b72085563f09
document_version_independent_id: 0c619a58-c97a-30cd-0897-b72085563f09
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/disk-encryption.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/disk-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/disk-encryption.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d3b77d70-4e95-56f1-7520-2f5ecc4f30e5
---

# Microsoft Intune endpoint security disk encryption policy - Microsoft Intune | Microsoft Learn

Endpoint security Disk encryption profiles focus on only the settings that are relevant for a devices built-in encryption method, like FileVault, BitLocker, and Personal Data Encryption (for Windows). This focus makes it easy for security admins to manage disk encryption settings without having to navigate a host of unrelated settings.

While you can configure the same device settings by using *Endpoint Protection* profiles for device configuration, the device configuration profiles include other categories of settings. These other settings are unrelated to disk encryption and can complicate the task of configuring only disk encryption.

Find the endpoint security policies for disk encryption under *Manage* in the **Endpoint security** node of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

## Prerequisites for disk encryption policy

- **macOS** - macOS 10.13 or later
- **Windows** - Windows

## Role-based access controls (RBAC)

For guidance on assigning the right level of permissions and rights to manage Intune Disk encryption policy, see [Role-based access control for endpoint security](manage-policies#role-based-access-control-for-endpoint-security).

## Disk encryption profiles

**macOS profiles**:

- **FileVault** - FileVault provides built-in Full Disk Encryption for macOS devices.

    Manage [FileVault settings](ref-disk-encryption-settings#filevault) for macOS.

    To create a FileVault profile, see [Use FileVault disk encryption for macOS](encrypt-filevault-macos).

**Windows profiles**:

- **BitLocker** - BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers.

    Note

    Beginning on June 19, 2023, the BitLocker profile for Windows was updated to use the settings format as found in the Settings Catalog. The new profile format includes the same settings as the older profile. With this change you can no longer create new versions of the old profiles. Your existing instances of the old profile remain available to use and edit.

    With the new profile format, we no longer publish a dedicated list of settings as found in the profile. Instead, use the *Learn more* link in the UI while viewing information for a setting, to open [BitLocker CSP](/en-us/windows/client-management/mdm/bitlocker-csp) in the Windows documentation, where the setting is detailed in full.

    You can continue to find a list of settings in the original BitLocker profiles created before June 19, 2023, at [BitLocker settings](ref-disk-encryption-settings#bitlocker) in the Intune documentation.
- **Personal Data Encryption** - Personal Data Encryption (PDE) encrypts data at the folder level and is available for devices that run Windows 11 version 22H2 or later. PDE differs from BitLocker in that it encrypts files instead of whole volumes and disks. PDE occurs in addition to other encryption methods such as BitLocker. Unlike BitLocker that releases data encryption keys at boot, PDE doesn't release data encryption keys until a user signs in using Windows Hello for Business. PDE uses the [PDE CSP](/en-us/windows/client-management/mdm/personaldataencryption-csp).

    For more information about PDE, including prerequisites, related requirements, and recommendations, see the following articles in the Windows security documentation:

    - [PDE overview](/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption)
    - [Configure PDE](/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption/configure)
    - [PDE frequently asked questions (FAQ)](/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption/faq)

To create a BitLocker or Personal Data Encryption profile, see [Use disk encryption for Windows](encrypt-bitlocker-windows).

## Manage device encryption

After you deploy policy to encrypt a device disk, see the following articles for information on managing encryption:

- [Manage encryption on Windows](encrypt-bitlocker-windows)
- [Manage encryption on macOS](encrypt-filevault-macos#monitor-and-manage-filevault)
- [Monitor device encryption](monitor-encryption)