---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 9 of 10 - Run Windows Autopilot task sequence on device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/run-autopilot-task-sequence
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 9 of 10 - Run Windows Autopilot task sequence on device.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 94bf9c05-1a04-c258-1c00-2de09fcecd11
document_version_independent_id: 94bf9c05-1a04-c258-1c00-2de09fcecd11
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/run-autopilot-task-sequence.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/run-autopilot-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/run-autopilot-task-sequence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 99cd12fe-773f-b74f-ad86-74d2fb0187d7
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 9 of 10 - Run Windows Autopilot task sequence on device | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)

- **Step 9: Run Windows Autopilot task sequence on device**

- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Run Windows Autopilot task sequence on device

Once the Windows Autopilot for existing devices is created, modified as needed, and deployed, the task sequence can be run on a device by following these steps:

1. Start the task sequence using the desired method based on how the task sequence deployment was configured:

    - Configuration Manager Software Center
    - PXE enabled distribution point
    - Task sequence bootable media
2. Allow the task sequence to complete.
3. Once the task sequence completes, the device either restarts or shuts down depending on the shutdown or restart behavior selected in one of the following two steps:

    - [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence#modify-the-task-sequence-to-account-for-sysprep-command-line-configuration).
    - [Speed up the deployment process](run-autopilot-task-sequence).

    The behavior of the device after the task sequence completes depends on whether the device restarted or shut down:

    - **Restart**: the device restarts as soon as the task sequence completes and then immediately boot into Windows for the first time and run OOBE. When OOBE runs, the Windows Autopilot JSON file is processed and the Windows Autopilot deployment starts.
    - **Shutdown**: the device shuts down and power off as soon as the task sequence completes. Shutting down the device gives the option to further prepare the device and then deliver it to an end-user. OOBE and the Windows Autopilot deployment start when the end-user turns on the device for the first time.

    Important

    A Windows Autopilot profile downloaded from Intune is used instead of the Windows Autopilot profile from the JSON file if the following conditions are met after the task sequence completes:

    - Device is registered as a Windows Autopilot device in Intune.
    - Device has a Windows Autopilot profile assigned to it in Intune.

    The Windows Autopilot profile downloaded from Intune has priority over the local Windows Autopilot profile from the JSON file.

## Next step: Register device for Windows Autopilot