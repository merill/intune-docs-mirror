---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 8 of 10 - Speed up the deployment process (optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/speed-up-deployment
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 8 of 10 - Speed up the deployment process (optional).
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 961e2376-b278-802a-2def-895d6bfae29e
document_version_independent_id: 961e2376-b278-802a-2def-895d6bfae29e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/speed-up-deployment.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/speed-up-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/speed-up-deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 53f387c9-eb60-c7c0-2446-dbf2c5f18edd
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 8 of 10 - Speed up the deployment process (optional) | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)

- **Step 8: Speed up the deployment process (optional)**

- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Windows Autopilot for existing devices task sequence process

When the Windows Autopilot for existing devices task sequence runs on a device, the Windows Autopilot deployment doesn't run when the device boots into Windows for the first time during the **Setup Windows and ConfigMgr** task of the task sequence. Instead, the Windows Autopilot deployment doesn't run until after the task sequence completes.

The Windows Autopilot deployment normally runs when Windows boots for the first time and Windows Setup and the out-of-box experience (OOBE) run. However, during a Windows Autopilot for existing devices task sequence, even though the task sequence injected a Windows Autopilot profile JSON file into the offline Windows installation, the file isn't processed when Windows first boots because the task sequence also creates and injects an `unattend.xml` file. When there's both an `unattend.xml` file and a Windows Autopilot profile JSON file during Windows Setup, Windows Setup ignores the Windows Autopilot profile JSON file, and it only processes the `unattend.xml` file.

After Windows Setup is done, the task sequence resumes and deletes the existing `unattend.xml`. Later in the task sequence when the task sequence runs Sysprep on the device, it doesn't specify or add a new `unattend.xml` file. Once the task sequence finishes running Sysprep, the task sequence completes and the device is rebooted. When the device reboots, Windows starts and Windows Setup runs for a second time. Since there's no `unattend.xml` file and only the Windows Autopilot profile JSON file exists, Windows Setup processes the Windows Autopilot profile JSON file and the Windows Autopilot deployment starts.

An overview of the Windows Autopilot for existing devices task sequence process is as follows:

1. Task sequence starts in Windows PE.
2. Task sequence formats and partitions the disk.
3. Task sequence applies the Windows OS and creates the `unattend.xml` file.
4. Task sequence injects the Windows Autopilot profile JSON file.
5. Task sequence boots into Windows for the first time.
6. Windows setup runs for the first time and processes the `unattend.xml` file. Windows Autopilot profile JSON file is ignored.
7. Task sequence resumes in the newly installed Windows OS.
8. Task sequence deletes the unattend.xml file.
9. Task sequence installs the Configuration Manager client.
10. Task sequence runs additional tasks (**Install Application**, **Install Software Updates**, **Install Package**, **Enable BitLocker**, etc.)
11. Task sequence uninstalls the Configuration Manager client.
12. Task sequence Syspreps the device.
13. Task sequence completes and device reboots.
14. Windows setup runs for the second time and processes the Windows Autopilot profile JSON file since there's no `unattend.xml` file.
15. Windows Autopilot deployment starts.

## Additional tasks running during a Windows Autopilot for existing devices task sequence

When using the **Create Task Sequence Wizard** in Configuration Manager to create the Windows Autopilot for existing devices task sequence, it assumes that additional tasks need to be run via the task sequence before the Windows Autopilot deployment runs. Examples of additional tasks running via the task sequence before the Windows Autopilot deployment runs include:

- Installing applications via the **Install Application** task.
- Installing software updates via the **Install Software Updates** task.
- Installing packages via the **Install Package** task.
- Enabling BitLocker via the **Enable BitLocker** task.
- Other customizations.

In order for these additional tasks to run, the task sequence deployment process performs the following processes after it boots out of Windows PE:

- Boots into the Windows OS for the first time and runs Windows Setup and OOBE.
- Continues the task sequence in the full Windows OS.
- Installs the Configuration Manager client to support running tasks such as the **Install Application** or **Install Software Updates** tasks.
- Runs the additional tasks.
- Removes the Configuration Manager client.
- Syspreps the device so that after the task sequence completes and the device reboots, it can rerun Windows Setup and OOBE, which then launches the Windows Autopilot deployment.

The above steps are necessary if additional tasks need to run during the task sequence. However, if additional tasks don't need to run during the task sequence, then several of the above steps aren't needed. Running the above steps when they aren't needed can potentially cause several issues including:

- Needlessly adding time to the deployment process.
- Needlessly installing the Configuration Manager client on the device. It's best practice to avoid installing the Configuration Manager client if not needed during the task sequence and if it's eventually going to be uninstalled.
- Needlessly running Windows Setup and OOBE multiple times.
- Needlessly running Sysprep.

## Speed up the deployment process

Tip

If a task sequence is needed to run additional tasks before running the Windows Autopilot deployment, then skip to the next step of [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence).

However, even if additional tasks are needed, instead of using the task sequence to run these tasks, consider running the additional tasks using alternate methods. For example:

