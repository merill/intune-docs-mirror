---
layout: Conceptual
title: Technical preview 2206 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2206
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2206.
ms.date: 2022-06-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: d54858c5-2ec7-7cda-d14b-707552197531
document_version_independent_id: d54858c5-2ec7-7cda-d14b-707552197531
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2206.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2206
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2206.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 290df796-aa9a-27fd-d693-125234d067db
---

# Technical preview 2206 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2206. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Default site boundary group behavior to support cloud source selection

You can now add options via PowerShell to include and prefer cloud management gateway (CMG) management points for the default site boundary group. When a site is set up, there's a default site boundary group created for each site and all the clients are by default mapped to it until they're assigned to some custom boundary group.

Currently on the admin console, you can add references to default site boundary group, but the added references don't have any effect when the client requests for management point list. Starting with technical preview version 2206, you can use PowerShell cmdlets to include and prefer cloud-based sources for clients in the default site boundary group. This action is currently only for the management point role.

Note

You can't currently configure this behavior from the Configuration Manager console. For more information on configuring this behavior with PowerShell, see the cmdlet details in the following section.

### Set-CMDefaultBoundaryGroup

Use this cmdlet to modify the properties of a default site boundary group. You can set the options to include and prefer the cloud-based sources for the clients in default site boundary group.

#### Syntax

```powershell
Set-CMDefaultBoundaryGroup [-IncludeCloudBasedSources <Boolean>] [-PreferCloudBasedSources <Boolean>] 
```

#### Examples

```powershell
Set-CMDefaultBoundaryGroup -IncludeCloudBasedSources $true -PreferCloudBasedSources $true 

Set-CMDefaultBoundaryGroup -IncludeCloudBasedSources $true 

Set-CMDefaultBoundaryGroup -IncludeCloudBasedSources $true -PreferCloudBasedSources $false 
```

#### Parameters

- **IncludeCloudBasedSources**: Used to specify whether admin wants to include the cloud-based sources in the management point list for the clients in default site boundary group.
- **PreferCloudBasedSources**: Used to specify whether admin wants to prefer the cloud-based sources in the management point list for the clients in default site boundary group. On selecting this option, cloud-based servers will be given preference by the clients.

Note

You can only set this option to true if the parameter IncludeCloudBasedSources is set to true or was already set to true by admin.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Approve-CMOrchestrationGroupScript

Use this cmdlet to approve an orchestration group script. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name $Script:OGName
$preScript = $referenceOG | Get-CMOrchestrationGroupScript -ScriptType Pre
$preScript | Approve-CMOrchestrationGroupScript -Comment "Approve"
Approve-CMOrchestrationGroupScript -ScriptGuid $PreScript.ScriptGuid
```

#### Deny-CMOrchestrationGroupScript

Use this cmdlet to deny an orchestration group script. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name $Script:OGName
$preScript = $referenceOG | Get-CMOrchestrationGroupScript -ScriptType Pre
$preScript | Deny-CMOrchestrationGroupScript -Comment "Deny"
Deny-CMOrchestrationGroupScript -ScriptGuid $PreScript.ScriptGuid -Comment "Deny"
```

#### Get-CMOrchestrationGroupScript

