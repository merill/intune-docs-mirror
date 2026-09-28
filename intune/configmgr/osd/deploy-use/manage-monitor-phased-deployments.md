---
layout: Conceptual
title: Manage & monitor phased deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/manage-monitor-phased-deployments
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
description: Understand how to manage and monitor phased deployments for software in Configuration Manager.
ms.date: 2020-08-21T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8492cdb5-f3ad-c159-a949-bc9098de5687
document_version_independent_id: 7e5cff3d-0da0-1040-4fcf-61b63f272481
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/manage-monitor-phased-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/manage-monitor-phased-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/manage-monitor-phased-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab06385-661e-4214-8870-bbe4071c960d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/131ba09e-4280-4ae7-8622-1f9f1c0daad1
platformId: aaeeca2f-6f8a-ebf7-5c89-580e20f089ee
---

# Manage & monitor phased deployments - Configuration Manager | Microsoft Learn

This article describes how to manage and monitor phased deployments. Management tasks include manually beginning the next phase, and suspend or resume a phase.

First, you need to create a phased deployment:

- [Application](create-phased-deployment-for-task-sequence?toc=/mem/configmgr/apps/toc.json&amp;bc=/mem/configmgr/apps/breadcrumb/toc.json)
- [Software update](create-phased-deployment-for-task-sequence?toc=/mem/configmgr/sum/toc.json&amp;bc=/mem/configmgr/sum/breadcrumb/toc.json)
- [Task sequence](create-phased-deployment-for-task-sequence)

## Move to the next phase

When you select the setting, **Manually begin the second phase of deployment**, the site doesn't automatically start the next phase based on success criteria. You need to move the phased deployment to the next phase.

1. How to start this action varies based on the type of deployed software:

    - **Application**: Go to the **Software Library** workspace, expand **Application Management**, and select **Applications**.
    - **Software update**: Go to the **Software Library** workspace, and then select one of the following nodes:

        - Software Updates
            - **All Software Updates**
            - **Software Update Groups**
        - Windows Servicing, **All Windows Updates**
        - Office 365 Client Management, **Office 365 Updates**
    - **Task sequence**: Go to the **Software Library** workspace, expand **Operating Systems**, and select **Task Sequences**.
2. Select the software with the phased deployment.
3. In the details pane, switch to the **Phased Deployments** tab.
4. Select the phased deployment, and click **Move to next phase** in the ribbon.

    ![Right-click menu showing actions on a phased deployment.](media/suspend-phased-deployment.png)

Optionally, use the following Windows PowerShell cmdlet for this task: [Move-CMPhasedDeploymentToNext](/en-us/powershell/module/configurationmanager/move-cmphaseddeploymenttonext).

## Suspend and resume phases

You can manually suspend or resume a phased deployment. For example, you create a phased deployment for a task sequence. While monitoring the phase to your pilot group, you notice a large number of failures. You suspend the phased deployment to stop further devices from running the task sequence. After resolving the issue, you resume the phased deployment to continue the rollout.

1. How to start this action varies based on the type of deployed software:

    - **Application**: Go to the **Software Library** workspace, expand **Application Management**, and select **Applications**.
    - **Software update**: Go to the **Software Library** workspace, and then select one of the following nodes:

        - Software Updates
            - **All Software Updates**
            - **Software Update Groups**
        - Windows Servicing, **All Windows Updates**
        - Office 365 Client Management, **Office 365 Updates**
    - **Task sequence**: Go to the **Software Library** workspace, expand **Operating Systems**, and select **Task Sequences**. Select an existing task sequence, and then click **Create Phased Deployment** in the ribbon.
2. Select the software with the phased deployment.
3. In the details pane, switch to the **Phased Deployments** tab.
4. Select the phased deployment, and click **Suspend** or **Resume** in the ribbon.

Note

Starting on April 21, 2020, Office 365 ProPlus is being renamed to **Microsoft 365 Apps for enterprise**. For more information, see [Name change for Office 365 ProPlus](/en-us/deployoffice/name-change). You may still see the old name in the Configuration Manager product and documentation while the console is being updated.

Optionally, use the following Windows PowerShell cmdlets for this task:

- [Suspend-CMPhasedDeployment](/en-us/powershell/module/configurationmanager/suspend-cmphaseddeployment)
- [Resume-CMPhasedDeployment](/en-us/powershell/module/configurationmanager/resume-cmphaseddeployment)

## Monitor

Phased deployments have their own dedicated monitoring node, making it easier to identify phased deployments you have created and navigate to the phased deployment monitoring view. From the **Monitoring** workspace, select **Phased Deployments**, then double-click one of the phased deployments to see the status. 

![Phased deployment status dashboard showing status of two phases](media/1358577-phased-deployment-status.png)

This dashboard shows the following information for each phase in the deployment:

- **Total devices** or **Total resources**: How many devices are targeted by this phase.
- **Status**: The current status of this phase. Each phase can be in one of the following states:

    - **Deployment created**: The phased deployment created a deployment of the software to the collection for this phase. Clients are actively targeted with this software.
    - **Waiting**: The previous phase hasn't yet reached the success criteria for the deployment to continue to this phase.
    - **Suspended**: An administrator suspended the deployment.
