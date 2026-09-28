---
layout: Conceptual
title: Technical preview 2001.2 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2001-2
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2001.2.
ms.date: 2020-02-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: ed4a1a97-0acf-df94-751a-c656811ddd83
document_version_independent_id: 6d65b63c-35f3-e6c4-389f-c1578cbcbe1c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2001-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2001-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2001-2.md
platformId: 9bcbb5a6-8dc2-a1a3-3c50-8676e1598171
---

# Technical preview 2001.2 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2001.2. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Token based authentication for cloud management gateway

The cloud management gateway (CMG) supports many types of clients, but even with [Enhanced HTTP](../../plan-design/hierarchy/enhanced-http), these clients require a [client authentication certificate](../../clients/manage/cmg/configure-authentication#pki-certificate). This certificate requirement can be challenging to provision on internet-based clients that don't often connect to the internal network, aren't able to join Microsoft Entra ID, and don't have a method to install a PKI-issued certificate.

Starting in this release, Configuration Manager extends its device support with the following methods:

Note

These methods only support device-centric management scenarios.

Microsoft recommends joining devices to Microsoft Entra ID. Internet-based devices can use Microsoft Entra ID to authenticate with Configuration Manager. It also enables both device and user scenarios whether the device is on the internet or connected to the internal network.

### Register on the internal network for a unique token

This method requires the client to first register with the management point on the internal network. Client registration typically happens right after installation. Now the management point gives the client a unique token that shows it's using a self-signed certificate. When the client roams onto the internet, to communicate with the CMG it pairs its self-signed certificate with the management point-issued token. The client renews the token once a month, and it's valid for 90 days.

The site enables this behavior by default.

### Create a bulk registration token for internet-based devices

If you can't install and register clients on the internal network, you can now create a bulk registration token. Use this token when the client installs on an internet-based device, and registers through the CMG. The bulk registration token has a short-validity period, and isn't stored on the client or the site. It allows the client to generate a unique token, which paired with its self-signed certificate, lets it authenticate with the CMG.

#### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Sign in to the top-level site server in the hierarchy with local administrator privileges.
2. Open a command prompt as an administrator.
3. Run the tool from the `\bin\X64` folder of the Configuration Manager installation directory on the site server: `BulkRegistrationTokenTool.exe`. Create a new token with the `/new` parameter. For example, `BulkRegistrationTokenTool.exe /new`.

    The tool displays the following information:

    - A GUID that the site uses to track issued tokens
    - The token validity period.
    - The token.
4. Copy the token and save it in a secure location.
5. Install the Configuration Manager client on an internet-based device. Include the new client installation parameter: **/regtoken**. The following example command line includes the other required setup parameters and properties:

    `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC SMSMP=https://mp1.contoso.com /regtoken:eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ik9Tbzh2Tmd5VldRUjlDYVh5T2lacHFlMDlXNCJ9.eyJTQ0NNVG9rZW5DYXRlZ29yeSI6IlNDQ01QcmVBdXRoVG9rZW4iLCJBdXRob3JpdHkiOiJTQ0NNIiwiTGljZW5zZSI6IlNDQ00iLCJUeXBlIjoiQnVsa1JlZ2lzdHJhdGlvbiIsIlRlbmFudElkIjoiQ0RDQzVFOTEtMEFERi00QTI0LTgyRDAtMTk2NjY3RjFDMDgxIiwiVW5pcXVlSWQiOiJkYjU5MWUzMy0wNmZkLTRjNWItODJmMy1iZjY3M2U1YmQwYTIiLCJpc3MiOiJ1cm46c2NjbTpvYXV0aDI6Y2RjYzVlOTEtMGFkZi00YTI0LTgyZDAtMTk2NjY3ZjFjMDgxIiwiYXVkIjoidXJuOnNjY206c2VydmljZSIsImV4cCI6MTU4MDQxNTUwNSwibmJmIjoxNTgwMTU2MzA1fQ.ZUJkxCX6lxHUZhMH_WhYXFm_tbXenESpgnbIqI1h8hYIJw7xDk3wv625SCfNfsqxhAwRwJByfkXdVGgIpAcFshzArXUVPPvmiUGaxlbB83etUTQjrLIk-gvQQZiE5NSgJ63LCp5KtqFCZe8vlZxnOloErFIrebjFikxqAgwOO4i5ukJdl3KQ07YPRhwpuXmwxRf1vsiawXBvTMhy40SOeZ3mAyCRypQpQNa7NM3adCBwUtYKwHqiX3a1jQU0y57LvU_brBfLUL6JUpk3ri-LSpwPFarRXzZPJUu4-mQFIgrMmKCYbFk3AaEvvrJienfWSvFYLpIYA7lg-6EVYRcCAA`

    Tip

    For more information on this command line, see [Install and register the client using Microsoft Entra identity](../../clients/deploy/deploy-clients-cmg-azure#install-and-register-the-client-using-azure-ad-identity). This process is similar, just doesn't use the Microsoft Entra properties.

## Improvements to Orchestration Groups

Orchestration Groups are the evolution of the "Server Groups" feature. They were first introduced in the [technical preview for Configuration Manager, version 1909](../2019/technical-preview-1909#bkmk_OGs). We improved upon Orchestration Groups in [technical preview 2001](technical-preview-2001#bkmk_orch) by adding customizable timeouts, resource validation, and site code selection for member selection. Now, in this technical preview, we've added the following improvements to Orchestration Groups:

- You can change the settings of an existing Orchestration Group using in the **Properties**.
- **Start Orchestration**: You can now start orchestration for your groups. Select your Orchestration Group, then click **Start Orchestration** in the ribbon or from the right-click menu. [![Start Orchestration ](media/3098816-start-orchestration.png)](media/3098816-start-orchestration.png#lightbox)

## New cmdlets for phased deployments

Configuration Manager now supports cmdlets for phased deployments. You can configure your phased deployment scenarios using the following new cmdlets:

- New-CMSoftwareUpdatePhase
- New-CMTaskSequencePhase
- Get-CMPhase
- New-CMApplicationAutoPhasedDeployment
- New-CMSoftwareUpdateAutoPhasedDeployment
- New-CMSoftwareUpdateManualPhasedDeployment
- New-CMTaskSequenceAutoPhasedDeployment
- New-CMTaskSequenceManualPhasedDeployment
- Get-CMApplicationPhasedDeployment
- Get-CMSoftwareUpdatePhasedDeployment
- Get-CMTaskSequencePhasedDeployment
- Get-CMPhasedDeploymentStatus
- Move-CMPhasedDeploymentToNext
- Resume-CMPhasedDeployment
- Suspend-CMPhasedDeployment
- Remove-CMApplicationPhasedDeployment
- Remove-CMSoftwareUpdatePhasedDeployment
- Remove-CMTaskSequencePhasedDeployment

### New-CMSoftwareUpdatePhase

Use this cmdlet to create a deployment phase for software update.

```PowerShell
New-CMSoftwareUpdatePhase `
 -CollectionName "MyCollection" `
 -PhaseName "MySUPhase"`
 -UserNotificationOption DisplaySoftwareCenterOnly
```

### New-CMTaskSequencePhase

Use this cmdlet to create a deployment phase for a task sequence.

```PowerShell
New-CMTaskSequencePhase -CollectionName "MyCollection" -PhaseName "MyTSPhase" -UserNotification DisplayAll -AllowRemoteDP $true
```

### Get-CMPhase

Use this cmdlet to get the deployment phase for a specific instance or a phased deployment.

```PowerShell
Get-CMPhase -Id "66DEDF86-D0CB-457D-88BE-47E3FAC92A47"

$myPhasedDeployment | Get-CMPhase
```

### New-CMApplicationAutoPhasedDeployment

Use this cmdlet to create a phased deployment for an application by generating two phases with same settings.

```PowerShell
New-CMApplicationAutoPhasedDeployment -ApplicationName "myApp" -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"
 
$myApp | New-CMApplicationAutoPhasedDeployment -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"
```

### New-CMSoftwareUpdateAutoPhasedDeployment

Use this cmdlet to create a phased deployment for software updates by generating two phases with same settings.

```PowerShell
New-CMSoftwareUpdateAutoPhasedDeployment -SoftwareUpdateName "myUpdateName" -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"

$myUpdate | New-CMSoftwareUpdateAutoPhasedDeployment -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"
```

### New-CMSoftwareUpdateManualPhasedDeployment

Use this cmdlet to create a phased deployment for software updates. You'll need to add new customized deployment phases with the cmdlet New-CMSoftwareUpdatePhase first.

```PowerShell
$phase1 = New-CMSoftwareUpdatePhase -CollectionId "SMSDM001" -PhaseName "test01" -UserNotificationOption DisplaySoftwareCenterOnly
$phase2 = New-CMSoftwareUpdatePhase -CollectionId "SMSDM003" -PhaseName "test02" -UserNotificationOption DisplaySoftwareCenterOnly
New-CMSoftwareUpdateManualPhasedDeployment -SoftwareUpdateNames ("myUpdateA", "myUpdateB") -Name "myPhaseDeployment" -AddPhases ($phase1, $phase2)
 
$phase3 = New-CMSoftwareUpdatePhase -CollectionId "SMSDM001" -PhaseName "test03" -UserNotificationOption DisplaySoftwareCenterOnly
$phase4 = New-CMSoftwareUpdatePhase -CollectionId "SMSDM003" -PhaseName "test04" -UserNotificationOption DisplaySoftwareCenterOnly
New-CMSoftwareUpdateManualPhasedDeployment -SoftwareUpdateGroupName "myGroup" -Name "myPhaseDeploymentForGroup" -AddPhases ($phase3, $phase4)
```

### New-CMTaskSequenceAutoPhasedDeployment

Use this cmdlet to create a phased deployment for a task sequence by generating two phases with same settings.

```PowerShell
New-CMTaskSequenceAutoPhasedDeployment -TaskSequenceName "myTaskSequenceName" -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"
 
$myTS | New-CMTaskSequenceAutoPhasedDeployment -Name "myPDName" -FirstCollectionID "SMSDM001" -SecondCollectionID "SMSDM003" -CriteriaOption Compliance -CriteriaValue 1 -BeginCondition AfterPeriod -DaysAfterPreviousPhaseSuccess 2 -ThrottlingDays 3 -InstallationChoice AfterPeriod -DeadlineUnit Hours -DeadlineValue 4 -Description "MyDescription"
```

### New-CMTaskSequenceManualPhasedDeployment

Use this cmdlet to create a phased deployment for a task sequence. You'll need to add new customized deployment phases with the cmdlet New-CMTaskSequencePhase first.

```PowerShell
$phase1 = New-CMTaskSequencePhase -CollectionId "SMSDM001" -PhaseName "test01" -UserNotification DisplayAll
$phase2 = New-CMTaskSequencePhase -CollectionId "SMSDM003" -PhaseName "test02" -UserNotification HideAll
New-CMTaskSequenceManualPhasedDeployment -TaskSequenceName "myTaskSequence" -Name "phasedDeployment" -AddPhases ($phase1, $phase2)
 
$phase3 = New-CMTaskSequencePhase -CollectionId "SMSDM001" -PhaseName "test03" -UserNotification DisplayAll
$phase4 = New-CMTaskSequencePhase -CollectionId "SMSDM003" -PhaseName "test04" -UserNotification HideAll
$myTaskSequence | New-CMTaskSequenceManualPhasedDeployment -Name "phasedDeployment" -AddPhases ($phase3, $phase4)
```

### Get-CMApplicationPhasedDeployment

Use this cmdlet to get the phased deployment for an application.

```PowerShell
Get-CMApplicationPhasedDeployment -Name "myPhasedDeploymentName"
 
Get-CMApplicationPhasedDeployment -ApplicationName "myApplicationName"
```

### Get-CMSoftwareUpdatePhasedDeployment

Use this cmdlet to get the phased deployment for software updates.

```PowerShell
Get-CMSoftwareUpdatePhasedDeployment -Name "myPhasedDeploymentName"
 
Get-CMSoftwareUpdatePhasedDeployment -SoftwareUpdateName "myUpdateName"
```

### Get-CMTaskSequencePhasedDeployment

Use this cmdlet to get the phased deployment for a task sequence.

```PowerShell
Get-CMTaskSequencePhasedDeployment -Name "myPhasedDeploymentName"
 
Get-CMTaskSequencePhasedDeployment -TaskSequenceName "myTaskSequenceName"
```

### Get-CMPhasedDeploymentStatus

Use this cmdlet to get the status of a specific phased deployment.

```PowerShell
Get-CMPhasedDeploymentStatus -Name "myPhasedDeploymentName"
 
$myPhasedDeployment | Get-CMPhasedDeploymentStatus -Catalog $catalog
```

### Move-CMPhasedDeploymentToNext

Use this cmdlet to move the specified phased deployment to the next phase.

```PowerShell
Move-CMPhasedDeploymentToNext -Name "myPhasedDeploymentName"  
 
$myPhasedDeployment | Move-CMPhasedDeploymentToNext -Force
```

### Resume-CMPhasedDeployment

Use this cmdlet to resume the phased deployment from the suspend status.

```PowerShell
Resume-CMPhasedDeployment -Name "myPhasedDeploymentName"  
 
$myPhasedDeployment | Resume-CMPhasedDeployment -Force
```

### Suspend-CMPhasedDeployment

Use this cmdlet to suspend the specified phased deployment.

```PowerShell
Suspend-CMPhasedDeployment -Name "myPhasedDeploymentName"
  
$myPhasedDeployment | Suspend-CMPhasedDeployment -Force
```

### Remove-CMApplicationPhasedDeployment

Use this cmdlet to remove an phased deployment for an application.

```PowerShell
Remove-CMApplicationPhasedDeployment -ApplicationName "myApplicationName"
 
Remove-CMApplicationPhasedDeployment -Name "myPhasedDeploymentName"
 
$myPhasedDeployment | Remove-CMApplicationPhasedDeployment -Force
```

### Remove-CMSoftwareUpdatePhasedDeployment

Use this cmdlet to remove an phased deployment for software updates.

```PowerShell
Remove-CMSoftwareUpdatePhasedDeployment -SoftwareUpdateName "mySoftwareUpdateName"
 
Remove-CMSoftwareUpdatePhasedDeployment -SoftwareUpdateGroupName "mySoftwareUpdateGroupName"
 
Remove-CMSoftwareUpdatePhasedDeployment -Name "myPhasedDeploymentName"
 
$myPhasedDeployment | Remove-CMSoftwareUpdatePhasedDeployment -Force
```

### Remove-CMTaskSequencePhasedDeployment

Use this cmdlet to remove an phased deployment for a task sequence.

```PowerShell
Remove-CMTaskSequencePhasedDeployment -TaskSequenceName "myTaskSequenceName"
 
Remove-CMTaskSequencePhasedDeployment -Name "myPhasedDeploymentName"
 
$myPhasedDeployment | Remove-CMTaskSequencePhasedDeployment -Force
```

## Exclude certain subnets for peer content download

Boundary groups include the following option for peer downloads: **During peer downloads, only use peers within the same subnet**. If you enable this option, the management point only includes in the content location list peer sources that are in the same subnet and boundary group as the client. For more information on this option, see [Boundary group options for peer downloads](../../servers/deploy/configure/boundary-group-options).

Depending on the configuration of your network, you can now exclude certain subnets for matching. For example, you want to include a boundary but exclude a specific VPN subnet. By default, Configuration Manager excludes the default Teredo subnet (`2001:0000:%`).

Import your subnet exclusion list as a comma-separated subnet string. Use the percent sign (`%`) as a wildcard character. On the top-level site server, set or read the **SubnetExclusionList** embedded property for the **SMS\_HIERARCHY\_MANAGER** component in the **SMS\_SCI\_Component** class. For more information, see [SMS_SCI_Component server WMI class](../../../develop/reference/core/servers/configure/sms_sci_component-server-wmi-class). The following script is a sample way of changing this value.

```PowerShell
#
# This sample sets the SubnetExclusionList property's for SMS_HIERARCHY_MANAGER component for the top-level site
#

# Replace "2001:0000:%,172.16.16.0" with the subnets that you would like to exclude. It's a comma separated string.
# This script must be run on the top-level site server
$PropertyValue = "2001:0000:%,172.16.16.0"

# Don't change any of the lines below
$PropertyName = "SubnetExclusionList"

# Get provider instance
$providerMachine = Get-WmiObject -namespace "root\sms" -class "SMS_ProviderLocation"

if($providerMachine -is [system.array])
{
    $providerMachine=$providerMachine[0]
}

$SiteCode = $providerMachine.SiteCode

$component = gwmi -ComputerName $providerMachine.Machine -namespace root\sms\site_$SiteCode -query 'select comp.* from sms_sci_component comp join SMS_SCI_SiteDefinition sdef on sdef.SiteCode=comp.SiteCode where sdef.ParentSiteCode="" and comp.componentname="SMS_HIERARCHY_MANAGER"'
$properties = $component.props

Write-host "Updating property for site " $SiteCode

foreach ($property in $properties)
{
  if ($property.propertyname -like $PropertyName) 
  {
    Write-host "Current value for SubnetExclusionList is  " $property.value1
    $property.value1 = $PropertyValue
    Write-host "Updating value for SubnetExclusionList to " $property.value1
    break
  }
}

$component.props = $properties
$component.put()
```

Note

By default, Configuration Manager includes the Teredo subnet in this list. When you change the list, always read the existing value first. Append additional subnets to the list, and then set the new value.

## Send a smile improvements

When you **Send a smile** or **Send a frown**, a status message is created when the feedback is submitted. This improvement provides a record of:

- When the feedback was submitted
- Who submitted the feedback
- The feedback ID
- If the feedback submission was successful or not

A status message with an ID of 53900 is a successful submission and 53901 is a failed submission.

[![Status message for successfully submitting feedback](media/5891852-send-smile-status-message.png)](media/5891852-send-smile-status-message.png#lightbox)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Send a smile or a frown

To send feedback on something, follow the instructions below:

1. In the upper right corner of the console, click on the smiley face.
2. In the drop-down menu, select **Send a smile** or **Send a frown**.
3. Use the text box to explain what you liked or what you didn't like.
4. Choose if you would like to share your e-mail address and a screenshot.
5. Click **Submit Feedback**.
    - Status messages aren't created if you [Send feedback that you saved for later submission](../../understand/product-feedback#send-feedback-that-you-saved-for-later-submission).
6. Check your status messages for:
    - Message ID of 53900 for a successful submission.
    - Message ID of 53901 for a failed submission.

## Improvements to task sequence as a deployment type

Technical preview version 1905 included the initial release of the task sequence as an app model deployment type. This feature allows you to install complex applications using task sequences via the application model. It provides the following benefits:

- Display the app task sequence with an icon in Software Center. An icon makes it easier for users to find and identify the app task sequence.
- Define additional metadata for the app task sequence, including localized information

This release includes the client-side functionality, so you can now see the deployment in Software Center. After you update the site, make sure to also update the client to the latest version.

For more information including prerequisites and set up instructions, see [task sequence as an app model deployment type](../2019/technical-preview-1905#bkmk_tsdt).

Note

Aside from the existing prerequisites for this feature to only use non-OSD task sequence steps, it also can't include an app with a task sequence deployment type. If you use the **Install Application** step, don't add an app to that step that installs a task sequence.

### Known issues

- You can't yet deploy an app task sequence to a user collection
- Don't use the **Install Application** step in this task sequence. Use the [Install Package](../../../osd/understand/task-sequence-steps#BKMK_InstallPackage) step to install apps.

## Improvements to Microsoft Edge Management dashboard

We've added a graph for **Default browser** to the Microsoft Edge Management dashboard. From the **Software Library** workspace, click **Microsoft Edge Management** to see the updated dashboard. Change the collection for the graph data by clicking **Browse** and choosing another collection.

[![Microsoft Edge Management dashboard](media/3871913-updated-edge-dashboard.png)](media/3871913-updated-edge-dashboard.png#lightbox)

## Improvements to cloud-connected services

This release includes the following improvements for monitoring the connection from Configuration Manager to cloud services. For example, [Desktop Analytics](../../../../device-updates/windows/monitor-compatibility). These features help you troubleshoot connectivity issues between on-premises systems and the connected cloud service.

### Critical status message shows server connection errors to required endpoints

If the Configuration Manager site server fails to connect to required endpoints for a cloud service, it raises a critical status message ID 11488. When the site server can't connect to the service, the SMS\_SERVICE\_CONNECTOR component status changes to critical. View detailed status in the **Component Status** node of the Configuration Manager console. For more information, see the following articles:

- [Monitor the status system of Configuration Manager](../../servers/manage/use-status-system#monitor-the-status-system)
- [Internet access requirements](../../plan-design/network/internet-endpoints)
- [Desktop Analytics endpoints](../../../../device-updates/windows/monitor-compatibility)

### Connection Health dashboard shows client connection issues

Use the Desktop Analytics [Connection Health](../../../../device-updates/windows/monitor-compatibility) dashboard in Configuration Manager to monitor the clients' connectivity health. It now helps you to more easily identify any client connectivity issues in two areas:

- **Endpoint connectivity checks**: If clients can't reach an internet [required endpoint](../../../../device-updates/windows/monitor-compatibility), you see a configuration alert in the dashboard. From the Connection Health dashboard, drill down into clients that are unable to unenroll. The **Endpoint connectivity checks** property of the device shows a numbered list of endpoints to which it can't connect.
- **Connectivity status**: If your clients use a proxy server to access the Desktop Analytics cloud service, Configuration Manager now displays proxy authentication issues from clients. From the Connection Health dashboard, drill down into clients that are unable to unenroll. The **Connectivity status** property of the device shows the following details:

    - Status code
    - Return code

    For more information on configuring proxy servers for use with Desktop Analytics, see [Proxy server authentication](../../../../device-updates/windows/monitor-compatibility).

For more general information on troubleshooting Desktop Analytics, see the following articles:

- [Troubleshoot Desktop Analytics](../../../../device-updates/windows/monitor-compatibility)

## Additional improvement to task sequence progress

Based on your feedback from the [improvements in technical preview version 2001](technical-preview-2001#bkmk_tsprogress), this release includes the following change:

- By default, the task sequence progress window uses the existing text. If you make no changes, it continues to work the same as in version 1912 and earlier.
- To show the new progress information, specify the new task sequence variable, **TSProgressInfoLevel**. You can set the type of information it displays by using the following values for this variable:

    - `1`: Include the current step and total steps to the progress text. For example, **2 of 10**.
    - `2`: Include the current step, total steps, and percentage completed. This behavior is the same as version 2001. For example, **2 of 10 (20% complete)**.
    - `3`: Include the percentage completed. For example, **(20% complete)**.

## General known issues

### Can't create or edit some collections

In this version of the technical preview branch, you can't create a new collection. You also can't edit the properties of an existing user collection.

To work around this issue, use Configuration Manager PowerShell cmdlets to create new collections and edit existing user collections. Some of the available cmdlets for managing collections include:

- [New-CMCollection](/en-us/powershell/module/configurationmanager/new-cmcollection)
- [Get-CMCollection](/en-us/powershell/module/configurationmanager/get-cmcollection)
- [Set-CMCollection](/en-us/powershell/module/configurationmanager/set-cmcollection#related-links)
- [Add-CMCollectionMembershipRule](/en-us/powershell/module/configurationmanager/add-cmcollectionmembershiprule)