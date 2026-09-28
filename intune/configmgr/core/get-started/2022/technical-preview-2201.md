---
layout: Conceptual
title: Technical preview 2201 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2201
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2201.
ms.date: 2022-01-27T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 3fba7d6f-7aa2-4e8f-6e34-ed39dbbd6de3
document_version_independent_id: 3fba7d6f-7aa2-4e8f-6e34-ed39dbbd6de3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2201.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2201
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2201.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 20342fd4-54b3-fe15-5173-26070a8ad5c6
---

# Technical preview 2201 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2201. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Visualize content distribution status

You can now monitor content distribution path and status in a graphical format. The graph shows distribution point type, distribution state, and associated status messages. This visualization allows you to more easily understand the status of your content package distribution. It helps you answer questions like:

- Has the site successfully distributed the content?
- Is the content distribution in progress?
- Which distribution points have already processed the content?

![Visualization of content distribution status of the Configuration Manager client package in an example hierarchy.](media/9495651-view-content-distribution.png)

This example shows a graph for the content distribution status of the Configuration Manager client package in an example hierarchy. It lets you easily see the following information:

- The solid blue line from the site server to each distribution point indicates that the rate limit is **Unlimited**. For more information, see [Rate limits](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-rate).
- The green check mark on `DP01` and `DP02` indicates that the content was successfully distributed to these site systems.
- The red `X` on `DP03` and both cloud distribution points indicates that there's an error in distributing the content to these site systems.

Tip

Navigating this graph is similar to the [collection relationships graphical view](../../clients/manage/collections/view-relationships). That article includes tips to navigate the viewer, many of which also apply to this graph for content distribution.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand **Distribution Status** and select the **Content Status** node.
2. If this node doesn't show anything, first [distribute content](../../servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).
3. Select a distributed content item. For example, the **Configuration Manager client package**.
4. In the ribbon, select **View Content Distribution**. This action displays the distribution graph for the selected content.

    - Hover over the status icon to quickly view more information. Select the path or the status icon to view status messages for the content.
    - Hover over the title of the site system to quickly view more information. Select it to drill through to the **Distribution Points** node.

## Custom icon support for task sequences and packages