- **Progress**: The color-coded deployment states from clients. For example: Success, In Progress, Error, Requirements Not Met, and Unknown.

### Success criteria tile

Use the **Select Phase** drop-down list to change the display of the **Success Criteria** tile. This tile compares the **Phase Goal** against the current compliance of the deployment. With the default settings, the phase goal is 95%. This value means that the deployment needs a 95% compliance to move to the next phase.

In the example, the phase goal is 65%, and the current compliance is 66.7%. The phased deployment automatically moved to the second phase, because the first phase met the success criteria.

![Example Success Criteria tile from Phased Deployment Status where goal is 65%](media/pod-status-success-criteria-tile.png)

The phase goal is the same as the **Deployment success percentage** on the Phase Settings for the *next* phase. For the phased deployment to start the next phase, that second phase defines the criteria for success of the first phase. To view this setting:

1. Go to the phased deployment object on the software, and open the Phased Deployment Properties.
2. Switch to the **Phases** tab. Select **Phase 2** and click **View**.
3. In the phase Properties window, switch to the **Phase Settings** tab.
4. View the value for **Deployment success percentage** in the *Criteria for success of the previous phase* group.

For example, the following properties are for the same phase as the success criteria tile shown above where the criteria is 65%:

![Phase settings tab on phase properties](media/phase-properties-phase-settings.png)

## PowerShell

Use the following Windows PowerShell cmdlets to manage phased deployments:

### Automatically create phased deployments

- [New-CMApplicationAutoPhasedDeployment](/en-us/powershell/module/configurationmanager/new-cmapplicationautophaseddeployment)
- [New-CMSoftwareUpdateAutoPhasedDeployment](/en-us/powershell/module/configurationmanager/new-cmsoftwareupdateautophaseddeployment)
- [New-CMTaskSequenceAutoPhasedDeployment](/en-us/powershell/module/configurationmanager/new-cmtasksequenceautophaseddeployment)

### Manually create phased deployments

- [New-CMSoftwareUpdatePhase](/en-us/powershell/module/configurationmanager/new-cmsoftwareupdatephase)
- [New-CMSoftwareUpdateManualPhasedDeployment](/en-us/powershell/module/configurationmanager/new-cmsoftwareupdatemanualphaseddeployment)
- [New-CMTaskSequencePhase](/en-us/powershell/module/configurationmanager/new-cmtasksequencephase)
- [New-CMTaskSequenceManualPhasedDeployment](/en-us/powershell/module/configurationmanager/new-cmtasksequencemanualphaseddeployment)

### Get existing phased deployment objects

- [Get-CMApplicationPhasedDeployment](/en-us/powershell/module/configurationmanager/get-cmapplicationphaseddeployment)
- [Get-CMSoftwareUpdatePhasedDeployment](/en-us/powershell/module/configurationmanager/get-cmsoftwareupdatephaseddeployment)
- [Get-CMTaskSequencePhasedDeployment](/en-us/powershell/module/configurationmanager/get-cmtasksequencephaseddeployment)
- [Get-CMPhase](/en-us/powershell/module/configurationmanager/get-cmphase)

### Monitor phased deployment status

- [Get-CMPhasedDeploymentStatus](/en-us/powershell/module/configurationmanager/get-cmphaseddeploymentstatus)

### Manage existing phased deployments

- [Move-CMPhasedDeploymentToNext](/en-us/powershell/module/configurationmanager/move-cmphaseddeploymenttonext)
- [Resume-CMPhasedDeployment](/en-us/powershell/module/configurationmanager/resume-cmphaseddeployment)
- [Suspend-CMPhasedDeployment](/en-us/powershell/module/configurationmanager/suspend-cmphaseddeployment)

### Modify existing phased deployments

- [Set-CMApplicationPhasedDeployment](/en-us/powershell/module/configurationmanager/set-cmapplicationphaseddeployment)
- [Set-CMSoftwareUpdatePhase](/en-us/powershell/module/configurationmanager/set-cmsoftwareupdatephase)
- [Set-CMSoftwareUpdatePhasedDeployment](/en-us/powershell/module/configurationmanager/set-cmsoftwareupdatephaseddeployment)
- [Set-CMTaskSequencePhase](/en-us/powershell/module/configurationmanager/set-cmtasksequencephase)
- [Set-CMTaskSequencePhasedDeployment](/en-us/powershell/module/configurationmanager/set-cmtasksequencephaseddeployment)
- [Remove-CMApplicationPhasedDeployment](/en-us/powershell/module/configurationmanager/remove-cmapplicationphaseddeployment)
- [Remove-CMSoftwareUpdatePhasedDeployment](/en-us/powershell/module/configurationmanager/remove-cmsoftwareupdatephaseddeployment)
- [Remove-CMTaskSequencePhasedDeployment](/en-us/powershell/module/configurationmanager/remove-cmtasksequencephaseddeployment)