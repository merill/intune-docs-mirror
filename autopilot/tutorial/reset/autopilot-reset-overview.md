---
layout: Conceptual
title: Overview for Windows Autopilot Reset in Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/reset/autopilot-reset-overview
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Overview for Windows Autopilot Reset in Intune.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 3660d4d8-c38a-a02c-99d4-a0a4654ef6c1
document_version_independent_id: 3660d4d8-c38a-a02c-99d4-a0a4654ef6c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/reset/autopilot-reset-overview.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/reset/autopilot-reset-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/reset/autopilot-reset-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 2e6080f7-5edc-2fe8-97df-34965382cc2f
---

# Overview for Windows Autopilot Reset in Intune | Microsoft Learn

Windows Autopilot Reset takes the device back to a business-ready state, allowing the next user to sign in and get productive quickly and simply. In addition, once the Windows Autopilot Reset begins, it blocks the user from accessing the desktop until information is restored, including reapplying any provisioning packages. Windows Autopilot Reset also blocks the new user from accessing the desktop until an Intune sync is completed.

Important

Windows Autopilot Reset only supports Microsoft Entra join devices. Windows Autopilot Reset doesn't support Microsoft Entra hybrid join devices. For Microsoft Entra hybrid join devices, a [device wipe](/en-us/intune/device-management/actions/wipe) is required. When a hybrid Microsoft Entra device goes through a full device reset, it might take up to 24 hours for it to be ready to be deployed again. This request can be expedited by re-registering the device. Consider also using the [Windows Autopilot deployment for existing devices](../existing-devices/existing-devices-workflow) scenario to wipe the device.

## Information removed and reset by a Windows Autopilot Reset

The Windows Autopilot Reset process removes or resets the following information from the existing device:

- The device's primary user is removed when a remote Windows Autopilot Reset is used. The next user who signs in after the Windows Autopilot Reset will be set as the primary user. Shared devices will remain shared after the remote Windows Autopilot Reset.
- The device's owner in Microsoft Entra is removed when a remote Windows Autopilot Reset is used. The next user who signs in after the Windows Autopilot Reset will be set as the owner.
- Removes personal files, apps, and settings.
- Reapplies a device's original settings.
- Sets the region, language, and keyboard to the original values.

## Information kept and migrated after a Windows Autopilot Reset

The Windows Autopilot Reset process automatically keeps the following information from the existing device:

- Maintains the device's identity connection to Microsoft Entra ID.
- Maintains the device's management connection to Intune.
- Wi-Fi connection details.
- Provisioning packages previously applied to the device.
- A provisioning package present on a USB drive when the reset process is started.
- Microsoft Entra device membership and Intune enrollment information.
- System Center Endpoint Protection (SCEP) certificates.
- The device's primary user and owner in Microsoft Entra aren't updated when a local Windows Autopilot Reset is used.

## Windows Autopilot Reset requirements

- Enrolled in Microsoft Entra ID. Only Microsoft Entra join devices are supported. Microsoft Entra hybrid join devices aren't supported.
- Enrolled in Intune.
- [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) is correctly configured and enabled on the device where Windows Autopilot Reset is used.
- User initiating [local Windows Autopilot Reset](local-autopilot-reset) must be a local administrator on the device.
- Admins initiating a [remote Windows Autopilot Reset](remote-autopilot-reset) must be a member of the Intune Service Administrator role.

## Windows Autopilot Reset Scenarios in Intune

Windows Autopilot Reset in Intune supports two scenarios:

- [Local reset](local-autopilot-reset) - a Windows Autopilot Reset started locally on the device by a user.
- [Remote reset](remote-autopilot-reset) - a Windows Autopilot Reset started remotely by an Intune admin in Microsoft Intune.

## How Windows Autopilot Reset works

Windows Autopilot Reset works by using the [push-button reset](/en-us/windows-hardware/manufacture/desktop/push-button-reset-overview) feature in Windows. The following actions occur during a Windows Autopilot Reset:

- A new OS of the same version is created by reconstructing it from the WinSxS store.
- Migration of data is performed between the old OS and the new OS to preserve the items from Information kept and migrated after a Windows Autopilot Reset.
- All existing user profiles and data are deleted.
- Non-Microsoft apps are uninstalled.

## Walkthrough

Both local Windows Autopilot Reset and remote Windows Autopilot Reset require a minimal number of steps to implement. Unlike other Windows Autopilot scenarios, instructions with multiple steps aren't needed. Select the desired Windows Autopilot Reset scenario for instructions on how to implement the scenario: