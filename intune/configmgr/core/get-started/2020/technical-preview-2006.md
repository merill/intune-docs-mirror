---
layout: Conceptual
title: Technical preview 2006 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2006
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2006.
ms.date: 2020-06-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 1b7795f5-f20b-b7be-bd19-f70bcabf9c6c
document_version_independent_id: d24965b2-04dd-3451-6f4c-65e6e2062aed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2006.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2006
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2006.md
platformId: 0f4af452-207d-0d50-8791-9f6f85f9ed59
---

# Technical preview 2006 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2006. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Use the Company Portal app on co-managed devices

The Company Portal app is now the cross-platform app portal experience for the Microsoft Intune family of products. You can now use a preview version of the Company Portal app on co-managed devices. By configuring co-managed devices to also use the Company Portal, you can provide a consistent user experience on all devices.

This preview version of the Company Portal supports the following actions:

- Launch the Company Portal app on co-managed devices and sign in with Microsoft Entra single sign-on (SSO).
- View available and installed Configuration Manager apps in the Company Portal alongside Intune apps.
- Install available Configuration Manager apps from the Company Portal and receive installation status information.

![Company Portal with app from Configuration Manager](media/3601237-company-portal.png)

The behavior of the Company Portal depends upon your co-management workload configuration:

| Workload | Setting | Behavior |
| --- | --- | --- |
| Client apps | **Configuration Manager** | You can see only Configuration Manager client apps |
| Client apps | **Pilot Intune** or **Intune** | You can see both Configuration Manager and Intune client apps |
| Office Click-to-run apps | **Configuration Manager** | You can see only Configuration Manager Office click-to-run apps |
| Office Click-to-run apps | **Pilot Intune** or **Intune** | You can see only Intune Office click-to-run apps |

For more information, see [How to switch Configuration Manager workloads to Intune](../../../comanage/how-to-switch-workloads).

### Prerequisites for Company Portal preview

- Company Portal app version 11.0.8980.0 or later
- Windows 10, version 1803 or later:

    - Enrolled to [co-management](../../../comanage/how-to-enable)
    - Access to [internet endpoints for Intune](../../../../fundamentals/endpoints)
- The user accounts that sign in to these devices require the following configurations:

    - A Microsoft Entra identity
    - Assigned an Intune license

## Improvements to available apps via CMG

An internet-based, domain-joined device that isn't joined to Microsoft Entra ID and communicates via a cloud management gateway (CMG) can now get apps deployed as available. The Active Directory domain user of the device needs a matching Microsoft Entra identity. When the user starts Software Center, Windows prompts them to enter their Microsoft Entra credentials. They can then see any available apps.

Configure the following prerequisites to enable this functionality:

- Windows 10 device

    - Joined to your on-premises Active Directory domain
    - Communicate via CMG
- The site has discovered the user by both [Active Directory](../../servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) and [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc)

## Intranet clients can use a CMG software update point

Intranet clients can now access a CMG software update point when it's assigned to the boundary group. Admins can allow intranet devices to scan against a CMG software update point in the following scenarios:

- When an internet machine connects to the VPN, it will continue scanning against the CMG software update point over the internet.
- If the only software update point for the boundary group is the CMG software update point, then all intranet and internet devices will scan against it.

## Improvements to task sequences via CMG

This release includes the following improvements to deploy task sequences to devices that communicate via a cloud management gateway (CMG):

- Support for OS deployment: With a task sequence that uses a boot image to deploy an OS, you can deploy it to a device that communicates via CMG. The user needs to start the task sequence from Software Center.
- This release fixes the two known issues from Configuration Manager current branch version 2002. You can now run a task sequence on a device that communicates via CMG in the following circumstances:

    - A workgroup device that you register with a [bulk registration token](../../clients/deploy/deploy-clients-cmg-token)
    - You configure the site for [Enhanced HTTP](../../plan-design/hierarchy/enhanced-http) and the management point is HTTP

### Known issue with OS deployment via CMG

If there's an **Install Application** step in an OS deployment task sequence to a client via CMG, it fails to download the app policy. To work around this issue, disable this step in the task sequence. Deploy the app separately from the task sequence.

## Management insights to optimize for remote workers