Previously, task sequences and legacy packages would always display a default icon in Software Center. Based on your feedback, you can now add custom icons for task sequences and legacy packages. These icons appear in Software Center when you deploy these objects. Instead of a default icon, a custom icon can improve the user experience to better identify the software.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. If needed, [create a task sequence](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks) or [create a package and program](../../../apps/deploy-use/packages-and-programs#create-a-package-and-program).
2. Open the properties of a task sequence or package.
3. For a task sequence, switch to the **More Options** tab. For a package, the icon option is on the **General** tab.

    Note

    The existing task sequence property page for **Performance** is now renamed to **More Options**.
4. In the section for the icon, select **Browse**. Select an icon from the default shell library, or browse to another file in a local or network path.

    - It supports the following file types:
        - Programs (`.exe`)
        - Libraries (`.dll`)
        - Icons (`.ico`)
        - Images (`.png`, `.jpeg`, `.jpg`)
    - The file doesn't need to be on clients that you target with the deployment. Configuration Manager includes the image with the deployment policy.
    - The maximum file size for an image is 256 KB.
    - Icons can have pixel dimensions of up to 512 x 512.

After you save the properties, deploy the task sequence or package, if it's not already deployed. For more information, see one of the following articles:

- [Deploy a task sequence](../../../osd/deploy-use/deploy-a-task-sequence)
- [Deploy packages and programs](../../../apps/deploy-use/packages-and-programs#deploy-packages-and-programs)

When clients receive the deployment policy, they'll display the icon in Software Center.

Note

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

### Known issues with icons for legacy packages

- To change the icon on an existing package that's already deployed, change another setting of the package or create a new deployment.
- Custom icons only appear for legacy packages that you deploy to device collections. They don't yet support user-based deployments.

## Prefer cloud-based software update points on switching

Clients now prefer to scan against a cloud management gateway (CMG) software update point (SUP) over an on-premises SUP when the boundary group uses the **Prefer cloud based source over on-premises source** option. To reduce the performance impact of this change, clients [don't automatically switch their SUP](../../../sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching) to a cloud-based SUP. The client will stay assigned to their current SUP unless their current SUP fails or the client is manually switched to a new SUP.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Ensure your [cloud management gateway](../../clients/manage/cmg/set-up-checklist?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) is configured and functional
2. Verify that your [software update points](../../../sum/get-started/install-a-software-update-point) are functional and synchronized.
3. Enable the [**Allow Configuration Manager cloud management gateway traffic**](../../clients/manage/cmg/setup-cloud-management-gateway#bkmk_role)option for any SUP you want to use with CMG.
    1. Go to **Administration** &gt; **Site Configuration** &gt; **Servers and Site System Roles**. Select **Properties** on the software update point site system role from the site server you want to use.
    2. On the **General** tab, enable the **Allow Configuration Manager cloud management gateway traffic** option.
4. [Configure the boundary group](../../servers/deploy/configure/boundary-group-procedures#configure-a-boundary-group) for this behavior by enabling the **Prefer cloud based sources over on-premises sources** option and adding the CGM SUP server to the **Site system servers**list.
    1. Go to **Administration** &gt; **Hierarchy Configuration** &gt; **Boundary Groups**. Edit the boundary groups where you want clients to prefer a CMG SUP for updates scanning.
    2. Select **Properties** for the boundary group.
    3. In the **References** tab, select **Add...** and add the CMG SUP to the **Site system servers** list.
    4. In the **Options** tab, select the **Prefer cloud based sources over on-premises sources** option.
    5. Select **OK** to save the settings and to close the boundary group properties window.
5. To manually switch clients to a new SUP, use the **Switch to next Software Update Point**[client notification](../../clients/manage/client-notification#switch-to-the-next-software-update-point)action for a device or for a collection.
    - Clients in the boundary group [don't automatically switch to a new SUP](../../../sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching) unless scanning against their current SUP fails four times over the course of two hours.
6. To verify that clients prefer the CMG SUP, start a software update scan cycle on some of the clients that you switched.
    - To limit potential performance issues caused by a large number of clients scanning against a new SUP simultaneously, we recommend that if you're immediately calling a scan cycle on a large number of clients that you start with no more than 100 clients every 10-15 minutes. Increase or decrease the number of clients and the frequency once you gauge the performance impact in your environment.
7. The client's **LocationServices.log** will show the CMG SUP listed as the first `LocationRecord WSUSURL` in the `WSUSLocationReply`. The CMG SUP will also be listed as the server for the update scan in the **WUAHandler.log**.

## LEDBAT support for software update points

You can now enable Windows Low Extra Delay Background Transport (LEDBAT) for your software update points. LEDBAT adjusts download speeds during client scans against WSUS to help control network congestion.

If a site system has both the distribution point and software update point roles, you can configure LEDBAT independently on the roles. For example, if you only enable LEDBAT on the distribution point role, the software update point role doesn't inherit the same configuration.

For more general information on Windows LEDBAT, see [Fundamental concepts for content management](../../plan-design/hierarchy/fundamental-concepts-for-content-management#windows-ledbat).

### Prerequisites for LEDBAT on software update points

To use LEDBAT in this scenario, install the software update point role on a site system running Windows Server 2016 or later.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Servers and Site System Roles** node.
2. Select a site system that has the software update point role.
3. In the details pane of site system roles, select the **Software update point** role.
4. In the ribbon, on the **Site Role** group, select **Properties**.
5. On the **General** tab of the software update point properties, enable the following setting: **Adjust the download speed to use the unused network bandwidth (Windows LEDBAT)**.

## Improvements to Power BI Report Server Integration

We've made the following improvements for Power BI Report Server integration:

- You can now use Microsoft Power BI Desktop (Optimized for Power BI Report Server) versions that were released after January 2021
- Configuration Manager now correctly handles Power BI reports saved by Power BI Desktop (optimized for Power BI Report Server) May 2021 or later.
    - Reports saved by Power BI Desktop (optimized for Power BI Report Server) May 2021 or later function in earlier versions of Configuration Manager. However, you might experience delays updating the data source on newly updated reports, or receive `The remote server returned an error; (400) Bad Request.` errors in the **SRSRP.log**. For more information about the relevant change to Power BI Desktop (optimized for Power BI Report Server) May 2021, see [Change data source connection strings in Power BI reports](/en-us/power-bi/report-server/connect-data-source-apis).

## Tenant attach features are generally available

The following [tenant attach](../../../tenant-attach/) features are now generally available:

- Client details
- Applications
- Device timeline
- Resource explorer
- CMPivot
- Scripts
- Bitlocker Recovery Keys
- Collections

## Deployment Status client notification actions

You can now perform client notification actions, including **Run Scripts**, from the **Deployment Status** view. To run client notification actions from the **Deployment Status** view:

1. Go to the **Deployments** node in the **Monitoring** workspace.
2. Select a deployment, then select **View Status**, or double-click on the deployment.
3. Right-click on either a group of clients in a **Category** or a single client in the **Asset details**pane to display the client notification actions.
    - Currently, any user can perform these actions, but they’ll receive a permissions error if they don't have the correct permissions.
    - Currently, when there are no devices associated with the deployment status, the client notification actions display but won't trigger any notifications.

[![Screenshot of the Deployment Status view showing the client notification actions. ](media/70779837-client-notification.png)](media/70779837-client-notification.png#lightbox)

## Sort by icon in the console

Based on your feedback, in the Configuration Manager console you can now sort by icon. Any node that uses different icons now sorts properly. This improvement helps you easily group objects of a similar type.

The following example shows the **Devices** node sorted by icon, which is the [device status](../../clients/manage/monitor-clients#monitor-individual-clients):

![The Devices node in the Configuration Manager console sorted by the Icon column.](media/3877839-devices-sort-icon.png)

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Get-CMAADTenant

Use this cmdlet to get a Microsoft Entra tenant from the site.

```powershell
Get-CMAADTenant
Get-CMAADTenant -Id $id
Get-CMAADTenant -Name $name
```

#### Set-CMCollectionCloudSync

Use this cmdlet to configure the following cloud sync features for a collection:

- Make a collection available to assign endpoint security policies from the Microsoft Intune admin center. For more information, see [Tenant attach: Onboard Configuration Manager clients to Microsoft Defender for Endpoint from the admin center](../../../tenant-attach/atp-onboard).
- Synchronize collection member results to Microsoft Entra groups. For more information, see [Synchronize members to Microsoft Entra groups](../../clients/manage/collections/create-collections#bkmk_aadcollsync).

```powershell
Set-CMCollectionCloudSync -Name $name -EnableAssignEndpointSecurityPolicy $true -TenantId $tenantId -AddGroupName $array  -Verbose
Set-CMCollectionCloudSync -Id $collectionId -TenantName $tenantName -RemoveGroupName $array1  -AddGroupName $array2
$collectionObj | Set-CMCollectionCloudSync TenantObject $tenantObj  -RemoveGroupName $array1  -AddGroupName $array2
```

### Modified cmdlets

#### Get-CMDeploymentTypeDetectionClause

For more information, see [Get-CMDeploymentTypeDetectionClause](/en-us/powershell/module/configurationmanager/Get-CMDeploymentTypeDetectionClause).

**Non-breaking changes**

The cmdlet can now get a detection clause from a script deployment type.

#### Get-CMDeploymentStatusDetails

For more information, see [Get-CMDeploymentStatusDetails](/en-us/powershell/module/configurationmanager/Get-CMDeploymentStatusDetails).

**Bugs that were fixed**

Updated the cmdlet to avoid a potential null reference error.

#### Import-CMApplication

For more information, see [Import-CMApplication](/en-us/powershell/module/configurationmanager/Import-CMApplication).

**Non-breaking changes**

Updated the import logic to align with console. Added new warning messages.

#### New-CMCoManagementPolicy

For more information, see [New-CMCoManagementPolicy](/en-us/powershell/module/configurationmanager/New-CMCoManagementPolicy).

**Non-breaking changes**

The cmdlet now supports applicability for Windows 11 on ARM64 devices.

#### New-CMApplication

For more information, see [New-CMApplication](/en-us/powershell/module/configurationmanager/New-CMApplication).

**Non-breaking changes**

It can now get an application icon from the specified file.

#### New-CMTaskSequence

For more information, see [New-CMTaskSequence](/en-us/powershell/module/configurationmanager/New-CMTaskSequence).

**Non-breaking changes**

Added the **IconLocationFile** parameter to support specifying an icon for the task sequence. For more information, see Support for task sequence and package icons.

#### New-CMTaskSequenceDeployment

For more information, see [New-CMTaskSequenceDeployment](/en-us/powershell/module/configurationmanager/New-CMTaskSequenceDeployment).

**Bugs that were fixed**

Fixed an issue with the **AllowSharedContent** parameter.

#### Publish-CMThirdPartySoftwareUpdateContent

For more information, see [Publish-CMThirdPartySoftwareUpdateContent](/en-us/powershell/module/configurationmanager/Publish-CMThirdPartySoftwareUpdateContent).

**Non-breaking changes**

Added the **Force** parameter to run the command without asking for confirmation.

#### Set-CMSoftwareUpdatePointComponent

For more information, see [Set-CMSoftwareUpdatePointComponent](/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdatePointComponent).

**Non-breaking changes**

Added the **NonWindowsUpdateMaxRuntimeMins** parameter to change the default maximum run time for non-Windows software updates.

#### Set-CMTaskSequence

For more information, see [Set-CMTaskSequence](/en-us/powershell/module/configurationmanager/Set-CMTaskSequence).

**Non-breaking changes**

Added the **IconLocationFile** parameter to support specifying an icon for the task sequence. For more information, see Support for task sequence and package icons.

#### Set-CMTaskSequenceDeployment

For more information, see [Set-CMTaskSequenceDeployment](/en-us/powershell/module/configurationmanager/Set-CMTaskSequenceDeployment).

**Bugs that were fixed**

Fixed an issue with the **AllowSharedContent** parameter.

#### Start-CMTaskSequenceDeployment

For more information, see [Start-CMTaskSequenceDeployment](/en-us/powershell/module/configurationmanager/Start-CMTaskSequenceDeployment).

**Bugs that were fixed**

Fixed an issue with the **AllowSharedContent** parameter.

## Improved notice for content on task sequence media

When you create task sequence media in the Configuration Manager console, you have to select distribution points that contain the content required by the task sequence. If some content isn't available on the selected distribution points, the wizard would display an error that simply said some packages aren't available.

Based on your feedback, this message now includes the list of package IDs for the content that's not available. This change makes the notice more actionable, so you can more easily see what content is missing. This information is also listed in the CreateTsMedia.log file.

![Error message during task sequence media wizard when content isn't available on distribution points that lists the missing package IDs.](media/12895956-tsmedia-error.png)