Use this cmdlet to get a script from the specified orchestration group. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name $Script:OGName
$preScript = $referenceOG | Get-CMOrchestrationGroupScript -ScriptType Pre
```

#### Get-CMTrustedRootCertificationAuthority

Use this cmdlet to get the certificates for trusted root certification authorities from the site.

```powershell
$ci =Get-CMTrustedRootCertificationAuthority
$ci =Get-CMTrustedRootCertificationAuthority -ViewDetail
```

#### New-CMAADClientApplication

Use this cmdlet to create a client app registration in Microsoft Entra ID. When you run this cmdlet, it will prompt you to sign in to your tenant. For more information on this app registration, see [Manually register Microsoft Entra apps for the CMG](../../clients/manage/cmg/manually-register-azure-ad-apps).

```powershell
$serverApp = New-CMAADServerApplication -AppName $appName
New-CMAADClientApplication -AppName $name -InputObject $serverApp
```

#### New-CMAADServerApplication

Use this cmdlet to create a server app registration in Microsoft Entra ID. When you run this cmdlet, it will prompt you to sign in to your tenant. For more information on this app registration, see [Manually register Microsoft Entra apps for the CMG](../../clients/manage/cmg/manually-register-azure-ad-apps).

```powershell
New-CMAADServerApplication -AppName $appName
```

### Modified cmdlets

#### Add-CMComplianceSettingWqlQuery

For more information, see [Add-CMComplianceSettingWqlQuery](/en-us/powershell/module/configurationmanager/Add-CMComplianceSettingWqlQuery).

**Non-breaking changes**

When using this cmdlet, you can now specify $null value to the parameter **WhereClause**.

#### Add-CMManagementPoint

For more information, see [Add-CMManagementPoint](/en-us/powershell/module/configurationmanager/Add-CMManagementPoint).

**Non-breaking changes**

When you use this cmdlet to enable communication with the cloud management gateway, it now by default configures the management point to support both internet and intranet clients.

#### Get-CMNotification

For more information, see [Get-CMNotification](/en-us/powershell/module/configurationmanager/Get-CMNotification).

**Non-breaking changes**

You can now use this cmdlet to get built-in notification by using parameter **IsBuiltIn**. You can now also use this cmdlet to get notification that could be dismissed by using parameter **CanDismiss**.

#### Get-CMObjectSecurityScope

For more information, see [Get-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Get-CMObjectSecurityScope).

**Non-breaking changes**

You can now use this cmdlet to get the security scope of a specified folder object.

#### New-CMCloudManagementGateway

For more information, see [New-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/New-CMCloudManagementGateway).

**Non-breaking changes**

Added parameters **VMSSVMSize** and **Version** to support creating a cloud management gateway (CMG) using a virtual machine scale set.

#### New-CMComplianceRuleRegistryKeyPermission

For more information, see [New-CMComplianceRuleRegistryKeyPermission](/en-us/powershell/module/configurationmanager/New-CMComplianceRuleRegistryKeyPermission).

**Non-breaking changes**

Fixed an issue in **OperandDataType** property when creating a rule.

#### Set-CMClientSettingClientCache

For more information, see [Set-CMClientSettingClientCache](/en-us/powershell/module/configurationmanager/Set-CMClientSettingClientCache).

**Non-breaking changes**

Added a new parameter **MinCacheTombstoneContentMins** to support setting the minimum duration before the client can remove cached content.

#### Set-CMClientSettingComplianceSetting

For more information, see [Set-CMClientSettingComplianceSetting](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComplianceSetting).

**Non-breaking changes**

Added a new parameter **ScriptExecutionTimeoutSecs** to extend the script execution timeout value.

#### Set-CMClientSettingEndpointProtection

For more information, see [Set-CMClientSettingEndpointProtection](/en-us/powershell/module/configurationmanager/Set-CMClientSettingEndpointProtection).

**Non-breaking changes**

You can now specify the defender agent type with the new parameter **DefenderAgent**.

#### Set-CMComplianceSettingWqlQuery

For more information, see [Set-CMComplianceSettingWqlQuery](/en-us/powershell/module/configurationmanager/Set-CMComplianceSettingWqlQuery).

**Non-breaking changes**

When using this cmdlet, you can now specify $null value to the parameter **WhereClause**.

#### Set-CMClientSettingComputerRestart

For more information, see [Set-CMClientSettingComputerRestart](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComputerRestart).

**Non-breaking changes**

- Extended the validation range of the parameters **CountdownMins** and **RebootLogoffNotificationCountdownMins** to align with the console.
- Added new parameters **CountdownIntervalMins** and **ServerRebootLowRight** to align with the console.
- Fixed a property name issue for the parameter **NoRebootEnforcement**.

#### Set-CMNotification

For more information, see [Set-CMNotification](/en-us/powershell/module/configurationmanager/Set-CMNotification)

**Non-breaking changes**

New alias **InputObject** has been added for parameter **NotificationTasks** which now supports pipeline.

### Module changes

The following folder-related cmdlets now support automatic deployment rules:

- [Get-CMFolder](/en-us/powershell/module/configurationmanager/get-cmfolder)
- [New-CMFolder](/en-us/powershell/module/configurationmanager/new-cmfolder)
- [Remove-CMFolder](/en-us/powershell/module/configurationmanager/remove-cmfolder)
- [Set-CMFolder](/en-us/powershell/module/configurationmanager/set-cmfolder)
- [Move-CMObject](/en-us/powershell/module/configurationmanager/move-cmobject)
- [Add-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Add-CMObjectSecurityScope)
- [Remove-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Remove-CMObjectSecurityScope)