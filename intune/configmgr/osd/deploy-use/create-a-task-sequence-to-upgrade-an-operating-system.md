---
layout: Conceptual
title: Create an OS upgrade task sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system
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
description: Use a task sequence to automatically upgrade Windows to a later version
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7568c6a4-86d8-f9b2-9312-47b36213074f
document_version_independent_id: b69e7008-b92a-af23-fc97-43e11700a96f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b87e604b-8e03-f40b-cd43-31794f2d54d2
---

# Create an OS upgrade task sequence - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use task sequences in Configuration Manager to automatically upgrade an OS on a destination computer. This upgrade can be from Windows 7 or later to Windows 10 or later, or from Windows Server 2012 or later to Windows Server 2016 or later. Create a task sequence that references an OS upgrade package or feature update and any other content to install, such as applications or software updates. The task sequence to upgrade an OS is part of the [Upgrade Windows to the latest version](upgrade-windows-to-the-latest-version) scenario.

Starting in version 2103, you can upgrade by using a feature update deployed with the task sequence. This integration combines the simplicity of Windows servicing with the flexibility of task sequences. Servicing uses content that you synchronize through the software update point. This process simplifies the need to manually get, import, and maintain the Windows image content used with a standard task sequence to upgrade Windows. The size of the servicing ESD file is generally smaller than the OS upgrade package and WIM image file.

## Prerequisites

Before you create the task sequence, make sure the following requirements are in place:

### Required

- An [OS upgrade package](../get-started/manage-operating-system-upgrade-packages) is available in the Configuration Manager console.

    Starting in version 2103, you can also use a feature update. In this case, the OS upgrade package isn't required. For more information, see Requirements for a feature update in a task sequence.
- When upgrading to Windows Server 2016 or later, select the **Ignore any dismissable compatibility messages** setting in the Upgrade Operating System task sequence step. Otherwise the upgrade fails.

### Required (if used)

- Synchronize [software updates](../../sum/get-started/synchronize-software-updates) in the Configuration Manager console.
- Add [applications](../../apps/deploy-use/create-applications) to the Configuration Manager console.

### Requirements for a feature update in a task sequence

- Synchronize the software update point to include the **Upgrades** classification. For more information, see [Configure classifications and products](../../sum/get-started/configure-classifications-and-products).
- For a deployment package that contains the feature update, distribute it to a distribution point that the client can access. For more information, see [Download software updates](../../sum/deploy-use/download-software-updates).

    Note

    If the feature update isn't already downloaded, you can manage the deployment package when you deploy the task sequence.

    When you deploy the task sequence, you can also select the option of **No deployment package** for the feature update. When clients run the task sequence, they download the feature update from peers or the Microsoft cloud.

    The option to **Pre-download content for this task sequence** doesn't apply to feature updates.
