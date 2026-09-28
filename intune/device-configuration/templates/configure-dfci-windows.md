---
layout: Conceptual
title: Update Windows BIOS features using DFCI MDM policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-dfci-windows
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
description: Learn more about the Device Firmware Configuration Interface (DFCI) profile to manage UEFI settings in Microsoft Intune. To use DFCI profiles, create Microsoft Entra security groups, the Windows Autopilot deployment profile, and the Enrollment State Page profile.
ms.date: 2026-06-23T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: madakeva
locale: en-us
document_id: 1ca80d4a-564f-85e5-4a84-8ebbd3686157
document_version_independent_id: 1ca80d4a-564f-85e5-4a84-8ebbd3686157
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-dfci-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-dfci-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-dfci-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7223a3c2-b75e-ac7c-4c49-4500680f4d99
---

# Update Windows BIOS features using DFCI MDM policies - Microsoft Intune | Microsoft Learn

When you use Intune to manage Windows Autopilot devices, you can manage UEFI (BIOS) settings after enrollment by using the Device Firmware Configuration Interface (DFCI). For an overview of benefits, scenarios, and prerequisites, see [Overview of DFCI](https://microsoft.github.io/mu/dyn/mu_feature_dfci/DfciPkg/Docs/Dfci_Feature/).

DFCI enables Windows to pass management commands from Intune to UEFI (Unified Extensible Firmware Interface).

In Intune, use this feature to control BIOS settings. Typically, firmware is more resilient to malicious attacks. It limits end users' control over the BIOS, which is good in a compromised situation.

This feature applies to:

- Windows on supported UEFI

For example, you use Windows client devices in a secure environment, and want to disable the camera. You can disable the camera at the firmware layer, so it doesn't matter what the end user does. Reinstalling the OS or wiping the computer won't turn the camera back on. In another example, lock down the boot options to prevent users from booting up another OS, or an older version of Windows that doesn't have the same security features.

When you reinstall an older Windows version, install a separate OS, or format the hard drive, you can't override DFCI management. This feature can prevent malware from communicating with OS processes, including elevated OS processes. DFCI's trust chain uses public key cryptography, and doesn't depend on local UEFI (BIOS) password security. This layer of security blocks local users from accessing managed settings from the device's UEFI (BIOS) menus.

Tip

For Dell devices, you can create a **BIOS configurations** policy. For more information, see [Use BIOS configuration profiles on Windows devices in Microsoft Intune](configure-bios-windows).

## Prerequisites

- The device manufacturer must add DFCI to their UEFI firmware during the manufacturing process or provide it as a firmware update that you install. Work with your device vendors to determine [the manufacturers that support DFCI](https://microsoft.github.io/mu/dyn/mu_feature_dfci/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) or the firmware version needed to use DFCI.
- A [Microsoft Cloud Solution Provider (CSP) partner](https://partner.microsoft.com/cloud-solution-provider) must register the device for Windows Autopilot, or the OEM can register the device directly.

    You can't use DFCI with devices manually registered for Windows Autopilot, such as [imported from a csv file](/en-us/autopilot/add-devices#add-devices). By design, DFCI management requires external attestation of the device's commercial acquisition through an OEM or a Microsoft CSP partner registration to Windows Autopilot.

    Once you register your device, its serial number appears in the list of Windows Autopilot devices.

    For more information on Windows Autopilot, including any requirements, see [Windows Autopilot registration overview](/en-us/autopilot/registration-overview).

## Create your Microsoft Entra security groups

Assign Windows Autopilot deployment profiles to Microsoft Entra security groups. Be sure to create groups that include your DFCI-supported devices. For DFCI devices, most organizations might create device groups instead of user groups. Consider the following scenarios:

- Human Resources (HR) have different Windows devices. For security reasons, you don't want anyone in this group to use the camera on the devices. In this scenario, you can create an HR security users group so the policy applies to users in the HR group, whatever the device type.
- On the manufacturing floor, you have 10 devices. On all devices, you want to prevent booting the devices from a USB device. In this scenario, you can create a security devices group, and add these 10 devices to the group.

For more information on creating groups in Intune, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).

## Create the profiles

To use DFCI, create the following profiles, and assign them to your group.

### Step 1 - Create a Windows Autopilot deployment profile

This profile sets up and preconfigures new devices. The following article lists the steps to create the profile:

- [Windows Autopilot deployment profile](/en-us/autopilot/profiles)

### Step 2 - Create an Enrollment State Page profile

This profile ensures that devices are verified and enabled for DFCI during the Windows setup. Use this profile to block device use until all apps and profiles are installed.

The following article lists the steps to create the profile:

- [Enrollment State Page profile](../../device-enrollment/windows/setup-status-page)

### Step 3 - Create the DFCI profile in Intune

This profile includes the DFCI settings you configure.

Tip

Configuring and assigning DFCI profiles can lock the device beyond repair. So, pay attention to the values you configure.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Device Firmware Configuration Interface**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your policies so you can easily identify them later. For example, a good profile name is **Windows - DFCI settings on Windows devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

    Select **Next**.
6. In **Configuration settings**, configure the settings you want to control in the UEFI firmware layer. For a list of all the settings, and what they do, go to:

    - [Windows DFCI settings](ref-dfci-settings-windows)

    Select **Next**.
7. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags). Select **Next**.
8. In **Assignments**, select the users or user group that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile). Select **Next**.
9. In **Review + create**, review your settings and select **Create**. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.

