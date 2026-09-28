---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 10 of 10 - Register device for Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/register-device
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 10 of 10 - Register device for Windows Autopilot.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 277c3eab-cb5a-39b0-0ded-87eb91aee7d9
document_version_independent_id: 277c3eab-cb5a-39b0-0ded-87eb91aee7d9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/register-device.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/register-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/register-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 71e302d4-62a3-5613-7c18-808f9b13b0fe
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 10 of 10 - Register device for Windows Autopilot | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)

- **Step 10: Register device for Windows Autopilot**

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Register device for Windows Autopilot

Running the Windows Autopilot for existing devices task sequence and the Windows Autopilot deployment on a device doesn't automatically register the device for Windows Autopilot. The Windows Autopilot profile JSON makes the Windows Autopilot deployment available to the device and allows the device to run that particular Windows Autopilot deployment, but it doesn't register the device for Windows Autopilot. If the device ever undergoes a reset, when it runs Windows Setup and the out-of-box experience (OOBE) for the first time after the reset, it won't run the Windows Autopilot deployment again even though it has previously run a Windows Autopilot deployment.

To ensure that the device can run a Windows Autopilot deployment after a reset, the device must be registered for Windows Autopilot. The device can be registered as a Windows Autopilot device by using one of the following methods:

1. [Manually register devices with Windows Autopilot](../../add-devices): Manually registering a device includes manually registering devices into Intune as a Windows Autopilot device via the hardware hash. The hardware hash of a device can be collected via one of the following methods:

    - [Configuration Manager](/en-us/intune/configmgr/comanage/how-to-prepare-Win10#windows-autopilot)
    - [PowerShell script](../../add-devices#powershell)
    - [Diagnostics page hash export](../../add-devices#diagnostics-page-hash-export)
    - [Desktop hash export](../../add-devices#desktop-hash-export)
2. In a Windows Autopilot profile that is deployed to a device group that the device is a member of, make sure the option **Convert all targeted devices to Autopilot** is set to **Yes**. For more information on creating and assigning Windows Autopilot profiles, see one of the following articles on creating and assigning a Windows Autopilot profile for each of the different Windows Autopilot scenarios:

    - [User-driven Microsoft Entra join: Create and assign user-driven Microsoft Entra join Windows Autopilot profile](../user-driven/azure-ad-join-autopilot-profile)
    - [User-driven Microsoft Entra hybrid join: Create and assign user-driven Microsoft Entra hybrid join Windows Autopilot profile](../user-driven/hybrid-azure-ad-join-autopilot-profile)
    - [Pre-provisioning Microsoft Entra join: Create and assign a pre-provisioned Microsoft Entra join Windows Autopilot profile](../pre-provisioning/azure-ad-join-autopilot-profile)
    - [Pre-provisioning Microsoft Entra hybrid join: Create and assign a pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile](../pre-provisioning/hybrid-azure-ad-join-autopilot-profile)
    - [Self-deploying mode: Create and assign self-deploying Windows Autopilot profile](../self-deploying/self-deploying-autopilot-profile)

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

## Ensure domain join profile is assigned to all devices

For Windows Autopilot scenarios that utilize Microsoft Entra hybrid join and run after the Windows Autopilot deployment for existing devices task sequence completes, make sure that the domain join profile is assigned to **All devices**. This modification can be done at the followings steps:

- For the [Windows Autopilot user-driven Microsoft Entra hybrid join](../user-driven/hybrid-azure-ad-join-workflow) scenario at [Step 8: Configure and assign domain join profile](../user-driven/hybrid-azure-ad-join-domain-join-profile).
- For the [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join](../pre-provisioning/hybrid-azure-ad-join-workflow) scenario at [Step 8: Configure and assign domain join profile](../pre-provisioning/hybrid-azure-ad-join-domain-join-profile).

The domain join profile needs to be assigned to **All devices** because:

- If the existing device has never joined Microsoft Entra ID before the Windows Autopilot deployment runs, then there isn't a Microsoft Entra ID device object for the device in Intune. The Microsoft Entra ID device object is created in Intune when the device joins Microsoft Entra ID as part of the Windows Autopilot deployment.
- If the existing device has never registered as a Windows Autopilot device before the Windows Autopilot deployment runs, then there isn't a Windows Autopilot device object for the device in Intune. Normally a device has to be a Windows Autopilot device before the Windows Autopilot deployment can run on it. However, for the Windows Autopilot deployment for existing devices scenario, registering the device as a Windows Autopilot device isn't required since it instead uses the Windows Autopilot profile JSON file. The device is instead registered as a Windows Autopilot device after the Windows Autopilot deployment completes via the methods in the Register device for Windows Autopilot section.

In both of the above scenarios, there's no device that can be added to a device group before the Windows Autopilot deployment begins. Since there's no device group that contains the device, there's no device group that the domain join profile can be assigned to before the Windows Autopilot deployment begins. Assigning the domain join profile to **All devices** resolves this problem and ensures that the device can pick up the domain join profile before it's either a Microsoft Entra device or Windows Autopilot device.