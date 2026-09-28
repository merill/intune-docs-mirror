---
layout: Conceptual
title: Windows shared device settings - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-shared-device-settings-windows
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
description: Add and use Windows 10/11 to configure devices that are shared, or used by multiple users in Microsoft Intune. See a list of all the settings and what they do on the devices, including Microsoft Surface. Control guest accounts, manage accounts and delete inactive accounts, allow or prevent saving to local storage, set power and sleep options, choose when updates are installed, and use devices in education environments in a device configuration profile.
ms.date: 2025-04-28T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 96ba5e43-e7db-a6b9-b824-191eff78ad5e
document_version_independent_id: 96ba5e43-e7db-a6b9-b824-191eff78ad5e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-shared-device-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-shared-device-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-shared-device-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: c444cdfc-f42f-2c53-cc95-10910a2bb600
---

# Windows shared device settings - Microsoft Intune | Microsoft Learn

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

Windows client devices, like the Microsoft Surface, can be used by many users. Devices that have multiple users are called shared devices, and are a part of mobile device management (MDM) solutions.

End users can sign in to these shared devices with a guest account. As they use the device, they only get access to features you allow. As the Intune administrator, you configure access, choose when accounts are deleted, control power management settings, and more for your shared Windows client devices.

This article describes some of the settings you can configure in an Intune device configuration profile. When the profile is created in Intune, you deploy or assign the profile to device groups in your organization. You can also assign this profile to device groups with mixed device types and Windows OS versions.

For more information on this feature in Intune, go to [Control access, accounts, and power features on shared PC or multi-user devices](configure-shared-device). For more information on the Windows CSP, go to [SharedPC CSP](/en-us/windows/client-management/mdm/sharedpc-csp).

## Before your begin

- Create a [Windows shared multi-user device configuration profile](configure-shared-device).

## Shared multi-user device settings

These settings use the [SharedPC CSP](/en-us/windows/client-management/mdm/sharedpc-csp).

- **Shared PC mode**: **Enable** turns on shared PC mode. In this mode, only one user signs in to the device at a time. Another user can't sign in until the first user signs out. When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Guest account**: Choose to create a Guest option on the sign-in screen. Guest accounts don't require any user credentials or authentication. This setting creates a new local account each time someone uses the device. Your options:

    - **Guest**: Only allows a local guest account to sign in to the device.
    - **Domain**: Only allows a Microsoft Entra domain account to sign in to the device.
    - **Guest and domain**: Allows a local guest account, or a Microsoft Entra domain account to sign in to the device.
- **Account management**: Choose if accounts are automatically deleted. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Enabled**: Accounts created by guests, and accounts in on-premises Active Directory and Microsoft Entra ID are automatically deleted from the devices. When a user signs off the device, or when system maintenance runs, these accounts are removed from the devices.

        Also enter:

        - **Account Deletion**: Choose when accounts are deleted:
            - **At storage space threshold**
            - **At storage space threshold and inactive threshold**
            - **Immediately after log-out**

        Also enter:

        - **Start delete threshold(%)**: Enter a percentage (0-100) of disk space. When the total disk/storage space drops below the value you enter, the cached accounts are deleted. It continuously deletes accounts to reclaim disk space. Accounts that are inactive the longest are deleted first.
        - **Stop delete threshold(%)**: Enter a percentage (0-100) of disk space. When the total disk/storage space meets the value you enter, the deleting stops.
        - **Inactive account threshold**: Enter the number of consecutive days before deleting the account that hasn't signed in, from 0-60 days.
    - **Disabled**: The local, Active Directory, and Microsoft Entra accounts created by guests stay on the device, and aren't deleted.
- **Local Storage**: With local storage, users can save and view files on the device's hard drive. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Enabled**: Allows users to see and save files locally using File Explorer.
    - **Disabled**: Prevents users from saving and viewing files on the device's hard drive.
- **Power Policies**: Allow or prevent users from changing the power settings. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Enabled**: Users can hibernate the device, can close the lid to sleep the device, and change the power settings.
    - **Disabled**: Users can't turn off hibernate, can't override all sleep actions (like closing the lid), and can't change the power settings.
- **Sleep time out (in seconds)**: Enter the number of inactive seconds (0-18000) before the device goes into sleep mode. `0` means the device never sleeps. If you don't set a time, the device goes to sleep after 3600 seconds (60 minutes).
- **Sign-in when PC wakes**: Choose if users must sign in after the device comes out of sleep mode. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Enabled**: Requires users to sign in with a password when device comes out of sleep mode.
    - **Disabled**: Users don't have to enter their username and password.
- **Maintenance start time (in minutes from midnight)**: Enter the time in minutes (0-1440) when automatic maintenance tasks, like Windows Update, run. The default start time is midnight, or zero (`0`) minutes. Change the start time by entering a start time in minutes from midnight. For example, if you want maintenance to begin at 2 AM, enter `120`. If you want maintenance to begin at 8 PM, enter `1200`.

    When set to **Not configured** (default), Intune doesn't change or update this setting.
- **Education policies**: Choose if policies for education environment are enabled. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Enabled**: Uses the recommended settings for devices used in schools, which are more restrictive.
    - **Disabled**: The default and recommended education policies aren't used.

    To learn more, see:

    - [Shared PC technical reference - SetEDUPolicy](/en-us/windows/configuration/shared-pc/shared-pc-technical#setedupolicy)
    - [SetEduPolicies CSP](/en-us/windows/client-management/mdm/sharedpc-csp#setedupolicies)
    - [Common Education device restrictions](../../solutions/education/tutorial-school-deployment/ref-device-restrictions-settings-windows)

Tip

[Set up a shared or guest PC](/en-us/windows/configuration/set-up-shared-or-guest-pc) (opens another docs web site) is a great resource on this Windows client feature, including concepts and group policies that can be set in shared mode.