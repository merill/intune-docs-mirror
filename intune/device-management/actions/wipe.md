---
layout: Conceptual
title: Wipe devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/wipe
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.reviewer: mattcall
ms.subservice: remote-actions
zone_pivot_group_filename: device-management/actions/zone-pivot-groups.json
description: Learn how to wipe managed devices with Microsoft Intune, choose platform-specific reset options, and prepare devices for retirement, reuse, or recovery.
ms.date: 2026-09-16T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
zone_pivot_groups: c5fbc3ee-cfe5-494a-b441-d95cbed3128c
locale: en-us
document_id: 96caac9f-c89a-0447-4343-a82acb12a275
document_version_independent_id: 96caac9f-c89a-0447-4343-a82acb12a275
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/wipe.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/wipe
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/wipe.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: ca4779f7-13b6-8af3-c28d-c4fc6b93b64e
---

# Wipe devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Use the *Wipe* action in Intune to factory reset a device, restoring it to its default settings. This action removes all personal and organizational data, apps, and configurations. It's commonly used when a device needs to be retired, repurposed, reset for troubleshooting, or securely erased if lost or stolen.

Depending on the platform, you can customize the wipe behavior to meet your organization's needs.

Important

A tenant can submit up to 500 Wipe actions per day. This tenant-wide limit is cumulative across individual device actions, bulk device actions, and Microsoft Graph API requests. To request a limit change, [contact Microsoft support](../../fundamentals/it-pro-support/get-support-admin-center). For all device action limits, see [Daily tenant limits](./#daily-tenant-limits).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated (COSU)
> - Android Enterprise corporate-owned fully managed (COBO)
> - Android Enterprise corporate-owned work profile (COPE)
> - Android Open Source Project (AOSP)
> - ChromeOS
> - iOS/iPadOS
> - macOS
> - tvOS 10.2+
> - visionOS 1.1+
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Wipe**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

::: zone pivot="macos,android"

## Before wiping a device

::: zone-end

::: zone pivot="macos"

Review the requirements for erasing macOS devices available on [Apple's deployment guide for erasing devices](https://support.apple.com/guide/deployment/dep0a819891e).

::: zone-end

::: zone pivot="android"

### Factory Reset Protection (FRP) considerations

Whether a device requires Google account credentials after reset depends on ownership (Android Enterprise corporate-owned work profile/fully managed/dedicated), the reset method (Settings, Recovery, or admin wipe), and whether FRP is configured. By default, Intune's admin wipe doesn't preserve FRP data.

For more information, see [Factory reset protection emails setting isn't enforced after you reset an Android Enterprise device](/en-us/troubleshoot/mem/intune/device-configuration/factory-reset-protection-emails-not-enforced).

### Samsung devices

For Android Enterprise fully managed Samsung devices, make sure the **Factory Reset** setting under **Device Restrictions** isn't set to **Block**.

If **Factory Reset** is blocked and a **Wipe** action is initiated, the device loses contact with Intune and be unable to complete the factory reset.

### Zebra devices

On Zebra Android devices, the **Wipe** action is designed to remove only corporate data. It doesn't perform a factory reset.

To factory reset a Zebra Android device, use one of the following methods:

- [Use Zebra StageNow](https://techdocs.zebra.com/stagenow/5-17/profiles/wipedevice/)
- [Use OEM Config Data Wipe Configuration](https://techdocs.zebra.com/oemconfig/latest/mc2/)

::: zone-end

## How to wipe a device from the Intune admin center

::: zone pivot="android"

Important

To choose whether to remove eSIMs during a single-device wipe, use the new device view. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices), set **Preview new device view** to **On**, and then select the device.

::: zone-end

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remove data** &gt; **Wipe**.

::: zone pivot="android"

1. For Android Enterprise corporate-owned fully managed (COBO), corporate-owned dedicated (COSU), and corporate-owned work profile (COPE) devices, eSIMs are preserved by default. To remove the eSIMs during the wipe, select the option to remove eSIMs.
2. Select **Wipe**.

::: zone-end

::: zone pivot="macos"

1. Enter a 6-digit **Recovery PIN**. This PIN is required to reinstall the operating system on devices that don't have the T2 security chip—typically models from 2018 or earlier, or devices running macOS 10.14 or earlier. Make sure to record the PIN and share it with the device owner. The PIN won't be visible after the wipe completes.
2. Select an option from **Obliteration Behavior**, which is used to define the fallback for devices when Erase All Contents and Settings (EACS) fails. The following options can be configured:

    - **Default**: If Erase All Content and Settings (EACS) preflight fails, the device responds to Intune with an Error status and then attempts to erase itself. If EACS preflight succeeds but EACS fails, then the device attempts to erase itself.
    - **Do not obliterate**: If Erase All Content and Settings (EACS) preflight fails, the device responds to Intune with an Error status and doesn't attempt to erase itself. If EACS preflight succeeds but EACS fails, then the device doesn't attempt to erase itself.
    - **Obliterate with warning**: If Erase All Content and Settings (EACS) preflight fails, the device responds with a Success status and then attempts to erase itself. If EACS preflight succeeds but EACS fails, then the device attempts to erase itself.
    - **Always obliterate**: The system doesn't attempt Erase All Content and Settings (EACS). T2 and later devices always obliterate.
3. Select **Wipe** to erase the device.

::: zone-end

::: zone pivot="windows"

1. You can customize the wipe behavior with the following options:

    - **Wipe device, but keep enrollment state and associated user account**
        - Resets the device to factory settings, while preserving the user data, user accounts, and important settings. To learn more about what data is preserved, see [How push-button reset features work](/en-us/windows-hardware/manufacture/desktop/how-push-button-reset-features-work#keep-my-files).
        - MDM policies and settings are removed, but the device remains enrolled in Intune.
        - Uses the [doWipePersistUserData](/en-us/windows/client-management/mdm/remotewipe-csp#dowipepersistuserdata) CSP node.
    - **Wipe device, and continue to wipe even if device loses power**
        - Resets the device to factory settings, deleting all user data, settings, and MDM policies.
        - Overwrites the free space to prevent data recovery.
        - Ensures the wipe continues even if the device loses power, preventing interruption—ideal for high-security scenarios such as lost or stolen devices.
        - Uses the [doWipeProtected](/en-us/windows/client-management/mdm/remotewipe-csp#dowipeprotected) CSP node. 
            Important

            This option can prevent some devices from starting up again. The wipe process may interfere with boot recovery or firmware protections, leaving the device unrecoverable. Use only on corporate-owned devices where full data destruction is required and recovery procedures are in place.
    - **No options selected**
        - Resets the device to factory settings, deleting all user data, settings, and MDM policies.
        - If the wipe is interrupted, the device attempts to roll back to its previous state. If rollback fails, the device may become unusable and require a full Windows reinstallation.
        - Uses the [doWipe](/en-us/windows/client-management/mdm/remotewipe-csp#dowipe) CSP node.
2. To confirm the wipe, select **Wipe**.

::: zone-end

::: zone pivot="ios"

1. For iOS/iPadOS eSIM devices, the cellular data plan is preserved by default when you wipe a device. If you want to remove the data plan from the device when you wipe the device, select the **Also remove the devices data plan...** option.

::: zone-end

::: zone pivot="chromeos"

1. Select on of the following options:

    - **Remove user profiles only**: To remove all user account data. Device and enrollment policies remain on the device.
    - **Factory reset (powerwash)**: To restore a device to its factory state, removing all personal and work data. Before using this action, [deprovision](deprovision) the device. Otherwise, once it connects to Wi-Fi, it will automatically enroll again.

For more information about wiping ChromeOS devices, see [Wipe ChromeOS device data](https://support.google.com/chrome/a/answer/1360642).

::: zone-end

::: zone pivot="android"

## Wipe multiple Android Enterprise devices

Use a bulk device action to wipe up to 100 corporate-owned fully managed (COBO), corporate-owned dedicated (COSU), or corporate-owned work profile (COPE) devices. By default, the wipe preserves the devices' eSIM data plans.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices) &gt; [**Bulk device actions**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Devices/BulkActionWizardBlade).
2. On the **Basics** page, select **Android** for the operating system and **Wipe** for the device action.
3. To remove the eSIM data plans during the wipe, select the option to also remove the devices' data plans. If you don't select the option, the wipe preserves the data plans. Select **Next**.
4. On the **Devices** page, select up to 100 supported corporate-owned Android Enterprise devices. Select **Next**.
5. On the **Review + create** page, review the action, and then select **Create**.

::: zone-end

Note

This action might be governed by an Intune access policy that requires Multiple Administrative Approval (MAA). If so, a second administrator must approve the action before it can proceed.

For more information, see [Use access policies to require multiple administrative approvals](../../fundamentals/role-based-access-control/multi-admin-approval).

::: zone pivot="windows"

## Remove a device from Windows Autopilot

After executing the action on a device from Intune, you might also want to remove its registration from Windows Autopilot, if applicable.

For more information, see [Deregister from Windows Autopilot using Intune](/en-us/autopilot/registration-overview#deregister-from-windows-autopilot-using-intune).

::: zone-end

::: zone pivot="android,ios,macos,windows"

## Remove a device from Microsoft Entra ID

After executing the action on a device from Intune, you might also want to remove its record from Microsoft Entra ID to fully disconnect it from your organization's identity infrastructure. This step helps ensure that the device no longer appears in your tenant, avoids potential confusion in device inventory, and prevents lingering access permissions or stale records that could affect compliance or reporting.

For more information about removing devices from Microsoft Entra ID, see [Manage stale devices in Microsoft Entra ID](/en-us/entra/identity/devices/manage-stale-devices).

::: zone-end

## Reference links

- Microsoft Graph API: [wipe action](/en-us/graph/api/intune-devices-manageddevice-wipe)

::: zone pivot="windows"

- Configuration service provider (CSP) used to initiate the action: [RemoteWipe CSP](/en-us/windows/client-management/mdm/remotewipe-csp)

::: zone-end