This release adds a new group of [management insights](../../servers/manage/management-insights), **Optimize for remote workers**. These insights help you create better experiences for remote workers and reduce load on your infrastructure. The insights in this release primarily focus on VPN:

- **Define VPN boundary groups**: Create a VPN boundary and associate it to a boundary group. Associate VPN-specific site systems to the group, and configure the settings for your environment. This insight checks for at least one boundary group with at least one VPN boundary in it. From the properties of this insight, select **Review Actions** to go to the **Boundary Groups** node. For more information, see [VPN boundary type](technical-preview-2005#bkmk_vpn).
- **Configure VPN connected clients to prefer cloud based content sources**: To reduce traffic on the VPN, enable the boundary group option to **Prefer cloud based sources over on-premises sources**. This option allows clients to download content from the internet instead of distribution points across the VPN. For more information, see [Boundary group options](../../servers/deploy/configure/boundary-group-options).
- **Disable peer to peer content sharing for VPN connected clients**: To prevent unnecessary peer-to-peer traffic that likely doesn't benefit the remote clients, disable the boundary group option to **Allow peer downloads in this boundary group**. For more information, see [Boundary group options](../../servers/deploy/configure/boundary-group-options).

## Improvements to VPN boundary type

This release improves upon the new VPN boundary type first introduced in [technical preview version 2005](technical-preview-2005#bkmk_vpn). You can now create more than one VPN boundary, and can detect the connection by the VPN name or description. When you open the **Create Boundary** page, and select the **VPN** type, choose one of the following options:

- **Auto detect VPN**: This option is the same behavior as before. The boundary value in the console list will be `AUT:1`. It should detect any VPN solution that uses the point-to-point tunneling protocol (PPTP). If it doesn't detect your VPN, use one of the other options.
- **Connection name**: Specify the name of the VPN connection on the device. It's the name of the network adapter in Windows for the VPN connection. Configuration Manager matches the first 251 characters of the string, but doesn't support wildcard characters or partial strings. The boundary value in the console list will be `NAM:<name>`, where `<name>` is the connection name that you specify.

    For example, you run the `ipconfig` command on the device, and one of the sections starts with: `PPP adapter ContosoVPN:`. Use the string `ContosoVPN` as the **Connection name**. It displays in the list as `NAM:ContosoVPN`.
- **Connection description**: Specify the description of the VPN connection. Configuration Manager matches the first 251 characters of the string, but doesn't support wildcard characters or partial strings. The boundary value in the console list will be `DES:<description>`, where `<description>` is the connection description that you specify.

    For example, you run the `ipconfig /all` command on the device, and one of the connections includes the following line: `Description . . . . . . . . . . . : ContosoMainVPN`. Use the string `ContosoMainVPN` as the **Connection description**. It displays in the list as `DES:ContosoMainVPN`.

In every case, the device needs to be connected to the VPN for Configuration Manager to associate the client in that boundary.

## Tenant Attach: Improvements to Configuration Manager actions in Microsoft Intune admin center

This release introduces some improvements to the administration of Configuration Manager devices in Microsoft Intune admin center. Improvements include:

- Configuration errors now include links to documentation to help you troubleshoot.
- User available applications now appear in the **Applications** node for a ConfigMgr device.

    - The application list includes applications deployed to a user currently logged on to the device.
    - Multi-user session scenarios aren't supported.
    - Microsoft Entra joined devices aren't currently supported, only AD joined devices.

To deploy an application to a user, install the latest version of the Configuration Manager client, then follow the instructions in [Tenant attach: Install an application from the admin center](technical-preview-2005#bkmk_apps).

## CMG support for endpoint protection policies

While the cloud management gateway (CMG) [supported endpoint protection policies](../../clients/manage/cmg/supported-configurations#bkmk_note1), devices required access to on-premises domain controllers. From this release, clients that communicate via a CMG can immediately apply endpoint protection policies without an active connection to Active Directory.

## Import previously created Microsoft Entra application during tenant attach onboarding

During a new onboarding, an administrator can specify a previously created application during onboarding to tenant attach. From the **Tenant onboarding** page in the **Co-management Configuration Wizard**, select **Optionally import a separate web app to synchronize Configuration Manager client data to Microsoft Endpoint Manager admin center**. This option will prompt you to specify the following information for your Microsoft Entra app:

- Microsoft Entra tenant name
- Microsoft Entra tenant ID
- Application name
- Client ID
- Secret key
- Secret key expiry
- App ID URI

## Improvements to client upgrade on a metered connection

Starting in Configuration Manager technical preview version 2005, you could install and upgrade the client when you allowed client communication on a metered connection. You can now also configure the client setting **Client communication on metered internet connections** to **Limit**. This option reduces the client communication on a metered network, but now still allows the client to stay current.

For more information, see the following articles:

- [Technical preview 2005: Install and upgrade the client on a metered connection](technical-preview-2005#bkmk_meter)
- [About client settings: Client communication on metered internet connections](../../clients/deploy/about-client-settings#client-communication-on-metered-internet-connections)

## Improvements to managing device restarts

Configuration Manager provides many options to manage [device restart notifications](../../clients/deploy/device-restart-notifications). Based on your feedback, you can now configure client settings to prevent devices from automatically restarting when a deployment requires it. By default, Configuration Manager can still force devices to restart.

Important

This new client setting applies to all application, software update, and package deployments to the device. Until a user manually restarts the device:

- Software updates and app revisions may not be fully installed
- Additional software installs may not happen

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. In the **Computer Restart** group of client settings, disable the following new option: **Configuration Manager can force a device to restart**. When you disable this setting, you can't specify the amounts of time after the deadline that the device is restarted or the user is presented a final countdown notification.
2. For the purposes of testing the behavior, change the frequency of the following setting to `2` minutes: **After the deadline, specify the frequency of restart reminder notifications to the user (minutes)**.
3. [Deploy an app](../../../apps/deploy-use/deploy-applications) that requires a restart. Make the deployment required with an immediate deadline.

    Tip

    For the purposes of testing, on the app deployment type properties, go to the **Return Codes** tab. For return code value `0`, change the **Code Type** to **Hard Reboot**.

Wait or force the client to receive the updated client settings and app deployment policies. After the app installs successfully, you'll see the following notification:

![Software Center notification to restart your computer](media/3601213-restart-your-computer.png)

If you **Snooze** this notification, it will show again based on how you configure the frequency of restart reminder notifications. The device won't restart until you select **Restart** or manually restart Windows.

To help troubleshoot, use the rebootcoordinator.log and SCNotify.log files.

## Improved support for Windows Virtual Desktop

The **Windows 10 Enterprise multi-session** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists.

For more information on Configuration Manager's support for Windows Virtual Desktop, see [Supported OS versions for clients and devices](../../plan-design/configs/supported-operating-systems-for-clients-and-devices#azure-virtual-desktop).

Note

If you previously selected the top-level **Windows 10** platform, this action automatically selected all child platforms. This new platform isn't automatically selected. If you want to add **Windows 10 Enterprise multi-session**, manually select it in the list.

### Known issue with new OS platform

On a task sequence or package, when you select the **Windows 10 Enterprise multi-session** platform, after you save it reverts to **All Windows 10 x64**.

To work around this issue, run the following SQL script on the site database:

```sql
Update SupportedPlatforms
Set OSMaxVersion = '10.00.99999.9997'
Where DisplayText like '%multi%'
```

## Direct links to Configuration Manager Community hub items

You can now easily navigate to and reference items in the Configuration Manager console Community hub node with a direct link. The intention for this feature is for easier collaboration and being able to share links to Community hub items with your colleagues. Currently, you'll see these links shared by the Configuration Manager team and in the documentation.

## General known issues

### Microsoft Entra authentication doesn't work

Configuration Manager's use of the Microsoft Entra security token service doesn't work. The **CCM\_STS.log** on the management point contains an entry similar to the following error: `ProcessRequest - Exception: System.IO.FileLoadException: Could not load file or assembly 'System.IdentityModel.Tokens.JWT.` It also includes the HRESULT 0x80131040.

Another symptom is issues with a cloud management gateway (CMG). If you run the CMG connection analyzer, it fails testing the CMG channel for management point with the following error: `Failed to get ConfigMgr token with Azure AD token. Status code is '500' and status description is 'CMGConnector_InternalServerError'.`

This issue is because of a version discrepancy with a supporting library.

To work around the issue, copy **System.IdentityModel.Tokens.JWT.dll** from the \bin\X64 folder of the installation directory on the site server to the SMS\_CCM\CCM\_STS\bin folder on the management point.