---
layout: Conceptual
title: Preprovision BitLocker in Windows PE - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/preprovision-bitlocker-in-windows-pe
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
description: The Preprovision BitLocker task in Configuration Manager enables BitLocker from the Windows Preinstallation Environment before operating system deployment.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9545cfb0-86e7-58ae-8270-5da51d6b28b6
document_version_independent_id: dd8141d6-7588-d1c0-5f2e-1353bc224c0f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/preprovision-bitlocker-in-windows-pe.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/preprovision-bitlocker-in-windows-pe
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/preprovision-bitlocker-in-windows-pe.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2d335c13-683f-109b-308a-26a383fa3f32
---

# Preprovision BitLocker in Windows PE - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The **Pre-provision BitLocker** task sequence step in Configuration Manager allows you to enable BitLocker from the Windows Preinstallation Environment (Windows PE) prior to operating system deployment. Only the used drive space is encrypted, and therefore, encryption times are much faster. This is done with a randomly generated clear protector applied to the formatted volume and encrypting the volume prior to running the Windows setup process. The ability to pre-provision BitLocker was introduced with Windows 8 and Windows Server 2012. However, you can pre-provision BitLocker on a hard drive and install Windows 7 as long as you follow specific steps. After Windows 7 Setup completes, you must set a BitLocker key protector because the Windows 7 BitLocker control panel does not support BitLocker with a clear protector. You must add a key protector by using the **Enable BitLocker** step or by using the manage-bde.exe command-line tool.

Generally, you must do the following to successfully pre-provision BitLocker on a computer that will install Windows 7:

- Restart the computer in Windows PE

    Important

    You must use a boot image with Windows PE 4 or later to pre-provision BitLocker. For more information about supported Windows PE versions in Configuration Manager, see [Dependencies External to Configuration Manager](../plan-design/infrastructure-requirements-for-operating-system-deployment#dependencies-external-to-configuration-manager).
- Partition and format the hard drive
- Pre-provision BitLocker
- Install Windows 7 with specific operating system and network settings
- Add a key protector to BitLocker

    In Configuration Manager, the recommended way to pre-provision BitLocker on a hard drive and install Windows 7 is to create a new task sequence and select **Install an existing image package** from the **Create New Task Sequence** page of the **Create Task Sequence Wizard**. The wizard creates the task sequence steps listed in following table.

Note

The task sequence might have additional steps depending on how you configured the settings in the wizard. For example, you might have the **Capture Windows Settings** step if you selected **Captured Microsoft Windows settings** on the **State Migration** page of the wizard.

| Task sequence step | Details |
| --- | --- |
| Disable BitLocker | This step disables BitLocker encryption, if it is currently enabled. For more information, see [Disable BitLocker](../understand/task-sequence-steps#BKMK_DisableBitLocker). |
| Restart Computer in Windows PE | This step restarts the computer in Windows PE by running the boot image assigned to the task sequence. You must use a boot image with Windows PE 4 or later to pre-provision BitLocker. For more information, see [Restart Computer](../understand/task-sequence-steps#BKMK_RestartComputer). |
| Partition Disk 0 - BIOS Partition Disk 0 - UEFI | These steps format and partition the specified drive on the destination computer by using BIOS or UEFI. The task sequence uses UEFI when it detects that the destination computer is in UEFI mode. For more information, see [Format and Partition Disk](../understand/task-sequence-steps#BKMK_FormatandPartitionDisk). |
| Pre-provision BitLocker | This step enables BitLocker on a drive while in Windows PE. Only the used drive space is encrypted. Because you partitioned and formatted the hard drive in the previous step, there is no data, and encryption completes very quickly. For more information, see [Pre-provision BitLocker](../understand/task-sequence-steps#BKMK_PreProvisionBitLocker). |
| Apply Operating System | This step prepares the answer file that is used to install the operating system on the destination computer and sets the OSDTargetSystemDrive task sequence variable to the drive letter of the partition that contains the operating system files. The answer file and variable are used by the Setup Windows and ConfigMgr step to install the operating system. For more information, see [Apply Operating System Image](../understand/task-sequence-steps#BKMK_ApplyOperatingSystemImage). |
| Apply Windows Settings | This step adds Windows settings to the answer file. The answer file is used by the Setup Windows and ConfigMgr step to install the operating system. For more information, see [Apply Windows Settings](../understand/task-sequence-steps#BKMK_ApplyWindowsSettings). |
| Apply Network Settings | This step adds Network settings to the answer file. The answer file is used by the Setup Windows and ConfigMgr step to install the operating system. For more information, see [Apply Network Settings Step](../understand/task-sequence-steps#BKMK_ApplyNetworkSettings). |
| Apply Device Drivers | This step matches and installs drivers as part of the operating system deployment. For more information, see [Auto Apply Drivers](../understand/task-sequence-steps#BKMK_AutoApplyDrivers). |
| Setup Windows and ConfigMgr | This step performs the transition from Windows PE to the new operating system. This task sequence step is a required part of any operating system deployment. It installs the Configuration Manager client into the new operating system and prepares for the task sequence to continue execution in the new operating system. For more information, see [Setup Windows and ConfigMgr](../understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr). |
| Enable BitLocker | This step enables BitLocker encryption on the hard drive and sets key protectors. Because the hard drive was pre-provisioned with BitLocker, this step completes very quickly. Windows 7 requires that you add a key protector. If you do not use this step, you can run the manage-bde.exe command-line tool to set a key protector. For more information, see [Enable BitLocker](../understand/task-sequence-steps#enable-bitlocker). |