---
layout: Conceptual
title: Linux device compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-linux-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- highpri
- highseo
- compliance
- sub-device-compliance
ms.subservice: protect
description: View the device compliance settings for Linux that you can manage with Microsoft Intune compliance policies.
ms.date: 2025-08-15T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: arnab
locale: en-us
document_id: eb6544dc-645d-4b0c-525d-46b2ce9dde2d
document_version_independent_id: eb6544dc-645d-4b0c-525d-46b2ce9dde2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/ref-linux-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/ref-linux-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/ref-linux-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 0f6e96dd-12a6-e979-b928-e49231216bd4
---

# Linux device compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

This article lists and describes the different compliance settings you can configure for Linux devices in Microsoft Intune.

For Linux, compliance settings are available from the [settings catalog](../../device-configuration/settings-catalog/) instead of from a predetermined template as seen for other platforms. Therefore, when configuring a compliance policy for Linux you choose the settings you want to include in your policy by browsing the catalog and selecting them.

Devices are also governed by tenant-wide [compliance policy settings](overview#compliance-policy-settings).

This feature applies to:

- Ubuntu Desktop 24.04 LTS or 26.04 LTS (physical or Hyper-V machine with x86/64 CPUs)
- RedHat Enterprise Linux 9
- RedHat Enterprise Linux 10

## Linux settings categories

Compliance policies for Linux can include settings from the following categories. Where applicable, guidance on configuring the setting is provided.

### Allowed distributions

Add entries that define a maximum and minimum OS version for a Linux distribution type.

Users of devices that fail to meet the defined criteria need to install a different version or distribution of Linux to bring the device into compliance.

### Custom compliance

Add the settings in this category when you use custom compliance settings for Linux.

For information about the available settings for custom compliance and how to use them, see [Use custom compliance policies and settings for Linux and Windows devices with Microsoft Intune](custom-settings).

### Device encryption

Add settings to manage disk encryption.

- **Require Device Encryption** – Specifies whether device-level encryption is required for writable fixed disks on this computer.

    Users of devices that aren't encrypted receive a message that they must encrypt the drives to bring the device into compliance.

    There are several options for disk and partition encryption on Linux operating systems. At this time, Intune recognizes any encryption system that uses the underlying [dm-crypt](https://gitlab.com/cryptsetup/cryptsetup/-/wikis/DMCrypt) subsystem that has been standard on Linux systems for some time.

    The preferred method of setting up dm-crypt is to use the LUKS format with the [cryptsetup](https://gitlab.com/cryptsetup/cryptsetup/) tool.

    Keep the following things in mind when configuring encryption:

    - Encrypting Linux system volumes after installation is possible, but potentially very time consuming. Microsoft recommends setting up disk encryption while installing the operating system.
    - Not all filesystem partitions need to be encrypted to meet organizational standards. The following are ignored:
        - Read-only partitions
        - Pseudo-filesystems like */proc* or *tmpfs*
        - The */boot* or */boot/efi* partitions

### Password policy

Enforce common password requirements for Linux devices:

- Minimum Lowercase - Specifies the minimum number of lowercase letters a password must contain.
- Minimum Uppercase - Specifies the minimum number of uppercase letters a password must contain.
- Minimum Symbols - Specifies the minimum number of symbols a password must contain.
- Minimum Length - Specifies the minimum number of total characters a password must contain.
- Minimum Digits - Specifies the minimum number of digits a password must contain.

Users that fail to meet password complexity requirements can receive a message that they must use a strong password to bring the device into compliance.

## Refresh compliance status

If you must modify a device's configuration, use one of the following methods to refresh the device compliance status with Intune after making changes:

- If the Microsoft Intune app is still running, on the apps *device details* page or the *compliance issues* page, select the **Refresh** link. The device starts a new check-in.
- If the Microsoft Intune app isn't running, start the app and sign in. Signing in starts a new check-in.
- By default, the Microsoft Intune app periodically uses a background task to check in while the computer is on and logged in.