## Assign the profiles and reboot

[Assign](../assign-device-profile) the profiles to your Microsoft Entra security groups that include your DFCI devices. You can assign the profile when you create it or after.

When the device runs Windows Autopilot, during the Enrollment Status page, DFCI might force a reboot. This first reboot enrolls UEFI to Intune.

If you want to confirm the device is enrolled, you can reboot the device again, but it's not required. Use the device manufacturer's instructions to open the UEFI menu, and confirm UEFI is now managed.

The next time the device syncs with Intune, Windows receives the DFCI settings. Reboot the device. This third reboot is required for UEFI to receive the DFCI settings from Windows.

## Update existing DFCI settings

You can change existing DFCI settings on devices that are in use. In your existing DFCI profile, change the settings, and save your changes. Since the profile is already assigned, the new DFCI settings take effect when:

1. The device checks in with the Intune service to review profile updates. Check-ins happen at various times. For more information, see [when devices get a policy, profile, or app updates](../troubleshoot-device-profiles#policy-refresh-intervals).
2. To enforce the new settings, reboot the device [remotely](../../device-management/actions/restart) or locally.

You can also [signal devices to check in](../../device-management/actions/sync). After a successful sync, [signal to reboot](../../device-management/actions/restart).

Note

Deleting the DFCI profile, or removing a device from the group assigned to the profile doesn't remove DFCI settings or re-enable the UEFI (BIOS) menus. To stop using DFCI, update the settings in your existing DFCI profile. For more information on the steps, see retire the device in this article.

## Conflicts

When you create the DFCI policy, you configure the [Windows DFCI settings](ref-dfci-settings-windows) you want to manage.

Some settings are in a logical category, like **Microphones and Speakers**. There's also granular settings, like **Microphones**. If these settings conflict, the following happens:

- In the first sync attempt, the granular setting is applied (Microphones) and the category setting is noncompliant (Microphones and Speakers).
- With every sync with the Intune service after the first sync, the following behavior happens in a loop:

    - Intune applies the category setting (Microphones and Speakers) since it's not compliant. The granular setting (Microphones) becomes noncompliant.
    - Intune applies the granular setting (Microphones) since it's not compliant. The category setting (Microphones and Speakers) becomes noncompliant.

To avoid this looping behavior, configure the category setting **or** the granular settings.

For example, you want to only allow Wi-Fi radios. In this scenario, you:

- Leave the category **Radios (Bluetooth, Wi-Fi, NFC, etc.)** setting to **Not configured**.
- For the **Wi-Fi** radio setting, set it to **Enable**.
- Set all the other granular radio settings to **Disabled**.

## Reuse, retire, or recover the device

### Reuse

If you plan to reset Windows to repurpose the device, then [wipe the device](../../device-management/actions/wipe). Do **not** remove the Windows Autopilot device record.

After wiping the device, move the device to the group assigned the new DFCI and Windows Autopilot profiles. Reboot the device to rerun Windows setup.

### Retire

When you're ready to retire the device and release it from management, update the DFCI profile to the UEFI (BIOS) settings you want at the exit state. Typically, you want all settings enabled. For example:

1. In the Intune admin center, open your DFCI profile (**Devices** &gt; **Manage devices** &gt; **Configuration**).
2. Change the **Allow local user to change UEFI (BIOS) settings** to **Only not configured settings**.
3. Set all other settings to **Not configured**.
4. Save your settings.

These steps unlock the device's UEFI (BIOS) menus. The values remain the same as the profile (**Enabled** or **Disabled**), and aren't set back to any default OS values.

You're now ready to wipe the device. Once the device is wiped, delete the Windows Autopilot record. Deleting the record prevents the device from automatically re-enrolling when it reboots.

Tip

To remove Surface devices from DFCI enrollment, go to [removing DFCI management](/en-us/surface/surface-manage-dfci-guide#removing-dfci-management).

### Recover

If you wipe a device, and delete the Windows Autopilot record before unlocking the UEFI (BIOS) menus, the menus remain locked. Intune can't send profile updates to unlock it.

To unlock the device, open the UEFI (BIOS) menu, and refresh management from network. Recovery unlocks the menus, but leaves all UEFI (BIOS) settings set to the values in the previous Intune DFCI profile.

## End user impact

When the DFCI policy is applied, local users can't change settings configured by DFCI, even if the UEFI (BIOS) menu is password protected. Depending on the settings you configure, end users might receive errors that hardware components aren't found, or can't be diagnosed. Provide documentation to end users explaining the options you disabled.