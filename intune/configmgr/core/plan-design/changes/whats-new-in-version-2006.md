---
layout: Conceptual
title: What's new in version 2006 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2006
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
description: Get details about changes and new capabilities introduced in version 2006 of Configuration Manager current branch.
ms.date: 2020-11-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 93b3ac18-508b-783a-2e3a-af3e90c133e6
document_version_independent_id: c4892fa3-74fa-af3d-f70d-594193ed7b1f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2006.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2006
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2006.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7ddd0ba-08b8-4055-8ab8-0da61f3dfbb3
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
platformId: 2616ff08-aac5-0d78-4912-c20ebde2afda
---

# What's new in version 2006 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2006 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 1810 or later. This article summarizes the changes and new features in Configuration Manager, version 2006.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2006](../../servers/manage/checklist-for-installing-update-2006). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2006#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Microsoft Intune tenant attach

### Scripts from the admin center

Bring the power of the Configuration Manager on-premises [Run scripts](../../../apps/deploy-use/create-deploy-scripts) feature to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to run PowerShell scripts from the cloud against an individual Configuration Manager managed device in real time. This gives all the traditional benefits of PowerShell scripts that have already been defined and approved by the Configuration Manager admin to this new environment. For more information, see [Tenant attach: Scripts from the admin center](../../../tenant-attach/scripts).

### Device timeline in the admin center

When Configuration Manager synchronizes a device to Microsoft Intune through tenant attach, you'll be able to see a timeline of events. This timeline shows past activity on the device that can help you troubleshoot problems. For more information, see [Tenant attach: Device timeline in the admin center](../../../tenant-attach/timeline).

### Resource explorer in the admin center

From the Microsoft Endpoint Management admin center, you can view hardware inventory for uploaded Configuration Manager devices by using resource explorer. For more information, see [Tenant attach: Resource explorer in the admin center](../../../tenant-attach/resource-explorer).

### CMPivot from the admin center

Bring the power of CMPivot to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to be able to initiate real-time queries from the cloud against an individual ConfigMgr managed device and return the results back to the admin center. This gives all the traditional benefits of CMPivot, which allows IT Admins and other designated personas the ability to quickly assess the state of devices in their environment and take action.

For more information about CMPivot from the admin center, see [Tenant attach: Launch CMPivot from the admin center](../../../tenant-attach/cmpivot-start), [CMPivot overview](../../../tenant-attach/cmpivot-overview-attached), and [CMPivot sample scripts](../../../tenant-attach/cmpivot-samples-attached).

### Microsoft Defender Antivirus policies in the Microsoft Intune admin center

You can now create Microsoft Defender antivirus policies in the Microsoft Intune admin center and deploy them to Configuration Manager collections. For more information including detailed instructions and available settings, see the following articles:

- [Tenant attach: Onboard Configuration Manager clients to Microsoft Defender for Endpoint from the admin center (preview)](../../../tenant-attach/atp-onboard)
- [Tenant attach: Deploy endpoint security Antivirus policy from the admin center (preview)](../../../tenant-attach/deploy-antivirus-policy)
- [Settings for Microsoft Defender Antivirus policy for tenant attached devices in Microsoft Intune](../../../../device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json).
- [Settings for Windows Security experience Antivirus policy for tenant attached devices](../../../../device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json)

### Install applications from the admin center

You can initiate an application install in real time for a tenant attached device from the Microsoft Intune admin center. Starting with Configuration Manager version 2006, the list of applications available for the device also includes applications deployed to the device's currently logged on user. For more information, see [Tenant attach: Install an application from the admin center](../../../tenant-attach/applications).

### Import previously created Azure AD application during tenant attach onboarding

