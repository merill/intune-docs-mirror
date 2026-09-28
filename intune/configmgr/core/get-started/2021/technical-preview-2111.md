---
layout: Conceptual
title: Technical preview 2111 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2111
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2111.
ms.date: 2021-11-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 10294430-e325-f267-a8f2-b732a42234c7
document_version_independent_id: 10294430-e325-f267-a8f2-b732a42234c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2111.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2111
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2111.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 001becf5-c971-2cac-5a26-f45e0306c957
---

# Technical preview 2111 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2111. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Improvements to the Windows servicing dashboard

We now display a **Windows 11 Latest Feature Updates** chart in the **Windows Servicing** dashboard. The new chart makes it easier to determine how many of your Windows 11 clients are on the latest feature update. To display the dashboard, go to **Software Library** &gt; **Overview** &gt; **Windows Servicing**.

![Screenshot of the Windows servicing dashboard. The Windows 11 Latest Feature Updates chart is displayed in the dashboard](media/10579996-windows-servicing-dashboard.png)

## Co-management Eligible Devices collection

There's a new built-in device collection for **Co-management Eligible Devices**. The **Co-management Eligible Devices** collection uses incremental updates and a daily full update to keep the collection up to date.

## Improvement to app groups

This release resolves one of the [known issues for app groups from version 2110](technical-preview-2110#bkmk_appgroups). View and managing app groups in the Microsoft Intune admin center doesn't require an elevated role. It honors permissions and scopes as defined in Configuration Manager. For example, your user account requires the **Approve** permission on an app group to approve it for installation from the admin center. This behavior is consistent with applications.

## Improvement to task sequence deployment type

Consider the following scenario:

- An application has a [task sequence deployment type](../../../apps/get-started/creating-windows-applications#bkmk_tsdt).
- It's deployed as available.
- A device has maintenance windows defined.
- A user on the device runs the deployment in Software Center outside of a maintenance window.

Configuration Manager honors the user's intent to install the application, even though there's no available maintenance window. Previously, when the task sequence ran, the **Restart Computer** step would fail because of the maintenance window.

Based on your feedback, this step now ignores maintenance windows only when the task sequence is run as an app deployment type.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets for orchestration groups

For more general information about this feature, see [Orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

#### Get-CMOrchestrationGroup

Use this cmdlet to get an orchestration group object by name or ID. You can use this object with Invoke-CMOrchestrationGroup, Remove-CMOrchestrationGroup, or Set-CMOrchestrationGroup.

#### Invoke-CMOrchestrationGroup

Use this cmdlet to [start orchestration](../../../sum/deploy-use/create-orchestration-groups#start-orchestration).

```powershell
Get-CMOrchestrationGroup -Name $OGName | Invoke-CMOrchestrationGroup -IgnoreServiceWindow $true
```

#### New-CMOrchestrationGroup

Use this cmdlet to create a new orchestration group.

```powershell
New-CMOrchestrationGroup -Name $Script:OGName -SiteCode $SiteCode -Description "Desc" -OrchestrationType Percentage -OrchestrationValue 10 -OrchestrationTimeOutMin 300 -MaxLockTimeOutMin 55 -PreScript "PreScript" -PreScriptTimeoutSec 30 -PostScript "PostScript" -PostScriptTimeoutSec 55 -MemberResourceIds $Script:device.ResourceID
```

#### Remove-CMOrchestrationGroup

Use this cmdlet to remove the specified orchestration group.

#### Set-CMOrchestrationGroup

Use this cmdlet to configure an orchestration group.

### Deprecated cmdlets

The **Remove-CMDeploymentTypeSupersedence** cmdlet for deployment type supersedence is deprecated and may be removed in a future release. Instead, use the new [Set-CMApplicationSupersedence](technical-preview-2109#set-cmapplicationsupersedence) cmdlet.

### Modified cmdlets

#### Add-CMDeviceCollectionDirectMembershipRule

For more information, see [Add-CMDeviceCollectionDirectMembershipRule](/en-us/powershell/module/configurationmanager/Add-CMDeviceCollectionDirectMembershipRule).

**Bugs that were fixed**

Fixed an issue when adding a rule by resource object.

#### Get-CMClientSetting

For more information, see [Get-CMClientSetting](/en-us/powershell/module/configurationmanager/Get-CMClientSetting).

**Non-breaking changes**

Added support to return the value for the [Disable Deadline Randomization](../../clients/deploy/about-client-settings#disable-deadline-randomization) setting in the Computer Agent group.

#### New-CMBoundary

For more information, see [New-CMBoundary](/en-us/powershell/module/configurationmanager/New-CMBoundary).

**Non-breaking changes**

Added new parameter **ValueStartsWith** to support [Improvements to VPN boundary types](technical-preview-2109#bkmk_vpn).

#### New-CMTSStepApplyWindowsSetting

For more information, see [New-CMTSStepApplyWindowsSetting](/en-us/powershell/module/configurationmanager/New-CMTSStepApplyWindowsSetting).

**Breaking changes**

Removed the following unsupported parameters:

- **MaximumConnection**
- **ServerLicensing**

#### New-CMTSPartitionSetting

For more information, see [New-CMTSPartitionSetting](/en-us/powershell/module/configurationmanager/New-CMTSPartitionSetting).

**Non-breaking changes**

Set default value for AssignVolumeLetter.

#### New-CMTSStepPrestartCheck

For more information, see [New-CMTSStepPrestartCheck](/en-us/powershell/module/configurationmanager/New-CMTSStepPrestartCheck).

**Non-breaking changes**

Added new parameters for [TPM existence check](technical-preview-2110#bkmk_tpm):

- **CheckTpmEnabled**
- **CheckTpmActivated**

#### New-CMWdacSetting

For more information, see [New-CMWdacSetting](/en-us/powershell/module/configurationmanager/New-CMWdacSetting).

**Non-breaking changes**

Added support for new platform rules for Windows 10 ARM64 and Windows 10 multi-session.

#### Remove-CMPersistentUserSettingsGroup

For more information, see [Remove-CMPersistentUserSettingsGroup](/en-us/powershell/module/configurationmanager/Remove-CMPersistentUserSettingsGroup).

**Bugs that were fixed**

Fixed a query issue when remove settings group by name.

#### Set-CMTSStepPrestartCheck

For more information, see [Set-CMTSStepPrestartCheck](/en-us/powershell/module/configurationmanager/Set-CMTSStepPrestartCheck).

**Non-breaking changes**

Added new parameters for [TPM existence check](technical-preview-2110#bkmk_tpm):

- **CheckTpmEnabled**
- **CheckTpmActivated**

#### Set-CMBoundary

For more information, see [Set-CMBoundary](/en-us/powershell/module/configurationmanager/Set-CMBoundary).

**Non-breaking changes**

Added new parameter **ValueStartsWith** to support [Improvements to VPN boundary types](technical-preview-2109#bkmk_vpn).

#### Set-CMDistributionPoint

For more information, see [Set-CMDistributionPoint](/en-us/powershell/module/configurationmanager/Set-CMDistributionPoint).

**Non-breaking changes**

Added new parameter **EnableMaintenanceMode** to support to manage [maintenance mode](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_maint).

#### Set-CMSoftwareUpdatePoint

For more information, see [Set-CMSoftwareUpdatePoint](/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdatePoint).

**Bugs that were fixed**

Fixed an issue with regular expression processing when trying to clear the WSUS access account from a software update point.

#### Set-CMTSStepApplyWindowsSetting

For more information, see [Set-CMTSStepApplyWindowsSetting](/en-us/powershell/module/configurationmanager/Set-CMTSStepApplyWindowsSetting).

**Breaking changes**

Removed the following unsupported parameters:

- **MaximumConnection**
- **ServerLicensing**