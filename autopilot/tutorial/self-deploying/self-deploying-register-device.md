---
layout: Conceptual
title: Windows Autopilot self-deploying mode - Step 3 of 6 - Register devices as Windows Autopilot devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/self-deploying/self-deploying-register-device
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
description: How to - Windows Autopilot self-deploying mode - Step 3 of 6 - Register devices as Windows Autopilot devices.
ms.date: 2025-03-25T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 1f61fa12-81f7-155e-cc3d-aa4274b6cc12
document_version_independent_id: 1f61fa12-81f7-155e-cc3d-aa4274b6cc12
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/self-deploying/self-deploying-register-device.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/self-deploying/self-deploying-register-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/self-deploying/self-deploying-register-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: ddf67b39-1b9f-5c0f-d0eb-30690cb1442e
---

# Windows Autopilot self-deploying mode - Step 3 of 6 - Register devices as Windows Autopilot devices | Microsoft Learn

Windows Autopilot self-deploying mode steps:

- Step 1: [Set up Windows automatic Intune enrollment](self-deploying-automatic-enrollment)

- **Step 2: Register devices as Windows Autopilot devices**

- Step 3: [Create a device group](self-deploying-device-group)
- Step 4: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](self-deploying-esp)
- Step 5: [Create and assign Windows Autopilot profile](self-deploying-autopilot-profile)
- Step 6: [Deploy the device](self-deploying-deploy-device)

For an overview of the Windows Autopilot self-deploying mode workflow, see [Windows Autopilot self-deploying overview](self-deploying-workflow#workflow).

Note

If devices are already registered as Windows Autopilot devices, skip this step and move on to [Step 3: Create a device group](self-deploying-device-group).

## Register devices as Windows Autopilot devices

Before a device can use Windows Autopilot, the device must be registered as a Windows Autopilot device. Registering a device as a Windows Autopilot device can be thought of as importing the device into Windows Autopilot so that Windows Autopilot service can be used on the device. Registering a device as a Windows Autopilot device doesn't mean that the device has used the Windows Autopilot service. It just makes the Windows Autopilot service available to the device.

Also note that a device registered in Windows Autopilot doesn't mean the device is enrolled in Intune. A device might be registered as a Windows Autopilot device but might not exist in Intune. It's not until a Windows Autopilot registered device goes through the Windows Autopilot process for the first time that it becomes enrolled in Intune. After the Windows Autopilot device undergoes the Windows Autopilot process and enrolls in Intune, the Windows Autopilot device appears as a device in both Microsoft Entra ID and Intune.

There are several methods to register a device as a Windows Autopilot device in Intune:

- Manually registering devices into Intune as a Windows Autopilot device via the hardware hash. The hardware hash of a device can be collected via one of the following methods:

    - [Configuration Manager](/en-us/intune/configmgr/comanage/how-to-prepare-Win10#windows-autopilot).
    - [PowerShell script](../../add-devices#powershell).
    - [Diagnostics page hash export](../../add-devices#diagnostics-page-hash-export).
    - [Desktop hash export](../../add-devices#desktop-hash-export).

    These methods of obtaining the hardware hash of a device are well documented. The corresponding documentation can be viewed by selecting the appropriate link from the above list.
- Automatically registering device via:

    - An [OEM](../../oem-registration), including [Microsoft Surface](/en-us/surface/surface-autopilot-registration-support) devices.
    - A [partner](../../partner-registration).

    Registering a device via an OEM or partner is also well documented. The corresponding documentation can be viewed by selecting the appropriate link from the above list.

For most organizations, using an OEM or partner to register devices as Windows Autopilot devices is the preferred, most common, and most secure method. However for smaller organizations, for testing/lab scenarios, and for emergency scenarios, manually registering devices as Windows Autopilot devices via the hardware hash is also used.

Important

The following type of devices shouldn't be registered as a Windows Autopilot device:

- [Microsoft Entra registered](/en-us/entra/identity/devices/concept-device-registration) devices, also known as "workplace joined" devices.
- [Intune MDM-only enrollment](/en-us/intune/device-enrollment/enroll-devices?tabs=byod-enrollment#windows-enrollment-methods) devices.

These options are intended for users to join personally owned devices to their organization's network. Windows Autopilot registered devices are registered as corporate owned devices.

If a device is already one of these two types of devices, to register is as a Windows Autopilot device, first remove it from Microsoft Intune and Microsoft Entra ID. For more information, see [Why is the join type for a device showing as "Microsoft Entra registered" instead of "Microsoft Entra joined"?](../../troubleshooting-faq#why-is-the-join-type-for-a-device-showing-as--microsoft-entra-registered--instead-of--microsoft-entra-joined--) and [Deregister a device](../../registration-overview#deregister-a-device).

Note

Assuming that a device isn't currently enrolled Intune, remember that registering a device in Windows Autopilot doesn't make it an Intune enrolled device. That device doesn't enroll into Intune until Windows Autopilot runs on the device for the first time.

## Importing the hardware hash CSV file for devices into Intune

Several of the methods in the previous section on obtaining the hardware hash when manually registering devices as Windows Autopilot devices produces a CSV file that contains the hardware hash of the device. This CSV file with the hardware hash needs to be imported into Intune to register the device as a Windows Autopilot device.

After the CSV file is created, it can be imported into Intune via the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen that opens, select **Import**.

    1. In the **Add Autopilot devices** window that opens:

        1. Under **Specify the path to the list you want to import.**, select the blue file folder.
        2. Browse to the CSV file obtained using one of the above methods to obtain the hardware hash of a device.
        3. After selecting the CSV file, verify that the correct CSV file is selected under **Specify the path to the list you want to import.**, and then select **Import**. Selecting **Import** closes the **Add Autopilot devices** window. Importing can take several minutes.
    2. After the import is complete, select **Sync**.

        A message displays saying that the sync is in progress. The sync process might take a few minutes to complete, depending on how many devices are being synchronized.

        Note

        If another sync is attempted within 10 minutes after initiating a sync, an error will be displayed. Syncs can only occur once every 10 minutes. To attempt a sync again, wait at least 10 minutes before trying again.
    3. Select **Refresh** to refresh the view. The newly imported devices should display within a few minutes. If the devices aren't yet displayed, wait a few minutes, and then select **Refresh** again.

## Next step: Create a device group