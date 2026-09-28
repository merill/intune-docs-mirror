---
layout: Conceptual
title: Technical preview 2104 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2104
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2104.
ms.date: 2021-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: c10d3288-723a-5896-1139-1c16c33abb57
document_version_independent_id: d629ea2e-7dcf-8868-b18e-085aad88a7e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2104.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2104
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2104.md
platformId: d3fad20f-8bf0-7a28-bc99-8ddbf15b5eeb
---

# Technical preview 2104 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2104. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Tenant attach: BitLocker recovery keys

You can now get BitLocker recovery keys for a [tenant-attached device](../../../tenant-attach/device-sync-actions) from the Microsoft Intune admin center. For example, a help desk technician who doesn't have access to Configuration Manager could use the web-based admin center to help an end user get a recovery key for their device.

Since this feature is still in preview, you need to access it from the **Admin center preview** option from the Configuration Manager console of the technical preview branch.

### Prerequisites for BitLocker recovery keys with tenant attach

- The administrative user needs the following permissions:

    - On the **Collection** object that's scoped to a collection that includes the device:

        - **Read**
        - **Read BitLocker Recovery Key**
    - An [Intune role](../../../../fundamentals/role-based-access-control/overview) assigned to the user
- Apply a Configuration Manager [BitLocker management](../../../protect/deploy-use/bitlocker/deploy-management-agent) policy to the device.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/find-help#product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node.
2. Select a device. In the **Device** group on the ribbon, select **Start**, and then select **Admin center preview**. This action opens the preview version of the Microsoft Intune admin center in the default browser.
3. In the admin center preview, select **Recovery keys** in the device menu. You'll see the list of encrypted drives on the device.
4. To display a recovery key for a drive, select **Show recovery key**. This action discloses the recovery key, which causes the device to rotate its recovery key. Select **Yes** to continue and view the key.
5. A pane to the right displays the device information, including the BitLocker recovery key. Select the copy icon to copy the key to the clipboard. This action makes it easier to share with a user.

![Microsoft Intune admin center (preview) Recovery Keys](media/6979225-bitlocker-recovery-key.png)

## Tenant attach: Historical inventory data in resource explorer

Resource explorer can display a historical view of the device inventory in the Microsoft Intune admin center. Since this feature is still in preview, you'll need to access it from the **Admin center preview** option from the Configuration Manager console of the technical preview branch.

