---
layout: Conceptual
title: Technical preview 2005 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2005
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2005.
ms.date: 2020-05-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 7c4718b7-9f68-aac5-06ef-bb1193dc1b3e
document_version_independent_id: 2d342075-25eb-1d6c-ab5d-365da842e102
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2005.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2005
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2005.md
platformId: 47ed658a-f505-38d5-8437-2713bff5a6a7
---

# Technical preview 2005 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2005. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Tenant attach: Device timeline in the admin center

When Configuration Manager synchronizes a device to Microsoft Intune through tenant attach, you can now see a timeline of events. This timeline shows past activity on the device that can help you troubleshoot problems.

Important

This is a preview experience. The final location will be the devices blade in Microsoft Intune admin center.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Prerequisites

You'll need to meet all of the prerequisites for [Tenant attach: ConfigMgr client details](technical-preview-2004#bkmk_mem):

- An environment that's [tenant attached with uploaded devices](../../../tenant-attach/device-sync-actions).
- One of the following browsers:
    - Microsoft Edge, version 77 and later
    - Google Chrome
- The user account has been discovered with both [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
    - Meaning the user account needs to be a synced user object in Azure.

Additionally, you'll need the following items:

- Enable Endpoint analytics data collection in Configuration Manager:
    1. In the Configuration Manager console, go to **Administration** &gt; **Client Settings** &gt; **Default Client Settings**.
    2. Right-click and select **Properties** then select the **Computer Agent** settings.
    3. Set **Enable Endpoint analytics data collection** to **Yes**.
        - Only events collected after the client receives this policy will be visible in the admin center preview. Events prior to receiving the policy won't be accessible.

#### Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission under **Collection** in Configuration Manager.
- The **Admin User**role for the Configuration Manager Microservice application in Microsoft Entra ID.
    - Add the role in Microsoft Entra ID from **Enterprise applications** &gt; **Configuration Manager Microservice** &gt; **Users and groups** &gt; **Add user**. Groups are supported if you have Microsoft Entra ID P1 or P2.

#### Generate events

Devices send events once a day to the admin center. Only events collected after the client receives the **Enable Endpoint analytics data collection** policy are visible in the admin center preview. Because of this, you may want to generate events to view in the timeline. Generate test events easily by installing an application or an update from Configuration Manager, or restart the device. Collecting Configuration Manager events requires a device restart. Events are retained for 30 days. Use the bellow chart to view events that are collected:

##### Collected events

| Event name | Provider name | Event ID |
| --- | --- | --- |
| Application Error | Application Error | 1000 |
| Application Hang | Application Hang | 1002 |
| Kernel Crash | Microsoft-Windows-WER-SystemErrorReporting | 1001 |
| Application Crash | Windows Error Reporting | 1001 |
| Windows Update Agent – Update Installation | Microsoft-Windows-WindowsUpdateClient | 19 |
| Unknown Shutdown | Boot | 0 |
| Initiated Shutdown | Boot | 1074 |
| Abnormal Shutdown | Boot | 41 |
| Boundary Group Change | Microsoft-ConfigMgr | 20000 |
| Application Deployment | Microsoft-ConfigMgr | 20001 |
| Configuration Manager – Update Installation | Microsoft-ConfigMgr | 20002 |
| Firmware version change | Microsoft-ConfigMgr | 20003 |

#### View the timeline

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace and select the **Devices** node.
2. Right-click on a device that's been uploaded to Microsoft Intune.
3. In the right-click menu, select **Start** &gt; **Admin Center Preview** to open the preview in your browser.
4. Click on **Timeline**. By default, you're shown events from the last 24 hours.
    - Use the **Filter** button to change the **Time range**, **Event levels**, and **Provider name**.
    - If you click on an event, you'll see the detailed message for it.
    - The device sends events once a day to the admin center. Select **Refresh** to reload the page and have the device send new uncollected events to the admin center preview. You'll need to select **Refresh** again after a few minutes to see the newly collected events.

[![Timeline of events for a device](media/7141381-timeline.png)](media/7141381-timeline.png#lightbox)

## Tenant attach: Install an application from the admin center

You can now initiate an application install in real time for a tenant attached device from the Microsoft Endpoint Management admin center.

Important

This is a preview experience. The final location will be the devices blade in Microsoft Intune admin center.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Prerequisites

You'll need to meet all of the prerequisites for [Tenant attach: ConfigMgr client details](technical-preview-2004#bkmk_mem):

- An environment that's [tenant attached with uploaded devices](../../../tenant-attach/device-sync-actions).
- One of the following browsers:
    - Microsoft Edge, version 77 and later
    - Google Chrome
- The user account has been discovered with both [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
    - Meaning the user account needs to be a synced user object in Azure.

Additionally, you'll need the following items:

- Enable the optional feature **Approve application requests for users per device**. For more information, see [Enable optional features from updates](../../servers/manage/optional-features).
- At least one application deployed to a device collection with the **An administrator must approve a request for this application on the device** option set on the deployment. For more information, see [Approve applications](../../../apps/deploy-use/app-approval#bkmk_opt).
    - User targeted applications or applications without the approval option set don't appear in the application list.

#### Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read** permission for **Application** in Configuration Manager.
- The **Approve** permission for **Application** in Configuration Manager.
- The **Admin User**role for the Configuration Manager Microservice application in Microsoft Entra ID.
    - Add the role in Microsoft Entra ID from **Enterprise applications** &gt; **Configuration Manager Microservice** &gt; **Users and groups** &gt; **Add user**. Groups are supported if you have Microsoft Entra ID P1 or P2.

#### Deploy an application from the admin center

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace and select the **Devices** node.
2. Right-click on a device that's been uploaded to Microsoft Intune.
3. In the right-click menu, select **Start** &gt; **Admin Center Preview** to open the preview in your browser.
4. Go to **Applications** in the admin center preview.
5. Select the application and click **Install**.

#### Known issues

In this technical preview, you can only use alphanumeric characters when searching applications.

## Tenant attach: CMPivot from the admin center

Bring the power of CMPivot to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to be able to initiate real-time queries from the cloud against an individual ConfigMgr managed device and return the results back to the admin center. This gives all the traditional benefits of CMPivot, which allows IT Admins and other designated personas the ability to quickly assess the state of devices in their environment and take action.

For more information about CMPivot, see:

- [CMPivot sample scripts](../../../tenant-attach/cmpivot-samples-attached)
- [CMPivot overview](../../../tenant-attach/cmpivot-overview-attached).

Important

This is a preview experience. The final location will be the devices blade in Microsoft Intune admin center.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Prerequisites

You'll need to meet all of the prerequisites for [Tenant attach: ConfigMgr client details](technical-preview-2004#bkmk_mem):

- An environment that's [tenant attached with uploaded devices](../../../tenant-attach/device-sync-actions).
- One of the following browsers:
    - Microsoft Edge, version 77 and later
    - Google Chrome
- The user account has been discovered with both [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
    - Meaning the user account needs to be a synced user object in Azure.

Additionally, the following items are required to use CMPivot:

- Upgrade the target devices to the latest version of the Configuration Manager client.
- Target clients require a minimum of PowerShell version 4.
- To gather data for the following entities, target clients require PowerShell version 5.0:
    - Administrators
    - Connection
    - IPConfig
    - SMBConfig

#### Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Admin User** role for the Configuration Manager Microservice application in Microsoft Entra ID.

    - Add the role in Microsoft Entra ID from **Enterprise applications** &gt; **Configuration Manager Microservice** &gt; **Users and groups** &gt; **Add user**. Groups are supported if you have Microsoft Entra ID P1 or P2.
- Configuration Manager permissions for CMPivot:

    - **Read** permission on the **SMS Scripts** object
    - **Run Scripts** permission on the **Collection**.
        - Alternatively, you can use **Run CMPivot** on **Collection**.
        - **Run Scripts** is a super set of the **Run CMPivot** permission.
    - **Read** permission on **Inventory Reports**
    - The default scope.

#### Use CMPivot from the admin center preview

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace and select the **Devices** node.
2. Right-click on a device that's been uploaded to Microsoft Intune.
3. In the right-click menu, select **Start** &gt; **Admin Center Preview** to open the preview in your browser.
4. Select **CMPivot**, type your query in the script pane, then click **Run**.
    - For query examples, see [CMPivot sample scripts](../../../tenant-attach/cmpivot-samples-attached).
    - For information about CMPivot entities, operators, and functions, see [CMPivot overview](../../../tenant-attach/cmpivot-overview-attached).

## Tenant attach: Run Scripts from the admin center

Bring the power of the Configuration Manager on-premises Run Scripts feature to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to run PowerShell scripts from the cloud against an individual Configuration Manager managed device. This gives all the traditional benefits of PowerShell scripts that have already been defined and approved by the Configuration Manager admin to this new environment.

Important

This is a preview experience. The final location will be the devices blade in Microsoft Intune admin center.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Prerequisites

You'll need to meet all of the prerequisites for [Tenant attach: ConfigMgr client details](technical-preview-2004#bkmk_mem):

- An environment that's [tenant attached with uploaded devices](../../../tenant-attach/device-sync-actions).
- One of the following browsers:
    - Microsoft Edge, version 77 and later
    - Google Chrome
- The user account has been discovered with both [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
    - Meaning the user account needs to be a synced user object in Azure.

Additionally, you'll need the following items:

- Configuration Manager clients must be running the latest version client.
- To run PowerShell scripts, the client must be running PowerShell version 3.0 or later.
    - If a script you run contains functionality from a later version of PowerShell, the client on which you run the script must be running that later version of PowerShell.
- At least one script that is already created and approved in Configuration Manager.
    - Scripts that have parameters aren't supported at this time and won't be visible in the Microsoft Intune admin center.
    - Only scripts that are already created and approved appear in the admin center. For more information on approving scripts, see [Approve or deny a script](../../../apps/deploy-use/create-deploy-scripts#run-script-authors-and-approvers).

#### Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Admin User**role for the Configuration Manager Microservice application in Microsoft Entra ID.
    - Add the role in Microsoft Entra ID from **Enterprise applications** &gt; **Configuration Manager Microservice** &gt; **Users and groups** &gt; **Add user**. Groups are supported if you have Microsoft Entra ID P1 or P2.
- To use scripts, you must be a member of the appropriate Configuration Manager security role. For more information, see [Security scopes for run scripts](../../../apps/deploy-use/create-deploy-scripts#bkmk_ScriptRoles).
- To run scripts, the account must have **Run Script** permissions for **Collections**.

#### Run a script

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace and select the **Devices** node.
2. Right-click on a device that's been uploaded to Microsoft Intune.
3. In the right-click menu, select **Start** &gt; **Admin Center Preview** to open the preview in your browser.
4. Select **Scripts**, then select one of your scripts. If needed, you can search by script name.
5. Click **Run script**from the page that appears on the right.
    - You'll be notified your script has started. The **Run script** button will be disabled until it's complete.
    - The **State** column is only valid while you're on the page. The state is reset to `Ready` if you navigate to another page.
6. When the script completes, the results will show in the **Output** pane. You can copy the text of the script output.

[![Script output in the admin center](media/6234688-script-output.png)](media/6234688-script-output.png#lightbox)

## VPN boundary type

To simplify managing remote clients, you can now create a new boundary type for VPNs.

Previously, you had to create boundaries for VPN clients based on the IP address or subnet. This configuration could be challenging or not possible because of the subnet configuration or the VPN design.

Now when a client sends a location request, it includes additional information about its network configuration. Based upon this information, the server determines whether the client is on a VPN. All clients that connect through a VPN automatically belong to the boundary group associated with this new boundary type.

For more information about boundaries, see [Define site boundaries and boundary groups](../../servers/deploy/configure/define-site-boundaries-and-boundary-groups).

### Prerequisites for VPN boundary

To take full advantage of this feature, after you update the site, also update clients to the latest version. New functionality appears in the Configuration Manager console when you update the site and console. The complete scenario isn't functional until the client version is also the latest.

To use this VPN boundary during an OS deployment, make sure to also update the boot image to include the latest client binaries.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Hierarchy Configuration**, and then select the **Boundaries** node.
2. In the ribbon, select **Create Boundary**.
3. Specify a **Description**, for example `VPN boundary`.
4. For the **Type**, select **VPN**. There are currently no additional configurations for this boundary type. Select **OK** to save and close.
5. Create a boundary group that includes this new VPN boundary. For more information, see [Create a boundary group](../../servers/deploy/configure/boundary-group-procedures#create-a-boundary-group).

### Known issues for VPN boundary

- You can only create one VPN boundary.
- The **Boundary** value in the console list is always `AUT:1`.
- The VPN detection logic may vary with different VPN solutions. If it doesn't work with your VPN, [file a frown](technical-preview-2003#bkmk_feedback). Share details of your implementation to help improve the detection logic.

## Microsoft Entra authentication in Software Center

This release fixes an issue with Software Center and Microsoft Entra authentication. For a client detected as on the intranet but communicating via the cloud management gateway (CMG), previously Software Center would use Windows authentication. When it tried to get the list of user available apps, it would fail. It now uses Microsoft Entra identity for devices joined to Microsoft Entra ID. These devices can be cloud-joined or hybrid-joined.

## Install and upgrade the client on a metered connection

Previously, if the device was connected to a metered network, new clients wouldn't install. Existing clients only upgraded if you allowed all client communication. For devices that are frequently roaming on a metered network, they would be unmanaged or on an older client version. Starting in this release, client install and upgrade both work when you set the client setting **Client communication on metered internet connections** to **Allow**.

To define the behavior for a new client installation, there's a new ccmsetup parameter **/AllowMetered**. When you allow client communication on a metered network for ccmsetup, it downloads the content, registers with the site, and downloads the initial policy. Any further client communication follows the configuration of the client setting from that policy.

If you reinstall the client on an existing device, it uses the following priority to determine its configuration:

1. Existing local client policy
2. The last command line stored in the Windows registry
3. Parameters on the ccmsetup command line

For more information, see the following articles:

- [About client settings](../../clients/deploy/about-client-settings#client-communication-on-metered-internet-connections)
- [About client installation parameters and properties](../../clients/deploy/about-client-installation-properties)

### Known issue with install and upgrade on metered connections

If you configure the client setting to **Limit**, the client won't install or upgrade. To work around this issue, configure the client setting to **Allow**.

## Task sequence media support for cloud-based content

Task sequence media can now download cloud-based content. For example, you send a USB key to a user at a remote office to reimage their device. Or an office that has a local PXE server, but you want devices to prioritize cloud services as much as possible. Instead of further taxing the WAN to download large OS deployment content, boot media and PXE deployments can now get content from cloud-based sources. For example, a cloud management gateway (CMG) that you enable to share content.

Note

The device still needs an intranet connection to the management point.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. Enable the following client setting in the **Cloud Services** group: **Allow access to cloud distribution point**. Make sure the client setting is deployed to the target clients. For more information, see the following articles:

    - [How to configure client settings](../../clients/deploy/configure-client-settings)
    - [About client settings - Cloud services](../../clients/deploy/about-client-settings#cloud-services)
2. For the boundary group that the client is in, associate the content-enabled CMG or cloud distribution point site systems. For more information, see [Configure a boundary group](../../servers/deploy/configure/boundary-group-procedures#configure-a-boundary-group).
3. On the same boundary group, enable the following option: **Prefer cloud based sources over on-premise sources**. For more information, see [Boundary group options for peer downloads](../../servers/deploy/configure/boundary-group-options).
4. Distribute the content referenced by the task sequence to the content-enabled CMG or cloud distribution point.
5. Start the task sequence from boot media or PXE on the client.

When the task sequence runs, it will download content from the cloud-based sources. Review **smsts.log** on the client.

## Improvements to cloud management gateway cmdlets

With more customers managing remote devices now, this release includes several new and improved Windows PowerShell cmdlets for the cloud management gateway (CMG). You can use these cmdlets to automate the creation, configuration, and management of the CMG service and Microsoft Entra requirements.

Note

While some of the new cmdlets might work with other Azure services, they're only tested with the **Cloud management** connection to support the CMG.

For example, an Azure administrator first creates the two required apps in Microsoft Entra ID. Then you write a script that uses the following cmdlets to deploy a CMG:

1. **Import-CMAADServerApplication**: Create the Microsoft Entra server app definition in Configuration Manager.
2. **Import-CMAADClientApplication**: Create the Microsoft Entra client app definition in Configuration Manager.
3. Use **Get-CMAADApplication** to get the app objects, and then pass to **New-CMCloudManagementAzureService** to create the Azure service connection in Configuration Manager.
4. **New-CMCloudManagementGateway**: Create the CMG service in Azure.
5. **Add-CMCloudManagementGatewayConnectionPoint**: Create the CMG connection point site system.

For more information, see [Overview of cloud management gateway](../../clients/manage/cmg/overview).

For more information on using PowerShell with Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

You can continue to use the following existing CMG cmdlets:

- [Add-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Add-CMCloudManagementGatewayConnectionPoint)
- [Get-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Get-CMCloudManagementGateway)
- [Get-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Get-CMCloudManagementGatewayConnectionPoint)
- [New-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/New-CMCloudManagementGateway)
- [Remove-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Remove-CMCloudManagementGateway)
- [Remove-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Remove-CMCloudManagementGatewayConnectionPoint)
- [Set-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Set-CMCloudManagementGateway)
- [Set-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Set-CMCloudManagementGatewayConnectionPoint)
- [Start-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Start-CMCloudManagementGateway)
- [Stop-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Stop-CMCloudManagementGateway)

The following existing cmdlets have significant improvements. For more information, see the sections below:

- New-CMCloudManagementGateway
- Set-CMCloudManagementGateway

### Get-CMAzureService

Use this cmdlet to get the Azure service. For more information, see [Configure Azure services](../../servers/deploy/configure/azure-services-wizard).

#### Example 1: Get the Azure service by name

The following example gets the Azure service from the site by its name. The **Name** is the same value as in the **Azure Services** node in the console.

```powershell
Get-CMAzureService -Name "Contoso"
```

#### Example 2: Get the Azure service by ID

The following example gets the Azure services from the site by its ID. The **Id** is the integer value stored in the site database for the service. For example, run the following SQL query, and look at the **ID** column: `select * from Azure_CloudService`.

```powershell
Get-CMAzureService -Id 2
```

### Remove-CMAzureService

Use this cmdlet to remove the Azure service. Its behavior and parameters are similar to the Get-CMAzureService cmdlet.

#### Example 1: Remove the Azure service by name

```powershell
Remove-CMAzureService -Name "Contoso"
```

#### Example 2: Force remove the Azure service by its ID

```powershell
Remove-CMAzureService -Id 2 -Force
```

#### Example 3: Get the Azure service by name and then remove it

```powershell
Get-CMAzureService -Name "Contoso" | Remove-CMAzureService
```

### Get-CMAADApplication

Use this cmdlet to get the Microsoft Entra app object from the site. It's commonly used with the New-CMCloudManagementAzureService cmdlet.

#### Example 1: Get Microsoft Entra client apps by tenant name

This example returns all client apps in the specified tenant.

```powershell
Get-CMAADApplication -TenantName "Contoso" -AppType ClientApplication
```

#### Example 2: Get Microsoft Entra server apps by tenant ID

This example returns all server apps in the specified tenant.

```powershell
Get-CMAADApplication -TenantId "aaaabbbb-0000-cccc-1111-dddd2222eeee" -AppType ServerApplication
```

#### Example 3: Get a Microsoft Entra app by its name

```powershell
Get-CMAADApplication -AppName "CmgServerApp"
```

### Import-CMAADServerApplication

Use this cmdlet to import the web/server app from Microsoft Entra ID, and define it for the Configuration Manager site. It assumes that an Azure administrator already created the app in Microsoft Entra ID.

```powershell
$date =(Get-Date).Date.AddDays(3)

Import-CMAADServerApplication -TenantName "Contoso" -TenantId "aaaabbbb-0000-cccc-1111-dddd2222eeee" -AppName "CmgServerApp" -ClientId "7078946d-fc1c-43b7-8dee-dd6e6b00d783" -SecretKey "1uXGR^!0@Cjas6qI*J02ZeS&&zY19^hC*9" -SecretKeyExpiry $date
```

### Import-CMAADClientApplication

Use this cmdlet to import the client app from Microsoft Entra ID, and define it for the Configuration Manager site. It assumes that an Azure administrator already created the app in Microsoft Entra ID.

Tip

The ClientId value is the **Application (client) ID** of the app in Microsoft Entra ID.

#### Example 1: Import the client app based on the tenant ID

```powershell
Import-CMAADClientApplication -TenantId "aaaabbbb-0000-cccc-1111-dddd2222eeee" -AppName "CmgClientApp" -ClientId "cf114f48-88db-4829-ac45-0c186e86dbf6"
```

#### Example 2: Import the client app based on the server app

```powershell
$serverApp = Get-CMAADApplication -TenantName "Contoso" -AppType ServerApplication -AppName "CmgServerApp"

Import-CMAADClientApplication -ServerApp $serverApp -AppName "CmgClientApp" -ClientId "cf114f48-88db-4829-ac45-0c186e86dbf6"
```

### New-CMCloudManagementAzureService

Use this cmdlet to create the Azure service in Configuration Manager for **Cloud Management**.

```powershell
$serverApp = Get-CMAADApplication -TenantName "Contoso" -AppType ServerApplication -AppName "CmgServerApp"

$clientApp = Get-CMAADApplication -TenantName "Contoso" -AppType ClientApplication -AppName "CmgClientApp"

New-CMCloudManagementAzureService -Name "Contoso" -Description "Azure Service" -ServerApp $serverApp -ClientApp $clientApp -AzureEnvironmentOption AzurePublicCloud
```

### Set-CMCloudManagementAzureService

Use this cmdlet to modify the settings of the Azure service in Configuration Manager for **Cloud Management**.

```powershell
Get-CMAzureService -Name "Contoso" | Set-CMCloudManagementAzureService -NewName "CMG service" -Description "ConfigMgr connection to Contoso tenant for CMG"
```

### New-CMCloudManagementGateway

This existing cmdlet includes the following new parameters:

- **EnvironmentSetting**: Specify the Azure environment, for example `AzurePublicCloud`
- **ServerAppClientID**: Specify the client ID of the Microsoft Entra server app. Use this parameter for non-user interaction mode. In the CMG properties, this value is the **Microsoft Entra app name**.
- **ServiceCertPath**: Specify the [CMG server authentication certificate](../../clients/manage/cmg/server-auth-cert).
- **ServiceCertPassword**: Specify the password for the service certificate.
- **ServiceName**: Specify the Azure service name. If you don't specify this parameter, Configuration Manager uses the service certificate's first DNS name. If the certificate has more than one DNS name, use this parameter to specify which one to use.
- **Region**: Specify the Azure service region, for example: ...
- **IsUsingExistingGroup**: Specify if the Azure resource group already exists.
- **GroupName**: Specify the name of the Azure resource group.
- **VMInstanceCount**: Specify the instance count of virtual machines.
- **CheckClientCertRevocation**: Enable or disable the option to **Verify client certificate revocation**.
- **EnforceProtocol**: Enable or disable the option to **Enforce TLS 1.2**.
- **EnableCloudDPFunction**: Enable or disable the option to **Allow CMG to function as a cloud distribution point and serve content from Azure storage**.
- **EnableTrafficOut**: Enable or disable the option to **Turn on 14-day threshold and alerts for monitoring outbound data transfer**.
- **TrafficOutStopService**: Enable or disable the option to **Stop this service when the critical threshold is exceeded**.

    Tip

    Use the following existing parameters to configure the specific threshold amount and alert percentages: **TrafficOutGB**, **TrafficWarningPct**, **TrafficCriticalPct**.
- **EnableStorageQuota**: Enable or disable the option to **Specify storage alert threshold**.
- **StorageQuotaGB**: Specify an integer value for the **Storage alert threshold (GB)**. For example, `2`.
- **StorageWarningPct**: Specify an integer value for the **Generate Warning alert (% of storage alert threshold)**. For example, `50`.
- **StorageCriticalPct**: Specify an integer value for the **Generate Critical alert (% of storage alert threshold)**. For example, `90`.
- **CARootCert**: Add root certificates to the cloud service.
- **Force**: If the service certificate contains multiple DNS names, use this parameter to avoid warnings from the cmdlet.

#### Example 1

```powershell
$Path = "c:\TestPath\RootCA.cer"
$Type = [Microsoft.ConfigurationManagement.AdminConsole.AzureServices.CertificateStore]::RootCA
$Cert =@{$Path = $Type}

$Password = "0HNy*c@63kAe" | ConvertTo-SecureString -AsPlainText -Force

New-CMCloudManagementGateway -ServiceCertPath "c:\TestPath\ServiceCert.pfx" -EnvironmentSetting AzurePublicCloud -SubscriptionId "aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e" -ServiceCertPassword $Password -ServiceName "GraniteFalls.CloudApp.Net" -Description "EastUS CMG for Contoso" -Region EastUS -VMInstanceCount 2 -CARootCert $Cert -CheckClientCertRevocation $False -EnforceProtocol $True -IsUsingExistingGroup $true -GroupName "Resource group 1"
```

#### Example 2

```powershell
New-CMCloudManagementGateway -ServiceCertPath "c:\TestPath\ServiceCert.pfx" -EnvironmentSetting AzurePublicCloud -SubscriptionId "aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e" -ServiceCertPassword $Password -ServiceName "GraniteFalls.CloudApp.Net" -Description "EastUS CMG for Contoso" -Region EastUS -VMInstanceCount 2 -CARootCert $Cert -CheckClientCertRevocation $False -EnforceProtocol $True -GroupName "Resource group 1" -EnableCloudDPFunction $true -EnableTrafficOut $true -TrafficOutStopService $true -TrafficOutGB 10000 -TrafficWarningPct 50 -TrafficCriticalPct 90 -EnableStorageQuota $true -StorageQuotaGB 2000 -StorageWarningPct 50 -StorageCriticalPct 90 -Force
```

### Set-CMCloudManagementGateway

This existing cmdlet includes the following new parameters. For more information on these parameters, see the descriptions in the section for New-CMCloudManagementGateway.

- EnableTrafficOut
- TrafficOutStopService
- EnableStorageQuota
- StorageQuotaGB
- StorageWarningPct
- StorageCriticalPct
- EnforceProtocol
- CARootCert
- RemoveCertThumbprints
- EnableCloudDPFunction

#### Example 1: Change the CMG alerts configuration

```powershell
Set-CMCloudManagementGateway -Name "GraniteFalls" -EnableTrafficOut $true -TrafficOutGB 10000 -TrafficWarningPct 50 –TrafficCriticalPct 90 -EnableStorageQuota $true -StorageQuotaGB 2000 -StorageWarningPct 50 -StorageCriticalPct 90
```

#### Example 2: Change the number of virtual machines for the CMG service

```powershell
Set-CMCloudManagementGateway -Name "GraniteFalls" -VMInstancesCount 4
```

#### Example 3: Enable the CMG to serve content from Azure storage

```powershell
Set-CMCloudManagementGateway -Name "GraniteFalls" -EnableCloudDPFunction $true
```

#### Example 4: Add two new certificate authorities

```powershell
$path1 = "folder\root.cer"
$type1 = [Microsoft.ConfigurationManagement.AdminConsole.AzureServices.CertificateStore]::RootCA

$path2 = "folder\intermediate.cer"
$type2 = [Microsoft.ConfigurationManagement.AdminConsole.AzureServices.CertificateStore]::IntermediateCA

$cert = @{$path1 = $type1; $path2 = $type2}

Set-CMCloudManagementGateway -Name "GraniteFalls" -CARootCert $cert
```

#### Example 5: Update the CMG server authentication certificate

```powershell
Set-CMCloudManagementGateway -Name "GraniteFalls" -ServiceCertPath "c:\TestPath\NewServiceCert.pfx" -ServiceCertPassword (ConvertTo-SecureString -String "tX*xJ11Nuo^B" -AsPlainText -Force)
```

#### Example 6: Remove a root certificate from a CMG

```powershell
Set-CMCloudManagementGateway -Name "GraniteFalls" -RemoveCertThumbprints "A7CBA0014DEF847593569D05003D5B96A1D6A627"
```

Note

The certificate thumbprint currently can't include any lowercase characters.

## Community hub and GitHub

The IT Admin community has developed a wealth of knowledge over the years. Rather than reinventing items like Scripts and Reports from scratch, we've built a **Configuration Manager Community hub** where IT Admins can share with each other. By leveraging the work of others, you can save hours of work. The Community hub fosters creativity by building on others' work and having other people build on yours. GitHub already has industry-wide processes and tools built for sharing. Now, the Community hub will leverage those tools directly in the Configuration Manager Console as foundational pieces for driving this new community. For the initial release, the content made available in the Community hub will be uploaded only by Microsoft. Currently, you can't upload your own content to GitHub for use by Community hub.

Community hub supports the following objects:

- PowerShell Scripts
- Reports
- Task sequences
- Applications
- Configuration items

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

#### Prerequisites

- The device running the Configuration Manager console used to access the hub needs the following items:

    - Windows 10 build 17110 or higher
    - .NET Framework version 4.6 or higher
- To download reports, you need to turn on the option **Use Configuration Manager-generated certificates for HTTP site systems** at the site you're importing into. For more information, see [enhanced HTTP](/en-us/sccm/core/plan-design/hierarchy/enhanced-http).

    1. Go to **Administration** &gt; **Site Configuration** &gt; **Sites**.
    2. Select the site and choose **Properties** in the ribbon.
    3. On the **Communication Security** tab, select the option to **Use Configuration Manager-generated certificates for HTTP site systems**.

#### Permissions

- To import a script: **Create** permission for SMS\_Scripts class.
- To import a report: Full Administrator security role.

#### Use the Community hub

1. Go to the **Community hub** node in the **Community** workspace.
2. Select an item to download.
3. You'll need appropriate permissions in your Configuration Manager site to download objects from the hub and import them into the site.
    - To import a script: **Create** permission for SMS\_Scripts class.
    - To import a report: Full Administrator security role.
4. Downloaded reports are deployed to a report folder called **hub** on the reporting services point. Downloaded scripts can be seen in the **Run Scripts** node.
5. View all items downloaded from the hub by your organization by clicking on **Your downloads** from the **Community hub** node.

[![All items downloaded from the community hub](media/3555935-community-hub-downloads.png)](media/3555935-community-hub-downloads.png#lightbox)

## Microsoft 365 Apps for enterprise

Office 365 ProPlus was renamed to Microsoft 365 Apps for enterprise on April 21, 2020. Starting in this technical preview the following changes have been made:

- The Configuration Manager console has been updated to use the new name.
    - This change also includes update channel names for Microsoft 365 Apps.
- A banner notification was added to the console to notify you if one or more automatic deployment rules reference obsolete channel names in the **Title** criteria for Microsoft 365 Apps updates.

If you use **Title** as criteria for Microsoft 365 Apps updates in your automatic deployment rules, use the next section to help modify them.

### Update channel information for Microsoft 365 Apps

When Office 365 ProPlus was renamed to **Microsoft 365 Apps for enterprise**, the update channels were also renamed. If you use an automatic deployment rule to deploy updates, you'll need to make changes to your rules if they rely on the **Title** property. That's because the name of update packages in the Microsoft Update Catalog is changing.

Currently, the title of an update package for Office 365 ProPlus begins with "Office 365 Client Update" as seen in the following example:

 Office 365 Client Update - Semi-annual Channel Version 1908 for x64 based Edition (Build 11929.20648)

For update packages released on and after June 9, the title will begin with "Microsoft 365 Apps Update" as seen in the following example:

 Microsoft 365 Apps Update - Semi-annual Channel Version 1908 for x64 based Edition (Build 11929.50000) 

| New Channel name | Previous Channel name |
| --- | --- |
| Semi-Annual Enterprise Channel | Semi-Annual Channel |
| Semi-Annual Enterprise Channel (Preview) | Semi-Annual Channel (Targeted) |
| Monthly Enterprise Channel | NA |
| Current Channel | Monthly Channel |
| Current Channel (Preview) | Monthly Channel (Targeted) |
| Beta Channel | Insider |

For more information about how to modify your automatic deployment rules, see [Automatically deploy software updates](../../../sum/deploy-use/automatically-deploy-software-updates). For more information about the name change, see [Name change for Office 365 ProPlus](/en-us/deployoffice/name-change).

## Report setup and upgrade failures to Microsoft

If the setup or update process fails to complete successfully, you can now report the error directly to Microsoft. If a failure occurs, the **Report update error to Microsoft** button is enabled. When you use the button, an interactive wizard opens allowing you to provide more information to us. In technical previews, this button is always enabled even when the setup completes successfully.

When running setup from the media rather than the console, you'll also be given the **Report update error to Microsoft** option if setup fails.

[![Report update error to Microsoft button in the ribbon](media/5622909-report-error.png)](media/5622909-report-error.png#lightbox)

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to **Administration** &gt; **Overview** &gt; **Updates and Servicing**.
2. Select an update then click **Report update error to Microsoft** in the ribbon.
3. Before you submit the feedback, you'll be given options to:
    - Attach additional files
    - Provide your email address if you're willing to be contacted about the error.
4. When you submit feedback, you'll be given a transaction ID for the feedback. A status message is also generated with this information.
    - Message ID 53900 is a successful submission.
    - Message ID 53901 is a failed submission.

## Notification for Microsoft Entra app secret key expiration

Based on your feedback, if you [Configure Azure services](../../servers/deploy/configure/azure-services-wizard) to cloud-attach your site, the Configuration Manager console now displays notifications for the following circumstances:

- One or more Microsoft Entra app secret keys will expire soon
- One or more Microsoft Entra app secret keys have expired

To mitigate both cases, use the in-console action to [Renew secret the key](../../servers/deploy/configure/azure-services-wizard#bkmk_renew).

### Known issue: Console may unexpectedly close

If you configure your site with a connection to the **Cloud Management** Azure service, this notification can cause the console to unexpectedly close. You use this Azure service for a variety of features, including the cloud management gateway (CMG) and Microsoft Entra discovery. For more information, see [Configure Azure services for use with Configuration Manager](../../servers/deploy/configure/azure-services-wizard#available-services).

By default, the site evaluates the state of this alert once per hour. To work around this issue, restart the console.

## Improvements to BitLocker task sequence steps

Based on your feedback, you can now specify the **Disk encryption mode** on the [Enable BitLocker](../../../osd/understand/task-sequence-steps#enable-bitlocker) and [Pre-provision BitLocker](../../../osd/understand/task-sequence-steps#BKMK_PreProvisionBitLocker) task sequence steps. By default, the steps continue to use the default encryption method for the OS version. Use the new setting to select one of the following encryption algorithms: AES\_128, AES\_256, XTS\_AES256, or XTS\_AES128.

If the step runs on a version of Windows that doesn't support the specified algorithm, it falls back to the OS default. In this circumstance, the task sequence engine sends status message 11911.

If you use the following PowerShell cmdlets to configure these task sequence steps, use the new **EncryptionMethod** parameter:

- [Set-CMTSStepEnableBitLocker](/en-us/powershell/module/configurationmanager/Set-CMTSStepEnableBitLocker)
- [New-CMTSStepEnableBitLocker](/en-us/powershell/module/configurationmanager/New-CMTSStepEnableBitLocker)
- [Set-CMTSStepOfflineEnableBitLocker](/en-us/powershell/module/configurationmanager/Set-CMTSStepOfflineEnableBitLocker)
- [New-CMTSStepOfflineEnableBitLocker](/en-us/powershell/module/configurationmanager/New-CMTSStepOfflineEnableBitLocker)

The **Enable BitLocker** step also now includes the setting to **Skip this step for computers that do not have a TPM or when TPM is not enabled**. By default, this setting is disabled. The step fails on a device without a TPM or a TPM that doesn't initialize. If you enable this setting, and the device doesn't have a functional TPM, the task sequence engine logs a warning to smsts.log and sends status message 11912.

Tip

This setting already exists on the Pre-provision BitLocker step. It can now also generate status message 11912 when necessary.

## Improvements to the content library cleanup tool

If you remove content from a distribution point while the site system is offline, an orphaned record can exist in WMI. Over time, this behavior can eventually lead to a warning status on the distribution point. To mitigate the issue in the past, you had to manually remove the orphaned entries from WMI. Making a mistake during this process could cause more severe issues with the server.

The content library cleanup tool in delete mode could remove orphaned files from the content library. It can now also remove orphaned content records from the WMI provider on a distribution point. Run the tool with the `/delete` parameter for both use cases.

For more information, see the [Content library cleanup tool](../../plan-design/hierarchy/content-library-cleanup-tool).

## Remove command prompt during Windows 10 in-place upgrade

During a task sequence to upgrade a device to Windows 10, during one of the final Windows configuration phases a command prompt window opens. The window is on top of the Windows out-of-box experience (OOBE), and users can interact with it to disrupt the upgrade process.

Starting in this release, the SetupCompleteTemplate.cmd and SetupRollbackTemplate.cmd scripts from Configuration Manager include a change to hide the command prompt window.