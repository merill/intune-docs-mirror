---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 5 of 10 - Create Windows Autopilot task sequence in Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/create-autopilot-task-sequence
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 5 of 10 - Create Windows Autopilot task sequence in Configuration Manager.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 3a893058-328e-2444-501c-3a8560f616e5
document_version_independent_id: 3a893058-328e-2444-501c-3a8560f616e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/create-autopilot-task-sequence.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/create-autopilot-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/create-autopilot-task-sequence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8316e7cd-0410-147e-1ff9-33e9b6dc9051
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 5 of 10 - Create Windows Autopilot task sequence in Configuration Manager | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)

- **Step 5: Create Windows Autopilot task sequence in Configuration Manager**

- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Create Windows Autopilot task sequence for existing devices in Configuration Manager

Once the packages containing the Windows Autopilot profile JSON files are created and distributed in Configuration Manager, the next step is to create a task sequence that performs the following functions:

- Wipes the device.
- Installs a fresh copy of Windows on the device.
- Copies the Windows Autopilot profile JSON file to the device.

Copying of the Windows Autopilot profile JSON file is done in WinPE when the newly installed Windows OS is offline. When the task sequence completes, the device boots into the newly installed Windows OS for the first time and runs the out-of-box experience (OOBE). The OOBE process then processes the Windows Autopilot profile JSON file, which initiates the Windows Autopilot deployment.

Note

If using multiple Windows Autopilot profiles and multiple Windows Autopilot profile JSON files were created, a separate task sequence is needed for each of the Windows Autopilot profiles.