[![Screenshot of choosing a date from Resource explorer in the Microsoft Intune admin center ](media/9546584-resource-explorer-historical-inventory.png)](media/9546584-resource-explorer-historical-inventory.png#lightbox)

### Try it out!

Try to complete the tasks. Then send [Feedback](/en-us/configmgr/core/understand/find-help#product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node.
2. Select a device. In the **Device** group on the ribbon, select **Start**, and then select **Admin center preview**. This action opens the preview version of the Microsoft Intune admin center in the default browser.
3. From the admin center preview, select **Resource explorer**.
4. Select a class, then enter a custom date in the date time picker to get historical inventory data.

## Tenant attach: Offboarding

While we know customers get enormous value by enabling tenant attach, there are rare cases where you might need to offboard a hierarchy. For example, you may need to offboard following a disaster recovery scenario where the on-premises environment was removed. Follow the steps below to remove your Configuration Manager hierarchy from the Microsoft Intune admin center:

1. Navigate to https://aka.ms/taoffboard.
2. Select **Tenant administration** then **Connectors and tokens**.
3. Select **Microsoft Endpoint Configuration Manager (Preview)**.
4. Choose the name of the site you would like to offboard, then select **Delete**.
    - This option is only visible for 2104 technical preview sites.

## Support layered keyboard driver during OS deployment

Based on your feedback, this release adds support for layered keyboard drivers during OS deployment. This driver specifies other types of keyboards that are common with Japanese and Korean languages. For more information, see the [LayeredDriver](/en-us/windows-hardware/customize/desktop/unattend/microsoft-windows-international-core-winpe-layereddriver) setting.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/find-help#product-feedback) with your thoughts on the feature.

1. [Create a task sequence](../../../osd/deploy-use/create-a-task-sequence-to-install-an-operating-system) to install an OS image.
2. [Edit the task sequence](../../../osd/understand/task-sequence-editor#bkmk_edit).
3. On the **Apply OS Image** step, in the section to **Select layered driver if applicable**, choose one of the following options:

    - **Do not specify** (`0`): This option is the default, which doesn't configure the LayeredDriver setting in the unattend.xml. This behavior is consistent with previous versions of Configuration Manager.
    - **PC/AT Enhanced keyboard (101/102-key)** (`1`)
    - **Korean PC/AT 101-Key Compatible keyboard or the Microsoft Natural keyboard (type 1)** (`2`)
    - **Korean PC/AT 101-Key Compatible keyboard or the Microsoft Natural keyboard (type 2)** (`3`)
    - **Korean PC/AT 101-Key Compatible keyboard or the Microsoft Natural keyboard (type 3)** (`4`)
    - **Korean keyboard (103/106-key)** (`5`)
    - **Japanese keyboard (106/109-key)** (`6`)
4. [Deploy the task sequence](../../../osd/deploy-use/deploy-a-task-sequence).

You can also use the new **OsdLayeredDriver** task sequence variable. Use the integer values noted after each option to configure this variable. The smsts.log file displays the integer value for this setting when the task sequence runs.

## Improvements to Support Center

Starting in this technical preview, the **Content** view in the **Support Center Client Tools** has been renamed to **Deployments**. From **Deployments**, you can review all of the deployments currently targeted to the device. The new view is grouped by **Category** and **Status**. The view can be sorted and filtered to help you find the deployments you're interested in. Select a deployment in the results pane to display more information in the details pane.

## Run software updates evaluation from deployment status

You can now right-click and notify devices to run a software updates evaluation cycle from the [software update deployment status](../../../sum/deploy-use/monitor-software-updates#BKMK_SUDeployStatus). You can target a single device under the **Asset Details** pane or select a group of devices based on their deployment status.

![Screenshot of the right-click action for software updates deployment evaluation from the software update deployment status](media/9012080-run-software-update-deployment-evaluation.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/find-help#product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, navigate to **Monitoring** &gt; **Overview** &gt; **Deployments**.
2. Select the software update group or software update for which you want to monitor the deployment status.
3. On the Home tab, in the Deployment group, select **View Status**.
4. Right-click on either a specific deployment status for the devices, or on a single device under **Asset Details** pane.
5. Select **Evaluate Software Update Deployments** to send a notification to the selected devices to run an evaluation cycle for software update deployments.

## Improvements to CMTrace

This release includes multiple performance improvements to the CMTrace log viewer. Configuration Manager automatically installs this tool in the following locations:

- The site server's tools directory. For example: `cd.latest\SMSSETUP\Tools\CMTrace.exe`
- The Management point's installation directory. For example: `C:\SMS_CCM\CMTrace.exe`
- The client installation directory. For example: `C:\Windows\CCM\CMTrace.exe`
- OS deployment boot images. For example: `X:\sms\bin\x64\CMTrace.exe`

If you have a copy of CMTrace in another location, consider removing it and using a copy in one of the default paths. If it's in a custom location that meets your business requirements, then make sure you have a process to keep it up to date. If your custom location might be of benefit to other customers, file [product feedback](../../understand/find-help#product-feedback).

For more information, see [Direct links to Community hub items](../../servers/manage/community-hub#bkmk_deeplink).

Tip

**OneTrace** is the log viewer with Support Center. It works similarly to CMTrace, with many improvements. For more information, see [Support Center OneTrace](../../support/support-center-onetrace).

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in technical preview version 2104.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### Modified cmdlets

#### Get-CMApplicationGroup

**Bugs that were fixed**

Fixed an issue to get the correct app group path.

#### Import-CMQuery

**Bugs that were fixed**

Fixed an issue to unblock the import function.

#### New-CMSoftwareUpdateDeployment

**Non-breaking changes**

Added **Description** alias to **Comment** parameter.

#### Set-CMTSStepUpgradeOperatingSystem

**Non-breaking changes**

Added new parameter **SoftwareUpdate** to specify a feature update for the [Upgrade OS](../../../osd/understand/task-sequence-steps#BKMK_UpgradeOS) task sequence step.

#### Remove-CMApplicationGroup

**Bugs that were fixed**

Fixed an issue to get the correct app group path when using the pipeline.

#### Set-CMClientSetting

**Non-breaking changes**

Added a meaningful deprecation message for the **SoftwareMetering** parameter.

#### Set-CMMsiDeploymentType

**Bugs that were fixed**

Update the deployment type according to the installer type to avoid resetting the configurations when you change the content location.

**Non-breaking changes**

Add support for specifying a folder path to the **ContentLocation** parameter.