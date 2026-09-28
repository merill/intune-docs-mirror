---
layout: Conceptual
title: Technical preview 2205 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2205
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2205.
ms.date: 2022-05-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 577a9c6b-f3f7-69cf-a954-7b029a66746e
document_version_independent_id: 577a9c6b-f3f7-69cf-a954-7b029a66746e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2205.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2205
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2205.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 701f4e22-1a5c-050b-377f-f67dce4aadb3
---

# Technical preview 2205 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2205. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Offset for reoccuring monthly maintenance window schedules

Based upon your feedback, you can now offset monthly maintenance window schedules to better align deployments with the release of monthly security updates. For example, using an offset of two days after the second Tuesday of the month, sets the maintenance window for Thursday.

[![Screenshot of menu displaying options for the new custom schedule for setting offset days.](media/3601127-window-schedule.png)](media/3601127-window-schedule.png#lightbox)

### Try it out!

Try to complete the tasks. Then send **Feedback** from the **Home** tab of the ribbon letting us know how it worked.

**Create a custom schedule that sets maintenance window offset from a base day**

1. In the **Device Collection** workspace, create **New Collection**, and select **Properties**.
2. Select on **Maintenance Window** and choose **New Custom Schedule**.
3. For the custom schedule, select **Monthly** and put in a base day such as the second Tuesday.
4. Verify the **Offset (days)** and the number of days for the offset then **OK** when finished.
5. Complete the deployment as usual.

Note

Before using this feature, upgrade the hierarchy to version 2205.

## Improvements to cloud management gateway (CMG) workflow

You can now approve the application workflow through email. For the application approvals through email, manually add the CMG URL in the Microsoft Entra app as single page application redirect URI. For more information on how to change the URI, see [Create an app registration in Microsoft Entra ID for your App Service app](/en-us/azure/app-service/configure-authentication-provider-aad).

## Script execution timeout for compliance settings

You can now define a **Script Execution Timeout (seconds)** when configuring [client settings](../../clients/deploy/about-client-settings#compliance-settings) for compliance settings. The timeout value can be set from a minimum of 60 seconds to a maximum of 600 seconds. This new setting allows you more flexibility for configuration items when you need to run scripts that may exceed the default of 60 seconds.

## Microsoft Defender for Endpoint onboarding for Windows Server 2012 R2 and Windows Server 2016

Configuration Manager will now utilize the [Windows Server 2012 R2 and Windows Server 2016 unified](/en-us/microsoft-365/security/defender-endpoint/configure-server-endpoints?#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) solution for anti-virus and endpoint detection and response. From this technical preview, devices that are targeted with Microsoft Defender for Endpoint onboarding policy use the unified agent versus the previous Microsoft Monitoring Agent based solution (where applicable).

Note

This functionality will only apply to clients that are onboarding. Upgrade scenarios will be supported in a future release. If you'd like to test this new functionality, you can offboard and onboard an existing device.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Approve-CMOrchestrationGroupScript

Use this cmdlet to approve an orchestration group script. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name "Orchestratrion group 1"
$preScript = $referenceOG | Get-CMOrchestrationGroupScript -ScriptType Pre
$preScript | Approve-CMOrchestrationGroupScript -Comment "Approve"

Approve-CMOrchestrationGroupScript -ScriptGuid $PreScript.ScriptGuid
```

#### Deny-CMOrchestrationGroupScript

Use this cmdlet to deny an orchestration group script. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name "Orchestratrion group 1"
$preScript = $referenceOG | Get-CMOrchestrationGroupScript -ScriptType Pre
$preScript | Deny-CMOrchestrationGroupScript -Comment "Deny"

Deny-CMOrchestrationGroupScript -ScriptGuid $PreScript.ScriptGuid -Comment "Deny"
```

#### Get-CMOrchestrationGroupScript

Use this cmdlet to get a script from the specified orchestration group. For more information, see [About orchestration groups in Configuration Manager](../../../sum/deploy-use/orchestration-groups).

```powershell
$referenceOG = Get-CMOrchestrationGroup -Name "Orchestratrion group 1"
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

#### Add-CMManagementPoint

For more information, see [Add-CMManagementPoint](/en-us/powershell/module/configurationmanager/Add-CMManagementPoint).

**Non-breaking changes**

When you use this cmdlet to enable communication with the cloud management gateway, it now by default configures the management point to support both internet and intranet clients.

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

#### Set-CMClientSettingComplianceSetting

For more information, see [Set-CMClientSettingComplianceSetting](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComplianceSetting).

**Non-breaking changes**

Added a new parameter **ScriptExecutionTimeoutSecs** to extend the script execution timeout value.

#### Set-CMClientSettingComputerRestart

For more information, see [Set-CMClientSettingComputerRestart](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComputerRestart).

**Non-breaking changes**

- Extended the validation range of the parameters **CountdownMins** and **RebootLogoffNotificationCountdownMins** to align with the console.
- Added new parameters **CountdownIntervalMins** and **ServerRebootLowRight** to align with the console.
- Fixed a property name issue for the parameter **NoRebootEnforcement**.

### Module changes

The following folder-related cmdlets now support automatic deployment rules:

- [Get-CMFolder](/en-us/powershell/module/configurationmanager/get-cmfolder)
- [New-CMFolder](/en-us/powershell/module/configurationmanager/new-cmfolder)
- [Remove-CMFolder](/en-us/powershell/module/configurationmanager/remove-cmfolder)
- [Set-CMFolder](/en-us/powershell/module/configurationmanager/set-cmfolder)
- [Move-CMObject](/en-us/powershell/module/configurationmanager/move-cmobject)
- [Add-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Add-CMObjectSecurityScope)
- [Remove-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Remove-CMObjectSecurityScope)