- Review the configuration of the following client settings in the [Software Updates](../../core/clients/deploy/about-client-settings#software-updates) group, which are applicable to this scenario:

    - **Specify thread priority for feature updates**: In most instances, set this value to **Normal**.
    - **Enable Dynamic Update for feature updates**: Use this setting to use dynamic update to install language packs, features on demand, drivers, and cumulative updates during Windows Setup. Clients download these other updates from the internet.
    - **Allow clients to download delta content when available**: If you use Windows Delivery Optimization, the content that the client downloads may be much smaller.

#### Known issues with feature updates in a task sequence

Windows 11 Feature Upgrades are not visible to be selected from the Wizard. This happens if the License Terms of the desired Feature Upgrade have not been accepted yet. To do so navigate to the Feature Upgrade and select "Review Licence" from the context menu. Review and Accept the licensing terms to make this Upgrade "deployable".

##### Create a new task sequence

*Applies to version 2103*

If you need to create a new task sequence, you need an OS upgrade package to complete the Create Task Sequence Wizard.

Note

To create a task sequence to upgrade Windows, you typically use the steps in the Process section. The task sequence includes the **Upgrade OS** step, as well as additional recommended steps and groups to handle the end-to-end upgrade process.

You can create a custom task sequence and add the [Upgrade OS](../understand/task-sequence-steps#BKMK_UpgradeOS) step. If you choose this method, also add the [Restart Computer](../understand/task-sequence-steps#BKMK_RestartComputer) step after the **Upgrade OS** step. Make sure to use the setting for **The currently installed default operating system** to restart the computer into the installed OS and not Windows PE.

If you have an existing in-place upgrade task sequence, [edit](../understand/task-sequence-editor#bkmk_edit) or [copy](manage-task-sequences-to-automate-tasks#copy) it. Then change the [Upgrade OS](../understand/task-sequence-steps#BKMK_UpgradeOS) task sequence step to install the feature update.

Starting in version 2107, you can create a new task sequence with just a feature update.

##### Export, import, and migrate task sequences

If you export a task sequence with the **Upgrade OS** step that uses a feature update, the exported task sequence doesn't include the feature update content. When you import the task sequence, readd the **Upgrade OS** step with the feature update.

This behavior is similar if you migrate a task sequence with a feature update between hierarchies.

##### Create prestaged content file

You can't currently use the action to **Create prestaged content file** for a task sequence with a feature update.

##### Create standalone media

Standalone media isn't supported for a task sequence with a feature update. When you try to create standalone media, it fails with entries similar to the following in CreateTSMedia.log:

```log
Unable to retrieve policy for Task Sequence XYZ004BD from site XYZ.
Failed to initialize.... Verify the user is authorized to create Task Sequence media and has local admin permissions.
MediaGenerator::~MediaGenerator()
Failed to create media generator (0x80070490)
CreateTsMedia failed with error 0x80070490, details=''
Media temp directory 'C:\Users\jqpublic\AppData\Local\Temp\_tsmedia_1053544' is fully cleared
Media creation process that was started from Admin Console completed.
CreateMedia.exe finished with error code 80070490
```

## Process

To upgrade the OS on clients, create a task sequence and select **Upgrade an operating system from upgrade package** in the Create Task Sequence Wizard. The wizard adds the task sequence steps to upgrade the OS, apply software updates, and install applications.

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select **Task Sequences**.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Task Sequence**.
3. On the **Create a New Task Sequence** page of the Create Task Sequence Wizard, select **Upgrade an operating system from an upgrade package**, and then select **Next**.
4. On the **Task Sequence Information** page, specify the following settings:

    - **Task sequence name**: Specify a name that identifies the task sequence.
    - **Description**: Optionally specify a description.
5. On the **Upgrade the Windows Operating System** page, specify the following settings:

    - **Upgrade package**: Specify the upgrade package that contains the OS upgrade source files. Verify that you've selected the correct upgrade package by looking at the information in the **Properties** pane. For more information, see [Manage OS upgrade packages](../get-started/manage-operating-system-upgrade-packages).
    - **Edition index**: If there are multiple OS edition indexes available in the package, select the edition index you want. By default, the wizard selects the first index.
    - **Product key**: Specify the Windows product key for the OS to install. Specify encoded volume license keys or standard product keys. If you use a standard product key, separate each group of five characters by a dash (`-`). For example: `XXXXX-XXXXX-XXXXX-XXXXX-XXXXX`. When the upgrade is for a volume license edition, the product key may not be required.

        Note

        This product key can be a multiple activation key (MAK), or a generic volume licensing key (GVLK). A GVLK is also referred to as a key management service (KMS) client setup key. For more information, see [Plan for volume activation](/en-us/windows/deployment/volume-activation/plan-for-volume-activation-client). For a list of KMS client setup keys, see [KMS client setup keys](/en-us/windows-server/get-started/kmsclientkeys) in the Windows Server activation guide.
    - **Ignore any dismissable compatibility messages**: Select this setting if you're upgrading to Windows Server 2016 or later. If you don't select this setting, the task sequence fails to complete because Windows Setup is waiting for the user to select **Confirm** on a Windows app compatibility dialog.
6. On the **Include Updates** page, specify whether to install required, all, or no software updates. Then select **Next**. If you specify to install software updates, Configuration Manager installs only those updates targeted to the collections of which the destination computer is a member.
7. On the **Install Applications** page, specify the applications to install on the destination computer, and then select **Next**. If you select more than one application, also specify whether the task sequence should continue if the installation of a specific application fails.
8. Complete the wizard.

Important

When the task sequence runs on a device, the Configuration Manager client creates several scripts to control the task sequence behavior in various scenarios. When the task sequence completes, the client doesn't remove these scripts until the computer restarts. These script files don't contain sensitive information.

## Customize

The default task sequence template for in-place upgrade includes other groups with recommended actions to add before and after the upgrade process. These actions are common among many customers who are successfully upgrading devices to Windows 10 or later. For more information, see [In-place upgrade recommendations](../understand/in-place-upgrade-recommendations).