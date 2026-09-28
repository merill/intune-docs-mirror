---
layout: Conceptual
title: Manage devices with on-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/wipe-lock-reset-devices
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
description: Protect device data with full wipe, selective wipe, remote lock, or passcode reset by using Configuration Manager on-premises mobile device management (MDM).
ms.date: 2018-08-14T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 27b8f349-8eaf-1d98-7962-6b6cc88c80e0
document_version_independent_id: a86da78e-d8c7-9986-b4e9-e4b3cbb891c9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/wipe-lock-reset-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/wipe-lock-reset-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/wipe-lock-reset-devices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 14051dd4-4bff-1c78-6ef5-64da8bf725c5
---

# Manage devices with on-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Mobile devices can store sensitive data and provide easy access to many organizational resources. To help protect devices and data, use Configuration Manager for the following device management actions:

- **Full wipe**: Restore the device to its factory settings
- **Selective wipe**: Remove only organizational data
- **Passcode reset**: Remove or reset the passcode when a user forgets it
- **Remote lock**: Help secure a device that might be lost

## Full wipe

When you need to secure a lost device or when you retire a device from active use, you can start a full wipe on it. This action restores the device to its factory defaults. It removes all organizational and user data and settings.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device that you want to wipe.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Retire/Wipe**.
4. In the **Retire from Configuration Manager** window, select the option to **Wipe the mobile device and retire it from Configuration Manager**.

## Selective wipe

To remove only organizational data from a device, start a selective wipe.

### Behaviors by OS version

The following tables describe what data is removed and the effect on data that remains on the device after a selective wipe.

#### Windows 10, Windows 8.1, Windows RT 8.1, and Windows RT

| Content | Selective wipe behavior |
| --- | --- |
| Apps and associated data installed by Configuration Manager | It uninstalls the apps, and removes any sideloading keys. It revokes the encryption key for apps that use Windows Selective Wipe, and the data is no longer accessible. |
| VPN and Wi-Fi profiles | Removes the profiles |
| Certificates | Removes and revokes the certificates |
| Settings | Removes requirements |
| Email profiles | Removes email that's EFS-enabled, which includes the Mail app for Windows email and attachments. |

#### Windows 10 Mobile, Windows Phone 8.0, and Windows Phone 8.1

| Content | Selective wipe behavior |
| --- | --- |
| Company apps and associated data installed by Configuration Manager | It uninstalls the apps and removes organizational app data. |
| VPN and Wi-Fi profiles | Removes the profiles for Windows 10 Mobile and Windows Phone 8.1 |
| Certificates | Removes the certificates for Windows Phone 8.1 |
| Email profiles | Removes the profiles (except Windows Phone 8.0) |

The following settings are also removed from Windows 10 Mobile and Windows Phone 8.1 devices:

- **Require a password to unlock mobile devices**
- **Allow simple passwords**
- **Minimum password length**
- **Required password type**
- **Password expiration (days)**
- **Remember password history**
- **Number of repeated sign-in failures to allow before the device is wiped**
- **Minutes of inactivity before password is required**
- **Required password type – minimum number of character sets**
- **Allow camera**
- **Require encryption on mobile device**
- **Allow removable storage**
- **Allow web browser**
- **Allow application store**
- **Allow screen capture**
- **Allow geolocation**
- **Allow Microsoft Account**
- **Allow copy and paste**
- **Allow Wi-Fi tethering**
- **Allow automatic connection to free Wi-Fi hotspots**
- **Allow Wi-Fi hotspot reporting**
- **Allow factory reset**
- **Allow Bluetooth**
- **Allow NFC**
- **Allow Wi-Fi**

### Start a selective wipe

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device that you want to wipe.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Retire/Wipe**.
4. In the **Retire from Configuration Manager** window, select the following option: **Wipe company content and retire the mobile device from Configuration Manager**.

### Recommendations for selective wipe

- For a successful wipe of email, set up email profiles to Windows Phone 8.1 devices.
- For a successful wipe of apps, make sure the apps are distributed through mobile device app management.

## Passcode reset

If a user forgets their passcode, use this action to force a new temporary passcode on the device. You can also remove the passcode entirely. The following table lists how passcode reset works on different mobile platforms.

| OS version | Passcode reset |
| --- | --- |
| Windows 10 | Not supported |
| Windows 10 mobile | Supported, excluding Microsoft Entra joined devices |
| Windows Phone 8 and Windows Phone 8.1 | Supported |
| Windows RT 8.1 | Not supported |
| Windows 8.1 | Not supported |

Note

Start the passcode reset action from the top-level site. For example, if you use a central administration site, you can only do the action on that site. If you're using a standalone primary site, you can only do the action from that site.

### Remotely reset the passcode on a mobile device

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device or devices on which to reset the passcode.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Passcode Reset**.

### Show the state of the passcode reset

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device or devices on which to show the state of the passcode reset.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Show Passcode State**.

## Remote lock

If a user loses their device, you can lock the device remotely. The following table lists how remote lock works on different mobile platforms.

| OS version | Remote lock |
| --- | --- |
| Windows 10 | Not supported |
| Windows Phone 8 and Windows Phone 8.1 | Supported |
| Windows RT 8.1 | Supported, if the current user of the device is the same user who enrolled the device. |
| Windows 8.1 | Supported, if the current user of the device is the same user who enrolled the device. |

Note

Start the remote lock action from the top-level site. For example, if you use a central administration site, you can only do the action on that site. If you're using a standalone primary site, do the action from that site.

### Remotely lock a mobile device

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device or devices to lock.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Remote Lock**. Confirm the action.

### Show the state of the remote lock

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and choose the **Devices** node. You can also choose **Device Collections** and select a collection of which the device is a member.
2. Select the device on which to show the state of the remote lock.
3. On the ribbon, in the Device group, select **Remote Device Actions**, and then choose **Show Remote Lock State**.