To create the Windows Autopilot for existing devices task sequence in Configuration Manager, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Operating Systems**.
3. Select **Task Sequences** and then on the ribbon, select **Create Task Sequence**. Alternatively, right-click **Task Sequences** and select **Create Task Sequence**.
4. The **Create Task Sequence Wizard** window appears:

    1. In the **Create new task sequence** page, select the option to **Deploy Windows Autopilot for existing devices**, and then select the **Next &gt;** button.
    2. In the **Specify task sequence information** page:

        1. Next to **Name**, enter an identifiable name for the Windows Autopilot scenario for the task sequence. For example, **Windows Autopilot user-driven Microsoft Entra join**.
        2. Next to **Description**, enter a description for the Windows Autopilot scenario for the task sequence.
        3. Next to **Boot image:**, select the **Browse** button.

            - In the **Select a Boot Image** windows that appears, under **Boot images:**, select a boot image, and then select the **OK** button.
        4. Select the **Next &gt;** button.
    3. In the **Install the Windows operating system** page:

        1. Next to **Image package:**, select the **Browse** button. In the **Select an Operating System Image** window that appears, under **Operating system images:**, locate and select the desired Windows operating system image, and then select the **OK** button.
        2. Next to **Image index:**, select the desired Windows version. For example, **Enterprise**.
        3. Make sure the option **Partition and format the target computer before installing the operating system** is selected and enabled.
        4. Make sure the option **Configure task sequence for use with BitLocker** isn't selected. If BitLocker encryption is desired, Microsoft recommends enabling via Intune policies that are applied during the Windows Autopilot deployment.

            Note

            Although BitLocker encryption could technically be enabled via the task sequence, it might result in undesired outcomes. For example, instead of saving BitLocker recovery keys to Intune or Microsoft Entra ID, they might be saved to:

            - Configuration Manager BitLocker Management.
            - On-premises Active Directory.

            Additionally, if BitLocker settings specified in the task sequence don't match the BitLocker policy settings in Intune, then this mis-match could cause the device to show as non-compliant. Resolving issues like this could mean having to decrypt and then re-encrypt the drive to resolve. Therefore Microsoft recommends not enabling BitLocker as part of the task sequence and instead enabling BitLocker as part of Intune policies deployed during Windows Autopilot.
        5. Leave **Product key** blank. The Windows Autopilot for existing devices task sequence runs the [Windows System Preparation Tool (Sysprep)](/en-us/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview) at the end of the task sequence. Sysprep clears any product key that is specified.
        6. Leave the option of **Randomly generate the local administrator password and disable the account on all support platforms (recommended)** selected. Alternatively, the option of **Enable the account and specify the local administrator password** can be selected and a password specified. However, the password specified will only be useful after the **Setup Windows and ConfigMgr** task and if the task sequence fails and doesn't complete successfully. If the task sequence completes successfully, the password is cleared at the end of the task sequence by Sysprep.
        7. Once all options are configured in the **Install the Windows operating system** page, select the **Next &gt;** button.

        Note

        If using the alternate [Speed up the deployment process (optional)](speed-up-deployment) step later in this tutorial, Sysprep never runs as part of the task sequence. However, the product key and local administrator password never get processed since the `unattend.xml` file that contains the product key and local administrator password is deleted as part of this optional step. For this reason, when using the alternate [Speed up the deployment process (optional)](speed-up-deployment) step, the settings specified for these two options are irrelevant since they're never processed.
    4. In the **Install the Configuration Manager client** page, add any necessary Configuration Manager client installation properties for the environment. For example, since the device is a Workgroup device and not domain joined during the Windows Autopilot for existing devices task sequence, the [SMSMP](/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#smsmp) or [SMSMPLIST](/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#smsmplist) parameters might be needed to run certain tasks such as the **Install Application** or **Install Software Updates** tasks. Once finished adding any Configuration Manager client installation properties, select the **Next &gt;** button.
    5. In the **Install software updates** page, select the desired option to install software updates during the task sequence. For the Windows Autopilot for existing devices task sequence, Microsoft recommends leaving the option to the default of **Do not install any software updates** and not install any software updates during the task sequence. Once the desired option is selected, select the **Next &gt;** button.

        Tip

        Microsoft recommends not installing software updates during the Windows Autopilot for existing devices task sequence because doing so significantly increases the time for the task sequence to complete. Instead, consider installing updates using one of the following two options:

        - The Configuration Manager offline image servicing feature of [Scheduled Updates](/en-us/intune/configmgr/osd/get-started/manage-operating-system-images#apply-software-updates-to-an-image)
        - Every month, download the latest monthly ISO for the version of Windows that's being installing and then update the **Operating System Images** package in Configuration Manager with the new updated `install.wim` image from the ISO. The ISOs are updated monthly and have the latest updates in them.
    6. In the **Install applications** page, select the desired applications to install during the task sequence. Once the desired applications are added, select the **Next &gt;** button. If no applications need to be installed, then select the **Next &gt;** button without selecting any applications.

        Tip

        Instead of installing applications during the task sequence, Microsoft recommends installing all applications and configurations from Microsoft Intune or Configuration Manager co-management. This process provides a consistent experience between users receiving new devices and those using Windows Autopilot for existing devices.
    7. On the **Prepare System for Windows Autopilot** page, select the package that includes the Windows Autopilot JSON file created in the step [Create and distribute package for JSON file in Configuration Manager](create-json-package). Once the package with the Windows Autopilot JSON file is selected, select the **Next &gt;** button.

        Note

        Leave the option **Shutdown computer after this task sequence completes** unchecked. This option is configured later in the section Modify the task sequence to account for Sysprep command line configuration.
    8. On the **Confirm the settings** page, verify that all settings are correct, and then select the **Next &gt;** button.
    9. When the **Create Task Sequence Wizard** completes with **The task "Create Task Sequence Wizard" completed successfully** message, select the **Close** button.
5. If using multiple Windows Autopilot profiles and multiple Windows Autopilot profile JSON files were created, repeat the above steps to create additional task sequences. Each Windows Autopilot profile JSON file needs its own separate task sequence.

Note

For Windows Autopilot for existing devices task sequence, the **Create Task Sequence Wizard** purposely skips configuring and adding the **Apply Network Settings** task. If the **Apply Network Settings** task isn't specified in a task sequence, it uses Windows default behavior, which is to join a workgroup.

The Windows Autopilot for existing devices task sequence runs the **Prepare Windows for capture** step, which uses the Windows System Preparation Tool (Sysprep). If the device is joined to a domain, Sysprep fails, so therefore the Windows Autopilot for existing devices task sequence joins a workgroup. For this reason, it isn't necessary to add the **Apply Network Settings** task to a Windows Autopilot for existing devices task sequence.

## Modify the task sequence to account for Sysprep command line configuration

The Windows Autopilot for existing devices task sequence adds the **Prepare Windows for Capture** task to the task sequence. The **Prepare Windows for Capture** task is the task that runs Sysprep. Sysprep needs to run so that on the next boot, OOBE runs and processes the Windows Autopilot profile JSON file. However, the **Prepare Windows for Capture** task adds the `/Generalize` parameter to the Sysprep command line. The `/Generalize` parameter causes Sysprep to delete the Windows Autopilot profile JSON file. The `/Generalize` parameter for Sysprep is normal for traditional build and capture task sequences not associated with Windows Autopilot, but it breaks Windows Autopilot deployments since the Windows Autopilot profile JSON file is deleted. Deletion of the Windows Autopilot profile JSON file causes Windows Autopilot to never run during Windows Setup and OOBE.

To resolve the issue, the **Prepare Windows for Capture** task needs to be removed from the task sequence and replaced with a **Run Command Line** task that runs Sysprep without the `/Generalize` parameter. This resolution can be accomplished by following these steps:

Note

If the optional step of [Speed up the deployment process (optional)](speed-up-deployment) is going to be followed, then skip this section and proceed to the next step of [Step 6: Create collection in Configuration Manager](create-collection).

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Operating Systems**.
3. Expand **Task Sequences** and then locate the Windows Autopilot for existing devices task sequence created in the Create Windows Autopilot task sequence for existing devices in Configuration Manager section.
4. Once the Windows Autopilot for existing devices task sequence is located, select it and then on the ribbon, select **Edit**. Alternatively, right-click on the Windows Autopilot for existing devices task sequence and select **Edit**.
5. In the **Task Sequence Editor** window that opens:

    1. Select the **Prepare Windows for Capture** task.
    2. Select the **Add** drop down menu in the top left of the task sequence editor and then select **General** &gt; **Run Command Line**. A **Run Command Line** task is added immediately after the **Prepare Windows for Capture** task.
    3. Select the **Run Command Line** task and then configure with the following settings:

        - **Name**: Sysprep
        - **Command Line**: Based on the desired behavior, select one of the following two Sysprep command lines by selecting **Copy** at the top right corner of the desired **Windows Command Prompt** code block and then pasting the copied Sysprep command line into the **Command Line** text box:

            - Restart device after running Sysprep. OOBE and that Windows Autopilot deployment will start immediately after the task sequence completes and the device restarts:

                ```cmd
                C:\Windows\System32\Sysprep\Sysprep.exe /oobe /reboot
                ```
            - Shut down device after running Sysprep. After the device shuts down, OOBE and the Windows Autopilot deployment won't start until the device is turned on for the first time by the end-user:

                ```cmd
                C:\Windows\System32\Sysprep\Sysprep.exe /oobe /shutdown
                ```

        Note

        Sysprep can either shut down or restart the device when it finishes running:

        - **Restarting** the device causes the device to restart as soon as the task sequence completes and then immediately boots into Windows for the first time and runs Windows Setup and OOBE. When Windows Setup and OOBE run, the Windows Autopilot JSON file is processed and the Windows Autopilot deployment starts.
        - **Shutting down** the device shuts down and powers off the device as soon as the task sequence completes. Shutting down and powering off the device give the option to further prepare the device and then deliver it to an end-user. Windows Setup, OOBE, and the Windows Autopilot deployment then start when the end-user turns on the device for the first time.
    4. Select the **Prepare Windows for Capture** task again and then select the **Remove** option in the top left of the task sequence editor. A confirmation dialog box appears confirming to delete the step. Select the **Yes** button to remove the **Prepare Windows for Capture** task.
    5. Select the **OK** button in the **Task Sequence Editor** to save the changes to the task sequence.

## Next step: Create collection in Configuration Manager