---
layout: Conceptual
title: Remote actions with co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-remote-actions
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
description: Run remote actions from Intune for co-managed devices
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 3fb77e43-2878-baba-6ebf-114b7aa48704
document_version_independent_id: 9320a651-b523-3011-4998-d2424507e554
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-remote-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-remote-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-remote-actions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 0cc3b4cc-e0dc-6310-a9b1-8a1c9f5e4c27
---

# Remote actions with co-management - Configuration Manager | Microsoft Learn

You need to make sure that every device you manage is reachable, no matter where it is, whenever it connects. You also need to provide each user with everything they need to stay productive, while protecting the apps and data. With the device actions supported by Intune, you can remotely solve these critical functions.

In the following video, principal program manager Heidi Cheng and senior program manager Danny Guillory discuss and demo remote actions with co-management:

## Benefits

Remote device actions give you management controls on the device without interfering with personal data. These remote device actions allow you to:

- Delete company data on lost or stolen devices
- Rename a device
- Restart a device
- Review device inventory
- Remotely control a device
- Wipe out pre-installed OEM apps with a Fresh Start reboot
- Do a factory reset on any Windows 10 or later device

These functions are an important and simple way to protect corporate data stored on these devices, whether in e-mail or OneDrive.

For more information on these actions, see [Available device actions](../../device-management/actions/#available-device-actions).

## Case studies

The global consulting firm Avanade regularly uses remote actions to manage the devices used by their 30,000 employees. In a blog post, the CIO of Avanade noted:

> 
> *Our immediate win from having the Intune functionality was the ability to remotely reset Windows on a machine. This is important to us for lost or stolen machines, which is more common in our highly mobile workforce.* *This is functionality that we otherwise would have had to build and maintain in a custom ConfigMgr package.*

For more information on how to use these device actions, see [Available device actions](../../device-management/actions/#available-device-actions).

## Value proposition

When a Configuration Manager device is co-managed, it immediately adds these functions that Configuration Manager doesn't natively have. Now you can do any remote action that's supported by Intune.

With co-management, the Configuration Manager devices are now just like any other Intune-managed device. For example, they have a full presence in the cloud, and you can reach them as long as they have internet access. You can do all of these actions without taking any additional steps beyond enabling co-management.

Since the auto-enrollment process is transparent to the user, there's no impact to their productivity. The user doesn't need to do anything.

### Available remote actions

Use these remote actions from Intune once you [enable co-management](how-to-enable) in Configuration Manager.

#### Remove devices

- **Retire**: This action removes managed apps and data (where applicable), settings, and e-mail profiles that were assigned to that device. The device is then removed from Intune management. This process happens the next time the device checks in and receives the remote retire action. The Retire function leaves the user's personal data on the device.
- **Wipe**: This action restores a device to its factory default settings. If you choose the option to **Retain enrollment state and user account**, then the user data is kept. Otherwise the drive is securely erased.
- **Delete**: If you want to remove devices from the Microsoft Intune admin center, delete them from the specific device pane. The next time the device checks in, it removes any organizational data stored on it.

For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](../../device-management/actions/wipe).

#### Selective wipe

When you choose an **App selective wipe**, it removes company app data without removing personal data. Use this action when a device is reported as lost or stolen.

For more information, see [How to wipe only corporate data from Intune-managed apps](../../app-management/protection/wipe-corporate-data).

#### Sync

The **Sync** device action forces the selected device to immediately check in with Intune. When a device checks in, it immediately receives any pending actions or policies that you've assigned to it.

This feature can help you immediately validate and troubleshoot policies you've assigned, without waiting for the next scheduled check-in.

For more information, see [Sync devices to get the latest policies and actions with Intune](../../device-management/actions/sync).

#### Restart

The **Restart** device action causes the device you choose to restart. This action is useful when there's a pending reboot, but the user isn't available to do it.

For more information, see [Remotely restart devices with Intune](../../device-management/actions/restart).

#### Fresh Start

The **Fresh Start** device action removes any apps installed on a device running Windows 10, version 1703 or later. Fresh Start helps remove pre-installed (OEM) apps that are typically installed with a new device.

If you choose not to retain user data, the device restores to its out-of-box state. It unenrolls from Microsoft Entra ID and MDM.

If you have predetermined standards regarding what apps should be on the device, then this action eliminates the ones that don't meet your criteria.

For more information, see [Use Fresh Start to reset Windows devices with Intune](../../device-management/actions/fresh-start).

#### Remote control

Devices managed by Intune can be administered remotely using [TeamViewer](https://www.teamviewer.com/). TeamViewer is a third-party program that you acquire separately.

For more information, see [Use TeamViewer to remotely administer Intune devices](../../device-management/tools/teamviewer-legacy).

## Configure

Other than remote control via TeamViewer, to start using these remote device actions in Intune, no additional setup is required after you [enable co-management](how-to-enable).

For more information on using TeamViewer for remote control, see [Use TeamViewer to remotely administer Intune devices](../../device-management/tools/teamviewer-legacy).