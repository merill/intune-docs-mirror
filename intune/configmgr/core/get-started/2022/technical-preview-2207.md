---
layout: Conceptual
title: Technical preview 2207 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2207
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2207.
ms.date: 2022-07-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: a670bc96-705d-cc8d-6245-9f463525b892
document_version_independent_id: a670bc96-705d-cc8d-6245-9f463525b892
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2207.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2207
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2207.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cd7aedbb-a9e1-7a85-39f6-745c79e0ddd9
---

# Technical preview 2207 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2207. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Distribution point content migration

Distribution point content migration support is now available for migrating content from one distribution point to another distribution point using PowerShell cmdlets. You can also monitor the distribution point migration status using these PowerShell cmdlets.

There are multiple scenarios where the content of one distribution point needs to be migrated to another distribution point.

1. Cloud distribution points (CDP) hosted on Azure classic services are getting deprecated by mid of 2024. You need to migrate CDP content to another distribution point.
2. Migration of cloud migration gateway v1 (CMGv1) hosted with \*.cloudapp.net domain is also getting deprecated, hence you may need to migrate CMGv1 content to another distribution point.
3. You may need to migrate local distribution point content to other local distribution point or CMG.

#### Prerequisites

1. The user's security role permission should have "Copy to Distribution Point" enabled under Distribution Point.
2. If you want to deprecate the source distribution point, make sure that the source and destination distribution points have the same boundary group.
3. The destination distribution point should be installed already and able to receive the content.

Note

You can't currently configure this behavior from the Configuration Manager console. For more information on configuring this behavior with PowerShell, see the cmdlet details in the following section.

### Start-CMDistributionPointMigration

Use this cmdlet to initiate distribution point content migration. You can pass the desired parameters such as SourceDistributionPointName and DestinationDistributionPointName per your distribution point migration scenario. You can also pass the LockSourceDistributionPoint parameter to lock the source distribution point. This parameter is used to deprecate the source distribution point scenarios (for example: CDP Migration). If the source distribution point is locked during distribution point migration, you won't be able to distribute the new content to the source distribution point, but the endpoints will be able to download the content that is already available in the source distribution point. For deprecation scenarios, you can delete the source distribution point after the distribution content migration is completed.

#### Syntax

```powershell
Start-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> 
```

#### Examples

```powershell
Start-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> -LockSourceDistributionPoint  

Start-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> 
```

#### Parameters

- **SourceDistributionPointName**: Use this to specify the source distribution point from where content will be migrated.
- **DestinationDistributionPointName**: Use this to specify the destination distribution point where you want the content to be copied.
- **LockSourceDistributionPoint**: Use when you need to initiate distribution point migration with source distribution point locked.

### Get-CMDistributionPointMigrationStatus

Use this cmdlet to monitor the distribution point migration status.

#### Syntax

```powershell
Get-CMDistributionPointMigrationStatus -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> 
```

### Get-CMDistributionPointMigrationContentStatus

Use this cmdlet to monitor the distribution point content migration status.

#### Syntax

```powershell
Get-CMDistributionPointMigrationContentStatus -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point>
```

### Stop-CMDistributionPointMigration

Use this cmdlet to stop the distribution point migration. In case you have mistakenly locked the source distribution point, you can use this cmdlet to unlock the source distribution point. Unlocking the source distribution point will stop the distribution point migration. To restart the migration, use the Start-CMDistributionPointMigration cmdlet.

#### Syntax

```powershell
Stop-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> 
```

#### Examples

```powershell
Stop-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> -LockSourceDistributionPoint  

Stop-CMDistributionPointMigration -SourceDistributionPointName <FQDN for source distribution point> -DestinationDistributionPointName <FQDN for destination distribution point> 
```

Note

You won't be able to perform multiple migrations at a shared time. Migration for one set of source and destination distribution points needs to be completed before starting another.

## Improvements to Configuration Manager policies for Microsoft Defender Application Guard