During a new onboarding, an administrator can specify a previously created application during onboarding to tenant attach. For more information, see [Microsoft Intune tenant attach: Device sync and device actions](../../../tenant-attach/device-sync-actions#bkmk_aad_app).

## Endpoint analytics

### Endpoint analytics data collection enabled by default

The **Enable Endpoint analytics data collection** client setting is now enabled by default. This setting allows your managed endpoints to send data, such as startup performance insights, to your Configuration Manager site server. This change affects local data collection only. Endpoint analytics data isn't uploaded to the Microsoft Intune admin center until you [enable data upload in Configuration Manager](../../../../endpoint-analytics/configure?pivots=cm). The new default value applies to the default client settings and any custom client settings created after upgrading to version 2006.

- If you're upgrading from version 2002 to version 2006, existing custom client settings values are retained. The default value for **Enable Endpoint analytics data collection** in Configuration Manager version 2002 is **No**.
- If you're upgrading to version 2006 from Configuration Manager version 1910 or prior, any pre-existing custom client settings that contain the **Computer Agent** group of settings inherits the new default of **Yes** for **Enable Endpoint analytics data collection**.

For more information, see [Configure Endpoint analytics data collection in Configuration Manager](../../../../endpoint-analytics/configure?pivots=cm).

## Site infrastructure

### VPN boundary type

To simplify managing remote clients, you can now create a new boundary type for VPNs. Previously, you had to create boundaries for VPN clients based on the IP address or subnet. This configuration could be challenging or not possible because of the subnet configuration or the VPN design.

Now when a client sends a location request, it includes additional information about its network configuration. Based on this information, the server determines whether the client is on a VPN.

For more information, see [Define boundaries](../../servers/deploy/configure/boundaries).

### Management insights to optimize for remote workers

This release adds a new group of management insights, **Optimize for remote workers**. These insights help you create better experiences for remote workers and reduce load on your infrastructure. The insights in this release primarily focus on VPN:

- **Define VPN boundary groups**
- **Configure VPN connected clients to prefer cloud based content sources**
- **Disable peer to peer content sharing for VPN connected clients**

For more information, see [Management insights](../../servers/manage/management-insights).

### Improved support for Azure Virtual Desktop

The **Windows 10 Enterprise multi-session** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists.

For more information on Configuration Manager's support for Azure Virtual Desktop, see [Supported OS versions for clients and devices](../configs/supported-operating-systems-for-clients-and-devices#azure-virtual-desktop).

### Intranet clients can use a CMG software update point

Intranet clients can now access a CMG software update point when it's assigned to a boundary group. For more information, see [Configure boundary groups](../../servers/deploy/configure/boundary-groups-software-update-points#intranet-clients-can-use-a-cmg-software-update-point).

## Cloud-attached management

### Use the Company Portal app on co-managed devices

The Company Portal app is now the cross-platform app portal experience for the Microsoft Intune family of products. By configuring co-managed devices to also use the Company Portal app, you can provide a consistent user experience on all devices.

For more information, see [Use the Company Portal app on co-managed devices](../../../comanage/company-portal).

### Use Microsoft Azure China 21Vianet for co-management

You can now select the Azure China Cloud as your Azure environment when enabling co-management. For more information, see [How to enable co-management](../../../comanage/how-to-enable).

### Notification for Azure AD app secret key expiration

If you configure Azure services to cloud-attach your site, the Configuration Manager console now displays notifications for the following circumstances:

- One or more Azure AD app secret keys will expire soon
- One or more Azure AD app secret keys have expired

For more information, see [Renew secret key](../../servers/deploy/configure/azure-services-wizard#bkmk_renew).

### Desktop Analytics

For more information on the monthly changes to the Desktop Analytics cloud service, see [What's new in Desktop Analytics](../../../../device-updates/windows/monitor-compatibility).

#### Change to diagnostic data labels

To better align with the Desktop Analytics requirements for Windows diagnostic data, these settings have new labels:

| Version 2006 and later | Version 2002 and earlier |
| --- | --- |
| Required | Basic |
| Optional (limited) | Enhanced (Limited) |
| N/A | Enhanced |
| Optional | Full |

If you previously configured any devices at the **Enhanced** level, when you upgrade to version 2006, they'll revert to **Optional (limited)**. They will then send less data to Microsoft. This change shouldn't impact what you see in Desktop Analytics.

For more information, see [Enable data sharing for Desktop Analytics](../../../../device-updates/windows/monitor-compatibility).

## Real-time management

### Improvements to CMPivot

The following improvements have been made in CMPivot:

- CMPivot from the console and CMPivot standalone have been converged
- Run CMPivot from an individual device or multiple devices without having to select or create a collection
- From CMPivot query results, you can select an individual device or multiple devices then launch a separate CMPivot instance scoped to your selection.

For more information, see [CMPivot starting in version 2006](../../servers/manage/cmpivot-changes#bkmk_2006).

## Client management

### Install and upgrade the client on a metered connection

Previously, if the device was connected to a metered network, new clients wouldn't install. Existing clients only upgraded if you allowed all client communication. For devices that are frequently roaming on a metered network, they would be unmanaged or on an older client version. Starting in this release, you can install and upgrade the client when you set the client setting **Client communication on metered internet connections** to **Allow** or **Limit**. With this setting, you can allow the client to stay current, but still manage the client communication on a metered network.

To define the behavior for a new client installation, there's a new ccmsetup parameter **/AllowMetered**. When you allow client communication on a metered network for ccmsetup, it downloads the content, registers with the site, and downloads the initial policy. Any further client communication follows the configuration of the client setting from that policy.

For more information, see the following articles:

- [About client settings](../../clients/deploy/about-client-settings#client-communication-on-metered-internet-connections)
- [About client installation parameters and properties](../../clients/deploy/about-client-installation-properties#allowmetered)

### Improvements to managing device restarts

Configuration Manager provides many options to manage device restarts and restart notifications. You can now configure a client setting to prevent devices from automatically restarting when a deployment requires it. This setting gives you more control in unique situations. By default, the client setting **Configuration Manager can force a device to restart** is enabled, so Configuration Manager can still force devices to restart. This setting only applies to application, software update, and package deployments that require a restart.

For more information, see [device restart notifications](../../clients/deploy/device-restart-notifications).

## Application management

### Improvements to available apps via CMG

This release fixes an issue with Software Center and Azure Active Directory (Azure AD) authentication. For a client detected as on the intranet but communicating via the cloud management gateway (CMG), previously Software Center would use Windows authentication. When it tried to get the list of user-available apps, it would fail. It now uses Azure Active Directory (Azure AD) identity for devices joined to Azure AD. These devices can be cloud-joined or hybrid-joined.

For more information, see [Prerequisites to deploy user-available apps](../../../apps/plan-design/prerequisites-deploy-user-available-apps).

### Microsoft 365 Apps for enterprise

Office 365 ProPlus was renamed to Microsoft 365 Apps for enterprise on April 21, 2020. Starting in version 2006, the following changes have been made:

- The Configuration Manager console has been updated to use the new name.
    - This change also includes update channel names for Microsoft 365 Apps.
- A banner notification was added to the console to notify you if one or more automatic deployment rules reference obsolete channel names in the **Title** criteria for Microsoft 365 Apps updates.

For more information, see [Microsoft 365 Apps channel names](../../../sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) and [Microsoft 365 Apps readiness dashboard](../../../sum/deploy-use/office-365-dashboard#bkmk_readiness-dash).

## OS deployment

### Task sequence media support for cloud-based content

Task sequence media can now download cloud-based content. For example, you send a USB key to a user at a remote office to reimage their device. Or an office that has a local PXE server, but you want devices to prioritize cloud services as much as possible. Instead of further taxing the WAN to download large OS deployment content, boot media and PXE deployments can now get content from cloud-based sources. For example, a cloud management gateway (CMG) that you enable to share content.

Note

The device still needs an intranet connection to the management point.

For more information, see [Bootable media support for cloud-based content](../../../osd/deploy-use/deploy-task-sequence-over-internet#bootable-media-support-for-cloud-based-content).

### Improvements to task sequences via CMG

This release includes the following improvements to deploy task sequences to devices that communicate via a cloud management gateway (CMG):

- Support for OS deployment: With a task sequence that uses a boot image to deploy an OS, you can deploy it to a device that communicates via CMG. The user needs to start the task sequence from Software Center. For more information, see [Supported configurations for CMG](../../clients/manage/cmg/supported-configurations).
- This release fixes the two known issues from Configuration Manager current branch version 2002. You can now run a task sequence on a device that communicates via CMG in the following circumstances:

    - A workgroup device that you register with a [bulk registration token](../../clients/deploy/deploy-clients-cmg-token)
    - You configure the site for [Enhanced HTTP](../hierarchy/enhanced-http) and the management point is HTTP

### Improvements to BitLocker task sequence steps

You can now specify the disk encryption mode on the **Enable BitLocker** and **Pre-provision BitLocker** task sequence steps. By default, the steps continue to use the default encryption method for the OS version.

The **Enable BitLocker** step also now includes a setting to **Skip this step for computers that do not have a TPM or when TPM is not enabled**. When you enable this setting, the step logs an error on a device without a TPM or a TPM that doesn't initialize, and the task sequence continues. This setting makes it easier to manage the task sequence behavior on devices that can't fully support BitLocker.

For more information, see [Task sequence steps](../../../osd/understand/task-sequence-steps).

### Management insight rules for OS deployment

When the size of the task sequence policy exceeds 32 MB, the client fails to process the large policy. The client then fails to run the task sequence deployment. To help you manage the policy size of task sequences, this release includes the following management insights:

- **Large task sequences may contribute to exceeding maximum policy size**
- **Total policy size for task sequences exceeds policy limit**

Tip

These rules are in a new group for **Operating System Deployment**. The existing rule for **Unused boot images** is now in this group too.

For more information, see [management insight](../../servers/manage/management-insights#operating-system-deployment).

### Improvements to OS deployment

This release includes the following additional improvements to OS deployment:

- Use a task sequence variable to specify the target of the [Format and Partition Disk](../../../osd/understand/task-sequence-steps#BKMK_FormatandPartitionDisk) step. This new variable option supports more complex task sequences with dynamic behaviors. For example, a custom script can detect the disk and set the variable based on the hardware type. Then you can use multiple instances of this step to configure different hardware types and partitions.
- The [Check Readiness](../../../osd/understand/task-sequence-steps#BKMK_CheckReadiness) step now includes a check to determine if the device uses UEFI. It also includes a new read-only task sequence variable, **\_TS\_CRUEFI**.
- If you enable the [task sequence progress window](../../../osd/understand/user-experience#task-sequence-progress) to show more detailed progress information, it now doesn't count enabled steps in a disabled group. This change helps make the progress estimate more precise.
- Previously, during a task sequence to upgrade a device to Windows 10, a command prompt window opened during one of the final Windows configuration phases. The window was on top of the Windows out-of-box experience (OOBE), and users could interact with it to disrupt the upgrade process. Now the SetupCompleteTemplate.cmd and SetupRollbackTemplate.cmd scripts from Configuration Manager include a change to hide this command prompt window.
- Some customers build custom task sequence interfaces using the **IProgressUI::ShowMessage** method, but it doesn't return a value for the user's response. This release adds the [IProgressUI::ShowMessageEx](../../../develop/reference/core/clients/client-classes/iprogressui--showmessageex-method) method. This new method is similar to the existing method, but also includes a new integer result variable, **pResult**.

## Protection

### CMG support for endpoint protection policies

While the cloud management gateway (CMG) has supported endpoint protection policies, devices required access to on-premises domain controllers. Starting in this release, clients that communicate via a CMG can immediately apply endpoint protection policies without an active connection to Active Directory.

For more information, see [Supported configurations for CMG](../../clients/manage/cmg/supported-configurations).

### BitLocker management support for hierarchies

You can now install the BitLocker self-service portal and the administration and monitoring website at the central administration site.

For more information, see [Set up BitLocker portals](../../../protect/deploy-use/bitlocker/setup-websites).

## Configuration Manager console

### Community hub and GitHub

*(First introduced in June 2020)*

The IT admin community has developed a wealth of knowledge over the years. Rather than reinventing items like scripts and reports from scratch, we've built a Configuration Manager **Community hub** where you can share with each other. By leveraging the work of others, you can save hours of work. The Community hub fosters creativity by building on others' work and having other people build on yours. GitHub already has industry-wide processes and tools built for sharing. Now, the Community hub will leverage those tools directly in the Configuration Manager console as foundational pieces for driving this new community. For the initial release, the content made available in the Community hub will be uploaded only by Microsoft.

For more information, see [Community hub and GitHub](../../servers/manage/community-hub).

### Direct links to Community hub items

You can easily navigate to and reference items in the Configuration Manager console Community hub node with a direct link. For more information, see [Direct links to Community hub items](../../servers/manage/community-hub#bkmk_deeplink).

### Notifications from Microsoft

You can now choose to receive notifications from Microsoft in the Configuration Manager console. These notifications help you stay informed about new or updated features, changes to Configuration Manager and attached services, and issues that require action to remediate.

For more information, see [Configure a site to receive messages from Microsoft](../../servers/manage/admin-console-notifications#bkmk_msft).

### Power BI sample reports

*(First introduced in June 2020)*

When you integrate Power BI Report Server with Configuration Manager reporting, there are now sample Power BI reports available. Download and install the following sample reports:

- Software Update Compliance Status
- Software Update Deployment Status

For more information, see [Install Power BI sample reports](../../servers/manage/powerbi-sample-reports).

## Deprecated operating systems

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

As first announced in version 1906, version 2006 drops support for the following client OS versions:

- Windows CE 7.0
- Windows 10 Mobile
- Windows 10 Mobile Enterprise

## Other updates

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [PowerShell version 2006 release notes](/en-us/powershell/sccm/2006-release-notes).

For more information on changes to the administration service REST API, see [Administration service release notes](../../../develop/adminservice/release-notes#bkmk_2006).

Aside from new features, this release also includes additional changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 2006](https://support.microsoft.com/help/4578830).

The following revised update rollup (4575789) is available in the console starting on November 30, 2020: [Revised update rollup for Microsoft Endpoint Configuration Manager current branch, version 2006](https://support.microsoft.com/help/4575789).

Note this revision supersedes the original release of KB 4578605 [Update rollup for Microsoft Configuration Manager version 2006](https://support.microsoft.com/help/4578605).

### Hotfixes

The following additional hotfixes are available to address specific issues:

| ID | Title | Date | In-console |
| --- | --- | --- | --- |
| [4580678](https://support.microsoft.com/help/4580678) | Tenant attach rollup for Configuration Manager current branch, version 2006 | September 18, 2020 | Yes |
| [4584759](https://support.microsoft.com/help/4584759) | Clients report Desktop Analytics configuration errors in Configuration Manager, version 2006 | October 2, 2020 | Yes |
| [4575786](https://support.microsoft.com/help/4575786) | Configuration Manager console terminates unexpectedly on Configuration Manager current branch, version 2006 | November 12, 2020 | Yes |
| [4575787](https://support.microsoft.com/help/4575787) | Co-management enrollment takes longer than expected for Configuration Manager clients | November 12, 2020 | No |
| [4575785](https://support.microsoft.com/help/4575785) | November 2020 Update for Asset Intelligence authentication certificate in Configuration Manager | November 18, 2020 | No |
| [4575790](https://support.microsoft.com/help/4575790) | Client setup is unable to download contents from a cloud distribution point in Configuration Manager current branch, version 2006 | November 20, 2020 | Yes |