---
layout: Conceptual
title: User experiences for OS deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/user-experience
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
description: Learn about user experiences like the task sequence progress and media wizard for operating system deployment in Configuration Manager.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 066412bb-96a7-da11-5ff2-0b93e6591b3f
document_version_independent_id: fdb6d159-ecca-b3de-3d38-377a07a92344
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/understand/user-experience.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/understand/user-experience
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/understand/user-experience.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 42df3857-2c50-4cef-c5eb-ec2600130cba
---

# User experiences for OS deployment - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you [deploy a task sequence](../deploy-use/deploy-a-task-sequence), depending upon the scenario there are different ways for users to interact with the deployment. This article shows the main user experiences with OS deployments, and how you can configure them:

- Software Center user notification for a high-impact deployment
- A sample PXE boot experience
- Task sequence wizard from media
- Progress window when the task sequence runs
- Error window when the task sequence fails

## Software Center

For a high-impact deployment, you can customize the message that Software Center displays. When the user opens the OS deployment in Software Center, they see a message similar to the following window:

![Customized task sequence notification to the end user from Software Center.](../media/user-notification-enduser.png)

For more information on how to customize the message in this window, see [Create a custom notification](../deploy-use/high-impact-task-sequence-settings#create-a-custom-notification).

You can also customize the organization name at the top of the window. (The above example shows the default value, `IT Organization`). Change the **Organization name** client setting in the **Computer Agent** group. For more information, see [About client settings](../../core/clients/deploy/about-client-settings#computer-agent).

For more information, see [Use Software Center to deploy Windows over the network](../deploy-use/use-software-center-to-deploy-windows-over-the-network).

## PXE

Different hardware models have different experiences for PXE. To boot to the network, UEFI-based devices typically use the `Enter` key, and BIOS-based devices use the `F12` key.

The following example shows the Hyper-V Gen1 (BIOS) PXE experience:

![Example BIOS PXE screen from a Hyper-V virtual machine.](media/hyperv-pxe.png)

After the device successfully boots via PXE, it behaves similarly to bootable media. For more information, see the next section on the Task sequence wizard.

For more information, see [Use PXE to deploy Windows over the network](../deploy-use/use-pxe-to-deploy-windows-over-the-network).

Warning

If you use PXE deployments, and configure device hardware with the network adapter as the first boot device, these devices can automatically start an OS deployment task sequence without user interaction. Deployment verification doesn't manage this configuration. While this configuration may simplify the process and reduce user interaction, it puts the device at greater risk for accidental reimage.

## Task sequence wizard

When you use [task sequence media](../deploy-use/create-task-sequence-media), the task sequence wizard runs to guide the process.

### Welcome to the task sequence wizard

![Screenshot of main page of the Task Sequence Wizard.](media/welcome-task-sequence-wizard.png)

- If you password-protect the media, the user has to enter the password on this welcome page.
- Select **Configure Network Settings** to specify a static IP address or other custom network settings. Otherwise, the device uses DHCP by default.
- If your network requires a proxy, select **Configure Proxy Settings**.

### Select a task sequence to run

If you deploy more than one task sequence to the device, you see this page to select a task sequence. Make sure to use a name and description for your task sequence that users can understand.

![Screenshot of the task sequence selection page of the Task Sequence Wizard.](media/task-sequence-wizard-select.png)

### Edit task sequence variables

If any task sequence variables have empty values, the wizard shows a page to edit the variable values.

![Screenshot of the edit task sequence variables page of the Task Sequence Wizard.](media/task-sequence-wizard-variables.png)

### Return to previous page on failure

When you run a task sequence, and there's a failure, you can return to a previous page of the task sequence wizard. In prior versions of Configuration Manager, you had to restart the task sequence when there was a failure. Use the **Previous** button in the following scenarios:

- When a computer starts in Windows PE, the task sequence bootstrap dialog might display before the task sequence is available. When you select Next in this scenario, the final page of the task sequence displays with a message that there are no task sequences available. Now, you can select **Previous** to search again for available task sequences. You can repeat this process until the task sequence is available.
- When you run a task sequence, but dependent content packages aren't available yet on distribution points, the task sequence fails. If the missing content wasn't distributed yet, distribute it now. Or wait for the content to be available on distribution points. Then select **Previous** to have the task sequence search again for the content.

## Prestart commands

You can customize task sequence media or boot images to run a prestart command. A prestart command runs before the task sequence starts. The following actions are some of the more common ones:

- Prompt the user for dynamic values, like the computer name
- Specify network configuration
- Set user device affinity

The prestart command is a command line that you specify with a script or program. The user experience is unique to that script or program.

For more information, see the following articles:

- [Prestart commands for task sequence media](prestart-commands-for-task-sequence-media)
- [Manage boot images](../get-started/manage-boot-images#customization)
- [Task sequence media](../deploy-use/create-task-sequence-media)

## Task sequence progress

When the task sequence runs, it displays the **Installation progress** window:

![Example of the Task Sequence Progress window.](media/task-sequence-progress.png)

- This window is always on top; you can move it, but you can't close or minimize it.
- You can customize the organization name at the top of the window. (The above example shows the default value, `IT Organization`). Change the **Organization name** client setting in the **Computer Agent** group. For more information, see [About client settings](../../core/clients/deploy/about-client-settings#computer-agent).

    Tip

    The task sequence stores this value in the read-only variable [_SMSTSOrgName](task-sequence-variables#SMSTSOrgName).
- You can customize the subheading. (The above example shows the default value, `Running: <task sequence name>`.) On the properties of the task sequence, select the option to **Use custom text** for the progress notification text. It allows a maximum of 255 characters.
- **Running action**: The first line shows the name of the current task sequence step. The progress bar below it shows the overall completion of the task sequence.
- The second line only shows for some steps that provide more detailed progress.
- Use the task sequence variable [TSDisableProgressUI](task-sequence-variables#TSDisableProgressUI) to control when the task sequence displays progress.

    To completely disable the progress window, disable the option to **Show Task Sequence progress** on the **User Experience** page of the task sequence deployment.

The task sequence progress window includes the following information:

- Shows the current step number, total number of steps, and percent completion
- Increased the width of the window to give you more space to better show the organization name in a single line

![Example task sequence progress window.](media/2356386-task-sequence-progress.png)

By default, the task sequence progress window uses the existing text. If you make no changes, it continues to work the same as in earlier versions. To show the progress information, specify the task sequence variable, [TSProgressInfoLevel](task-sequence-variables#TSProgressInfoLevel).

The count and percentage completed are intended for general guidance purposes only. These values are based on the total number of steps in the task sequence. For a more complex task sequence with steps that run conditionally based on task sequence logic, the progress may be non-linear.

The count of total steps doesn't include the following items in the task sequence:

- Groups. This item is a container for other steps, not a step itself.
- Instances of the **Run task sequence** step. This step is a container for other steps.
- Steps that you explicitly disable. A disabled step doesn't run during the task sequence.
- It doesn't count enabled steps in a disabled group.

## Task sequence error

If the task sequence fails, it displays the **Task Sequence Error** window.

![Example task sequence error window.](media/task-sequence-error.png)

- You customize the header information the same as the task sequence progress window.
- It displays the name of the task sequence, an error code, and a general message for users. For example: `Task sequence: Upgrade to Windows 10 Enterprise has failed with the error code (0x80004005). For more information, contact your system administrator or helpdesk operator.`
- The window automatically closes after a timeout period. By default, this timeout is 15 minutes. You can customize this value with the task sequence variable [SMSTSErrorDialogTimeout](task-sequence-variables#SMSTSErrorDialogTimeout).

Starting in version 2103, if the task sequence fails because the client doesn't meet the requirements configured in the [Check readiness](task-sequence-steps#BKMK_CheckReadiness) step, the user can now see more details about the failed prerequisites. They still see the common "task sequence error" message, but can then select an option to **Inspect**. This action shows the checks that failed on the device.

![Task sequence check readiness failure.](media/8888218-task-sequence-check-readiness-failure.png)