1. Windows Defender Application Guard has been renamed to [Microsoft Defender Application Guard](../../../protect/deploy-use/create-deploy-application-guard-policy) in the Configuration Manager console.
2. The **General** settings page allows you to enable for isolated Windows environments and enable for Microsoft Edge and isolated Windows environments.
3. The **Application Behavior** settings page allows you to enable or disable cameras and microphones, along with certificate matching the thumbprints to the isolated container.
4. The following items were removed:
    - The [Enterprise sites can load non-enterprise content, such as third-party plug-ins](../../../protect/deploy-use/create-deploy-application-guard-policy#bkmk_ABS) setting under the **Host interaction** page
    - The file trust criteria policy in the **File Management** page

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

#### Start-CMDPMigration

Use this cmdlet to start migration from source distribution point to destination distribution point. For more information, see [About migration in Configuration Manager](../../migration/planning-a-migration-job-strategy).

```powershell
Start-CMDPMigration -SourceDistributionPointName sourceServer.dp -DestinationDistributionPointName destinationServer.dp -LockSourceDP 1
```

#### Stop-CMDPMigration

Use this cmdlet to stop migration from source distribution point to destination distribution point. For more information, see [About migration in Configuration Manager](../../migration/planning-a-migration-job-strategy).

```powershell
Stop-CMDPMigration -SourceDistributionPointName sourceServer.dp -DestinationDistributionPointName destinationServer.dp -LockSourceDP 1
```

#### Get-CMDPMigrationContentStatus

Use this cmdlet to get the content status of the migration from source distribution point to destination distribution point. For more information, see [About migration in Configuration Manager](../../migration/planning-a-migration-job-strategy).

```powershell
Get-CMDPMigrationContentStatus  -SourceDistributionPointName sourceServer.dp -DestinationDistributionPointName destinationServer.dp
```

#### Get-CMDPMigrationStatus

Use this cmdlet to get the status of the migration from source distribution point to destination distribution point. For more information, see [About migration in Configuration Manager](../../migration/planning-a-migration-job-strategy).

```powershell
Get-CMDPMigrationStatus -SourceDistributionPointName sourceServer.dp -DestinationDistributionPointName destinationServer.dp
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

#### Set-CMDefaultBoundaryGroup

Use this cmdlet to modify the properties of a default site boundary group. You can set the options to include and prefer the cloud-based sources for the clients in default site boundary group. For more information on boundary groups, see [About boundary groups in Configuration Manager](../../servers/deploy/configure/boundary-groups).

```powershell
Set-CMDefaultBoundaryGroup -IncludeCloudBasedSources $true -PreferCloudBasedSources $true
```

### Modified cmdlets

#### Add-CMComplianceSettingWqlQuery

For more information, see [Add-CMComplianceSettingWqlQuery](/en-us/powershell/module/configurationmanager/Add-CMComplianceSettingWqlQuery).

**Non-breaking changes**

When using this cmdlet, you can now specify $null value to the parameter **WhereClause**.

#### Add-CMManagementPoint

For more information, see [Add-CMManagementPoint](/en-us/powershell/module/configurationmanager/Add-CMManagementPoint).

**Non-breaking changes**

When you enable cloud gateway, **ClientConnectionTypes.InternetAndIntranet** is now the default value.

#### Add-CMReportingServicePoint

For more information, see [Add-CMReportingServicePoint](/en-us/powershell/module/configurationmanager/Add-CMReportingServicePoint).

**Non-breaking changes**

This cmdlet will be blocked to run on PowerShell7, as SOAP is not supported in PowerShell7. This cmdlet requires the .NET Framework instead of .NET Core that's used with PowerShell version 7.

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

#### New-CMCoManagementPolicy

For more information, see [New-CMCoManagementPolicy](/en-us/powershell/module/configurationmanager/New-CMCoManagementPolicy).

**Non-breaking changes**

You can now view the policy created as well as prevent creation of second policy from this cmdlet. You can now also create child policies for each workload, like UI, while creating Co-Management policy from this cmdlet.

#### New-CMComplianceRuleRegistryKeyPermission

For more information, see [New-CMComplianceRuleRegistryKeyPermission](/en-us/powershell/module/configurationmanager/New-CMComplianceRuleRegistryKeyPermission).

**Non-breaking changes**

Fixed an issue in **OperandDataType** property when creating a rule.

#### New-CMFolder

For more information, see [New-CMFolder](/en-us/powershell/module/configurationmanager/New-CMFolder).

**Non-breaking changes**

An issue in folder path validation has been fixed when using this cmdlet to create a new folder in the console.

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

The following cmdlets now have added validation condition for starting or stopping service while CMG is a Virtual Machine Scale Set:

- [Start-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Start-CMCloudManagementGateway)
- [Stop-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Stop-CMCloudManagementGateway)

The following cmdlets have been removed due to the deprecated RA feature:

- [Add-CMCertificateRegistrationPoint](/en-us/powershell/module/configurationmanager/Add-CMCertificateRegistrationPoint)
- [Import-CMClientCertificatePfx](/en-us/powershell/module/configurationmanager/Import-CMClientCertificatePfx)
- [Import-CMWirelessProfileConfigurationItem](/en-us/powershell/module/configurationmanager/Import-CMWirelessProfileConfigurationItem)
- [New-CMCertificateProfilePfx](/en-us/powershell/module/configurationmanager/New-CMCertificateProfilePfx)
- [New-CMCertificateProfileScep](/en-us/powershell/module/configurationmanager/New-CMCertificateProfileScep)
- [New-CMCertificateProfileTrustedRootCA](/en-us/powershell/module/configurationmanager/New-CMCertificateProfileTrustedRootCA)
- [New-CMClientCertificateProfileConfigurationItem](/en-us/powershell/module/configurationmanager/New-CMClientCertificateProfileConfigurationItem)
- [New-CMEmailProfile](/en-us/powershell/module/configurationmanager/New-CMEmailProfile)
- [New-CMRootCertificateProfileConfigurationItem](/en-us/powershell/module/configurationmanager/New-CMRootCertificateProfileConfigurationItem)
- [New-CMVpnProfileConfigurationItem](/en-us/powershell/module/configurationmanager/New-CMVpnProfileConfigurationItem)
- [New-CMWirelessProfile](/en-us/powershell/module/configurationmanager/New-CMWirelessProfile)
- [New-CMWirelessProfileConfigurationItem](/en-us/powershell/module/configurationmanager/New-CMWirelessProfileConfigurationItem)
- [Set-CMCertificateProfilePfx](/en-us/powershell/module/configurationmanager/Set-CMCertificateProfilePfx)
- [Set-CMCertificateProfileScep](/en-us/powershell/module/configurationmanager/Set-CMCertificateProfileScep)
- [Set-CMCertificateProfileTrustedRootCA](/en-us/powershell/module/configurationmanager/Set-CMCertificateProfileTrustedRootCA)
- [Set-CMCertificateRegistrationPoint](/en-us/powershell/module/configurationmanager/Set-CMCertificateRegistrationPoint)
- [Set-CMClientCertificateProfileConfigurationItem](/en-us/powershell/module/configurationmanager/Set-CMClientCertificateProfileConfigurationItem)
- [Set-CMEmailProfile](/en-us/powershell/module/configurationmanager/Set-CMEmailProfile)
- [Set-CMVpnProfileConfigurationItem](/en-us/powershell/module/configurationmanager/Set-CMVpnProfileConfigurationItem)
- [Set-CMWirelessProfile](/en-us/powershell/module/configurationmanager/Set-CMWirelessProfile)
- [Set-CMWirelessProfileConfigurationItem](/en-us/powershell/module/configurationmanager/Set-CMWirelessProfileConfigurationItem)