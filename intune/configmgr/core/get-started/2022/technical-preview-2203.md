---
layout: Conceptual
title: Technical preview 2203 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2203
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2203.
ms.date: 2022-03-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: dadb3818-0d33-50c3-2a39-d1d626f34fce
document_version_independent_id: dadb3818-0d33-50c3-2a39-d1d626f34fce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2203.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2203
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2203.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: d0fecf86-20a9-192b-5200-267413bc7769
---

# Technical preview 2203 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2203. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Dark theme for the console

The Configuration Manager console now offers a dark theme. To use the theme, select the arrow from the top left of the ribbon, then choose **Switch console theme**. Select **Switch console theme** again to return to the light theme. Using a console theme can help you easily distinguish a test environment from a production environment or one hierarchy from another.

The console dark theme is a [pre-release](../../servers/manage/pre-release-features) feature. Currently, there are certain locations in the console that may not display the dark theme correctly.

![Screenshot of the Configuration Manager using the dark theme for the console. The 'Switch console theme' option is displayed in the upper right corner of the image.](media/9070525-console-dark-theme.png)

### Known issue

When you first switch to a different theme, you may notice the node navigation pane doesn't properly render when you move to a new workspace. To work around this issue, restart the console.

## Escrow BitLocker recovery password to the site during a task sequence

You can now configure the **Enable BitLocker** step of a task sequence to escrow the BitLocker recovery information for the OS volume to Configuration Manager. Previously, you had to escrow to Active Directory, or wait for the Configuration Manager client to receive BitLocker management policy after the task sequence. This new option makes sure that the device is fully protected by BitLocker when the task sequence completes, and that you can recover the OS volume immediately.

For more general information, see [Plan for BitLocker management](../../../protect/plan-design/bitlocker-management).

### Prerequisites for escrowing BitLocker recovery password during a task sequence

The client will only escrow its key to the Configuration Manager site if you configure one of the following options:

- Create and use a certificate to encrypt the site database for BitLocker management.
- Enable the BitLocker client management policy option to **Allow recovery information to be stored in plain text**.

For more information, see [Encrypt recovery data in the database](../../../protect/deploy-use/bitlocker/encrypt-recovery-data).

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. If needed, first [create a task sequence to deploy an OS](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks).
2. [Use the task sequence editor](../../../osd/understand/task-sequence-editor) to edit the task sequence.
3. If the task sequence doesn't already include the **Enable BitLocker** step, add it. For more information, see [About task sequence steps: Enable BitLocker](../../../osd/understand/task-sequence-steps#enable-bitlocker).
4. On the properties of the **Enable BitLocker** step, select the option to **Automatically store the recovery key**, and then select **The Configuration Manager database**.

    Note

    If Configuration Manager can't escrow the key, by default this task sequence step fails.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### Module changes

The following folder-related cmdlets now support software update groups and deployment packages:

- [Get-CMFolder](/en-us/powershell/module/configurationmanager/get-cmfolder)
- [New-CMFolder](/en-us/powershell/module/configurationmanager/new-cmfolder)
- [Remove-CMFolder](/en-us/powershell/module/configurationmanager/remove-cmfolder)
- [Set-CMFolder](/en-us/powershell/module/configurationmanager/set-cmfolder)
- [Move-CMObject](/en-us/powershell/module/configurationmanager/move-cmobject)
- [Add-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Add-CMObjectSecurityScope)
- [Remove-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Remove-CMObjectSecurityScope)

For more general information, see [Added folder support for nodes in the Software Library](technical-preview-2202#bkmk_folder).

### Modified cmdlets

#### New-CMSoftwareUpdateDeployment

For more information, see [New-CMSoftwareUpdateDeployment](/en-us/powershell/module/configurationmanager/New-CMSoftwareUpdateDeployment).

**Non-breaking changes**

Added parameter **PreDownloadUpdateContent** to support [pre-download for available software updates](technical-preview-2202#bkmk_pre-download).

#### Set-CMSoftwareUpdateDeployment

For more information, see [Set-CMSoftwareUpdateDeployment](/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdateDeployment).

**Non-breaking changes**

Added parameter **PreDownloadUpdateContent** to support [pre-download for available software updates](technical-preview-2202#bkmk_pre-download).