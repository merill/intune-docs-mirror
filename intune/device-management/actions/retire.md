---
layout: Conceptual
title: 'Device Action: Retire - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/retire
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
description: Learn how to retire device using Microsoft Intune.
ms.date: 2026-08-06T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 51e33912-415a-402f-8201-8acebf3e4991
locale: en-us
document_id: 81f04860-d425-cf06-1a4b-4bd04b094872
document_version_independent_id: 81f04860-d425-cf06-1a4b-4bd04b094872
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/retire.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/retire
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/retire.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: dfcac6a5-6ab1-25d0-9a3a-9b37a017848d
---

# Device Action: Retire - Microsoft Intune | Microsoft Learn

The *retire* action in Intune removes company data from a device without performing a full wipe or factory reset. This action is ideal for personally owned devices or when transitioning a device out of organizational control. It unenrolls the device from Intune and removes managed apps, settings, and profiles deployed through mobile device management (MDM), while preserving personal data.

Unlike the **Wipe** action, which resets the device to factory settings, **Retire** keeps user content intact. The action is triggered the next time the device checks in with Intune. Until then, the device might still appear in the admin center. If you need to remove a device immediately, consider using the [delete device action](delete) instead.

Important

A tenant can submit up to 1,000 Retire actions per day. This tenant-wide limit is cumulative across individual device actions, bulk device actions, and Microsoft Graph API requests. To request a limit change, [contact Microsoft support](../../fundamentals/it-pro-support/get-support-admin-center). For all device action limits, see [Daily tenant limits](./#daily-tenant-limits).

::: zone pivot="windows"

## Before retiring or deleting a Microsoft Entra joined device

If you delete or retire the Intune object for a Microsoft Entra joined device that is protected by BitLocker, Intune triggers a sync that removes key protectors. This action suspends BitLocker on the OS volume as a safeguard to prevent unrecoverable encryption scenarios when the Entra object is deleted.

Before retiring a Microsoft Entra joined device, make sure to back up any critical data that may be lost during the process, such as:

- BitLocker recovery key
- Local administrator account credentials

::: zone-end

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android device administrator
> - Android Enterprise personally-owned work profile (BYOD)
> - iOS/iPadOS
> - macOS
> - tvOS
> - visionOS
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Retire**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to retire a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Retire**. To confirm, select **Yes**.

Note

This action might be governed by an Intune access policy that requires Multiple Administrative Approval (MAA). If so, a second administrator must approve the action before it can proceed.

For more information, see [Use access policies to require multiple administrative approvals](../../fundamentals/role-based-access-control/multi-admin-approval).

## User experience

When you use the **Retire** device action, the user's personal data isn't removed from the device.

::: zone pivot="ios"

The following table shows what data is removed and what remains on the device after the action is applied.

| Data type | iOS |
| --- | --- |
| Company apps and associated data installed by Intune | **Apps installed using Company Portal:** For apps that are pinned to the management profile, all app data and the apps are removed. These apps include apps originally installed from App Store and later managed as company apps unless the app is configured to not be uninstalled on device removal. **Microsoft apps that use App Protection Policies and were installed from App Store:** Intune triggers a selective wipe (see [Wipe only corporate data from apps](../../app-management/protection/wipe-corporate-data)) for apps protected by an App Protection Policy (see [App protection policies overview](../../app-management/protection/overview)) when a Retire action is initiated against an enrolled device. This wipe includes apps installed from the App Store that have work or school account data. The next time the app is launched, the selective wipe removes the protected work or school account data. In order for the selective wipe to occur, an App Protection Policy check-in must occur between the MDM enrollment and retire events. Personal app data and the apps aren't removed after a selective wipe. |
| Settings | Configurations set by Intune policy are no longer enforced. Users can change the settings. |
| Wi-Fi and VPN profile settings | Removed. |
| Certificate profile settings | Certificates are removed and revoked. |
| Management agent | The management profile is removed. |
| Email | Email profiles that are provisioned through Intune are removed. Cached email on the device is deleted. |
| Microsoft Entra device record | The Microsoft Entra ID record isn't removed. |

Note

Users that reinstall the Outlook Mobile app following a **Retire** device action might need to choose to **Delete All Saved Contacts** before re-exporting contacts to avoid duplicate contact entries. Previously exported contacts from Outlook Mobile are considered personal data and are not removed by the **Retire** device action.

::: zone-end

::: zone pivot="android"

### Android Enterprise personally owned devices with a work profile

Removing company data from an Android personally owned work profile device removes all data, apps, and settings in the work profile on that device.

### Android device administrator

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

The following table shows what data is removed and what remains on the device after the action is applied.

| Data type | Android | Android Samsung Knox Standard |
| --- | --- | --- |
| Web links | Removed. | Removed. |
| Unmanaged Google Play apps | Apps and data remain installed. Company app data that's protected by Mobile Application Management (MAM) encryption within the app local storage is removed. Data that's protected by MAM encryption outside the app remains encrypted and unusable, but isn't removed. | Apps and data remain installed. Company app data that's protected by Mobile Application Management (MAM) encryption within the app local storage is removed. Data that's protected by MAM encryption outside the app remains encrypted and unusable, but isn't removed. |
| Unmanaged line-of-business apps | Apps and data remain installed. | Apps are uninstalled and data that's local to the app is removed. No data that's outside the app (for example, on an SD card) is removed. |
| Managed Google Play apps | App data is removed. The app isn't removed. Data that's protected by Mobile Application Management (MAM) encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed. | App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted, but isn't removed. |
| Managed line-of-business apps | App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed. | App data is removed. The app isn't removed. Data that's protected by MAM encryption outside the app (for example, an SD card) remains encrypted and unusable, but isn't removed. |
| Settings | Configurations set by Intune policy are no longer enforced. Users can change the settings. | Configurations set by Intune policy are no longer enforced. Users can change the settings. |
| Wi-Fi and VPN profile settings | Removed. | Removed. |
| Certificate profile settings | Certificates are revoked but not removed. | Certificates are removed and revoked. |
| Management agent | Device Administrator privilege is revoked. | Device Administrator privilege is revoked. |
| Email | N/A (Android devices don't support Email profiles) | Email profiles that are provisioned through Intune are removed. Cached email on the device is deleted. |
| Microsoft Entra device record | The Microsoft Entra ID record is removed. | The Microsoft Entra ID record is removed. |

::: zone-end

::: zone pivot="macos"

The following table shows what data is removed and what remains on the device after the action is applied.

| Data type | macOS |
| --- | --- |
| Settings | Configurations set by Intune policy are no longer enforced. Users can change the settings. |
| Wi-Fi and VPN profile settings | Removed. |
| Certificate profile settings | Certificates are removed and revoked. |
| Management agent | The management profile is removed. |
| Outlook | If Conditional Access is enabled, the device doesn't receive new mail. |
| Microsoft Entra device record | The Microsoft Entra ID record isn't removed. |

::: zone-end

::: zone pivot="windows"

The following table shows what data is removed and what remains on the device after the action is applied.

| Data type | Windows |
| --- | --- |
| Company apps and associated data installed by Intune | - Apps are uninstalled-Sideloading keys are removed Microsoft 365 Apps aren't removed- Intune management extension installed Win32 apps aren't uninstalled on unenrolled devices. Admins can use assignment exclusion to not offer Win32 apps to BYOD Devices. |
| Settings | Configurations set by Intune policy are no longer enforced. Users can change the settings. |
| Wi-Fi and VPN profile settings | Removed. |
| Certificate profile settings | Certificates are removed and revoked. |
| Email | Removes email that's EFS-enabled including emails and attachments in the Mail app for Windows. Removes mail accounts provisioned by Intune |
| Microsoft Entra join status | - If the device is Microsoft Entra joined, the device is unjoined from Microsoft Entra.- If the device is Microsoft Entra registered, the work or school account is disconnected and the device is unregistered from Microsoft Entra ID. |
| Microsoft Entra device record | - If the device is registered in Autopilot, the Microsoft Entra ID record is not removed.- If the device is Microsoft Entra joined, the record is removed.- If the device is Microsoft Entra registered, the record is removed. |

For Microsoft Entra ID joined devices, after the **Retire** command is executed, you can't sign in wih a Microsoft Entra account. Follow the steps to [start your PC in Safe mode on the Microsoft Support site](https://support.microsoft.com/topic/1af6ec8c-4d4a-4b23-adb7-e76eef0b847f) to sign in with a local admin account and regain access to the user's local data.

::: zone-end

## Remove a device from Microsoft Entra ID

After executing the action on a device from Intune, you might also want to remove its record from Microsoft Entra ID to fully disconnect it from your organization's identity infrastructure. This step helps ensure that the device no longer appears in your tenant, avoids potential confusion in device inventory, and prevents lingering access permissions or stale records that could affect compliance or reporting.

For more information about removing devices from Microsoft Entra ID, see [Manage stale devices in Microsoft Entra ID](/en-us/entra/identity/devices/manage-stale-devices).

::: zone pivot="ios,macos"

## Remove an Apple ADE device from Apple Business Manager

After executing the action on an Apple Automated Device Enrollment (ADE) device in Intune, you might also need to release the device from Apple Business Manager to fully remove it from organizational control.

Follow these steps:

1. Go to http://business.apple.com, navigate to the **Devices** section, and search for the device using its serial number.
2. Select the device, opent the **...** menu, and the select **Release from Organization**.
3. Confirm the action by checking **I understand this cannot be undone**, and then select **Continue**.

Note

In some cases, the iOS device must be restored with iTunes to apply this change. Please find further instructions from Apple [here](https://support.apple.com/guide/itunes/restore-to-factory-settings-itnsdb1fe305/windows).

::: zone-end

## Reference links

- Microsoft Graph API: [retire action](/en-us/graph/api/intune-devices-manageddevice-retire)
- Configuration service provider (CSP) used to initiate the action: [RemoteWipe CSP](/en-us/windows/client-management/mdm/remotewipe-csp)