- Install applications via Intune.
- Enable BitLocker via Intune.
- Install software updates via offline servicing and [Configuration Manager Scheduled Updates](/en-us/intune/configmgr/osd/get-started/manage-operating-system-images#apply-software-updates-to-an-image).

When possible, Microsoft recommends using the above methods to run the additional tasks instead of running them via the task sequence. Using the above methods allows using this solution to speed up the deployment.

If no additional tasks are needed via a task sequence before running the Windows Autopilot deployment, then the Windows Autopilot for existing devices task sequence can be modified to eliminate unneeded tasks and processes. Eliminating unneeded tasks and processes speeds up the deployment process and the time it takes for the deployment to finish. Examples of processes that can be eliminated to speed up the deployment include:

- Running Windows Setup additional times via the **Setup Windows and ConfigMgr** task.
- Installing the Configuration Manager client via the **Setup Windows and ConfigMgr**.
- Uninstalling the Configuration Manager client via the **Prepare ConfigMgr Client for Capture** task.
- Running Sysprep via the **Prepare Windows for Capture**/**Sysprep** tasks.

The solution to speed up the deployment deletes the `unattend.xml` file and eliminates the unnecessary tasks so that the Windows Autopilot profile JSON file is processed during the first boot into Windows. After the solution is applied, the updated overview of the Windows Autopilot for existing devices task sequence process is as follows:

1. Task sequence starts in Windows PE.
2. Task sequence formats and partitions the disk.
3. Task sequence applies the Windows OS and creates the unattend.xml file.
4. Task sequence injects the Windows Autopilot profile JSON file.
5. Task sequence deletes the `unattend.xml` file.
6. Task sequence boots into Windows for the first time.
7. Windows setup runs for the first time and processes the Windows Autopilot profile JSON file since there's no `unattend.xml` file.
8. Windows Autopilot deployment starts.

The solution to speed up the deployment reduces the number of steps in the deployment process from 15 to 8.

Note

The steps for the solution to speed up the deployment are optional. The out-of-box Windows Autopilot for existing devices task sequence still works without any modification. The below steps are only designed to reduce the time it takes to run the deployment and potentially avoid some issues. If the preference is to not modify the existing Windows Autopilot for existing devices task sequence, then skip to the next step of [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence).

To modify the Windows Autopilot for existing devices task sequence to speed up the deployment process, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Operating Systems**.
3. Expand **Task Sequences** and then locate the Windows Autopilot for existing devices task sequence created in the [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence) step.
4. Once the Windows Autopilot for existing devices task sequence is located, select it and then on the ribbon, select **Edit**. Alternatively, right-click on the Windows Autopilot for existing devices task sequence and select **Edit**.
5. In the **Task Sequence Editor** window that opens:

    1. Select the **Prepare device for Windows Autopilot** group and then select the **Remove** option in the top left of the task sequence editor. A confirmation dialog box appears confirming to delete the step. Select the **Yes** button to remove the **Prepare device for Windows Autopilot** group.
    2. Select the **Setup Operating System** group and then select the **Remove** option in the top left of the task sequence editor. A confirmation dialog box appears confirming to delete the step. Select the **Yes** button to remove the **Setup Operating System** group.

        Note

        If there were any additional tasks or groups after the **Setup Windows and Configuration Manager** task, then also remove those tasks and groups by selecting the **Remove** option in the top left of the task sequence editor for each one of those tasks or groups. For each removal, a confirmation dialog box appears confirming to delete the step or group. Select the **Yes** button to remove each additional task or group.
    3. Select the last task in the task sequence.
    4. Select the **Add** drop down menu in the top left of the task sequence editor and then select **General** &gt; **Run Command Line**. A **Run Command Line** task is added as the last task in the task sequence.
    5. Select the **Run Command Line** task and then configure with the following settings:

        - **Name**: Remove unattend.xml from Panther
        - **Command Line**: Select **Copy** at the top right corner of the below **Windows Command Prompt** code block and then paste into the **Command Line** text box:

            ```cmd
            cmd.exe /c del %OSDTargetSystemDrive%\Windows\Panther\unattend.xml /s
            ```
    6. Select the **OK** button in the **Task Sequence Editor** to save the changes to the task sequence.
6. If there are multiple Windows Autopilot for existing devices task sequences, then repeat the above steps for each task sequence.

## Shut down device after the task sequence completes (optional)

When the task sequence modified to speed up the deployment process finishes running and is complete, the device restarts and then immediately boot into Windows for the first time. After booting into Windows for the first time, it will run Windows Setup and OOBE. When Windows Setup and OOBE run, the Windows Autopilot JSON file is processed and the Windows Autopilot deployment begins.

However, the device can be shut down instead of restarting when the task sequence completes. Shutting down the device instead of restarting it when the task sequence completes can be useful, for example, to give the option to further prepare the device and then deliver it to an end-user. Windows Setup, OOBE, and the Windows Autopilot deployment then instead starts when the end-user turns on the device for the first time.

If the default behavior of restarting the device when the task sequence completes is desired, then skip this section and proceed to the next step of [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence). Otherwise, to shut down the device instead of restarting it when the task sequence completes, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Operating Systems**.
3. Expand **Task Sequences** and then locate the Windows Autopilot for existing devices task sequence modified in the Speed up the deployment process section.
4. Once the Windows Autopilot for existing devices task sequence is located, select it and then on the ribbon, select **Edit**. Alternatively, right-click on the Windows Autopilot for existing devices task sequence and select **Edit**.
5. In the **Task Sequence Editor** window that opens:

    1. Select the last task in the task sequence.
    2. Select the **Add** drop down menu in the top left of the task sequence editor and then select **General** &gt; **Run Command Line**. A **Run Command Line** task is added as the last task in the task sequence.
    3. Select the **Run Command Line** task and then configure with the following settings:

        - **Name**: Shutdown
        - **Command Line**: Select **Copy** at the top right corner of the below **Windows Command Prompt** code block and then paste into the **Command Line** text box:

            ```cmd
            wpeutil.exe shutdown
            
            ```
    4. Select the **OK** button in the **Task Sequence Editor** to save the changes to the task sequence.
6. If there are multiple Windows Autopilot for existing devices task sequences, then repeat the above steps for each task sequence.

## Next step: Run Windows Autopilot task sequence on device