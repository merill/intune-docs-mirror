---
layout: Conceptual
title: What's new in version 1810 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-1810
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
description: Get details about changes and new capabilities introduced in version 1810 of Configuration Manager current branch.
ms.date: 2020-07-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 17b302a5-5d14-92af-bee0-06ad08c59075
document_version_independent_id: 62a92503-8532-ea6e-caa2-3adb7ac2817e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-1810.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-1810
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-1810.md
platformId: a25e1baa-c501-17bb-ace3-4b2e5572d8c1
---

# What's new in version 1810 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 1810 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 1710, 1802, or 1806.  This article summarizes the changes and new features in Configuration Manager, version 1810.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 1810](../../servers/manage/checklist-for-installing-update-1810). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-1810#post-update-checklist).

To take advantage of new Configuration Manager features, first update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Deprecated features and operating systems

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

Starting on August 14, 2018, the hybrid mobile device management feature is deprecated. For more information, see [What happened to hybrid MDM](../../../mdm/understand/what-happened-to-hybrid).

Support for System Center Endpoint Protection (SCEP) for Mac and Linux (all versions) ends on December 31, 2018. Availability of new virus definitions for SCEP for Mac and SCEP for Linux may be discontinued after the end of support. For more information, see [End of support blog post](https://techcommunity.microsoft.com/t5/configuration-manager-blog/end-of-support-for-scep-for-mac-and-scep-for-linux-on-december/ba-p/286257).

Classic service deployments in Azure are now deprecated in Configuration Manager. Start using Azure Resource Manager deployments for the cloud management gateway and the cloud distribution point. For more information, see [Plan for CMG](../../clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager).

## Site infrastructure

### Support for Windows Server 2019

Configuration Manager now supports Windows Server 2019 and Windows Server, version 1809, as site systems.

For more information, see [Supported operating systems for site system servers](../configs/supported-operating-systems-for-site-system-servers).

### Hierarchy support for site server high availability

Central administration sites and child primary sites can now have an additional site server in passive mode.

For more information, see [Site server high availability](../../servers/deploy/configure/site-server-high-availability).

### Improvements to setup prerequisites

When you install or update to version 1810, Configuration Manager setup now includes or improves the following prerequisite checks:

- **Pending system restart**: This prerequisite check is now more resilient. It checks additional registry keys for Windows features. For more information, see [Pending system restart](../../servers/deploy/install/list-of-prerequisite-checks#pending-system-restart).
- **SQL Server change tracking cleanup**: A new check if the site database has a backlog of SQL Server change tracking data. For more information, including a procedure to verify and clear this backlog, see [SQL Server change tracking cleanup](../../servers/deploy/install/list-of-prerequisite-checks#bkmk_changetracking).
- **SQL Server Native Client version**: This prerequisite check is updated for versions of SQL Server Native Client that support TLS 1.2. The minimum version is [SQL Server 2012 SP4](https://www.microsoft.com/download/details.aspx?id=50402). For more information, see [SQL Server Native Client version](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).
- **Site system on Windows cluster node**: The Configuration Manager setup process no longer blocks installation of the site server role on a computer with the Windows role for Failover Clustering. SQL Server Always On availability groups require this role, so previously you couldn't colocate the site database on the site server. With this change, you can create a highly available site with fewer servers by using an availability group and a site server in passive mode. For more information, see [Windows Failover Cluster](../../servers/deploy/install/list-of-prerequisite-checks#windows-failover-cluster).

### New permission for client notification actions

Client notification actions now require the **Notify Resource** permission on the SMS\_Collection class. The following built-in roles have this permission by default:

- Full Administrator
- Infrastructure Administrator

Add this permission to any custom roles that need to use client notification actions.

For more information, see [Client notifications](../../clients/manage/client-notification).

## Content management

### New boundary group options

Boundary groups now include the following additional settings to give you more control over content distribution in your environment:

- **Prefer distribution points over peers with the same subnet**: By default, the management point prioritizes peer cache sources at the top of the list of content locations. This setting reverses that priority for clients that are in the same subnet as the peer cache source.
- **Prefer cloud distribution points over distribution points**: If you have a branch office with a faster internet link, you can now prioritize cloud content.

For more information, see [Boundary group options for peer downloads](../../servers/deploy/configure/boundary-group-options).

### Management insights rule for peer cache source client version

The **Management Insights** node has a new rule to identify clients that serve as a peer cache source but haven't upgraded from a pre-1806 client version. The new rule is **Upgrade peer cache sources to the latest version of the Configuration Manager client**, and is part of the new **Proactive Maintenance** rule group. Pre-1806 clients can't be used as a peer cache source for clients that run version 1806 or later. Select **Take action** to open a device view that displays the list of clients.

For more information, see [Management insights](../../servers/manage/management-insights).

## Client management

### New client notification action to wake up device

You can now wake up clients from the Configuration Manager console, even if the client isn't on the same subnet as the site server. If you need to do maintenance or query devices, you're not limited by remote clients that are asleep. The site server uses the client notification channel to identify another client that's awake on the same remote subnet. The awake client then sends a wake on LAN request (magic packet).

For more information, see [Configure Wake on LAN](../../clients/deploy/configure-wake-on-lan) and [How to wake up clients](../../clients/deploy/plan/plan-wake-up-clients).

### New option to perform client notification from devices node

Up until 1810, the **Client Notification** option was only available from either the Device Collection node or when you viewed the membership of a Device Collection. It's now possible to perform a **Client Notification** from the **Devices** node directly. There's no longer a requirement to be within a collection membership view.

For more information, see [Client notifications](../../clients/manage/client-notification).

### Improvements to collection evaluation

The following changes in collection evaluation behavior can improve site performance:

- Previously, when you configured a schedule on a query-based collection, the site would continue to evaluate the query whether or not you enabled the collection setting to **Schedule a full update on this collection**. To fully disable the schedule, you had to change the schedule to **None**. Now the site clears the schedule when you disable this setting. To specify a schedule for collection evaluation, enable the option to **Schedule a full update on this collection**.
- You can't disable the evaluation of built-in collections like **All Systems**, but now you can configure the schedule. This behavior allows you to customize this action at a time that meets your business requirements.

For more information, see [How to create collections](../../clients/manage/collections/create-collections#bkmk_create).

### Improvement to client installation

When installing the Configuration Manager client, the ccmsetup process contacts the management point to locate the necessary content. Previously in this process the management point only returns distribution points in the client's current boundary group. If no content is available, the setup process falls back to download content from the management point. There's no option to fall back to distribution points in other boundary groups that might have the necessary content. Now the management point returns distribution points based on boundary group configuration.

For more information, see [Configure boundary groups](../../servers/deploy/configure/boundary-groups-distribution-points#client-installation).

## Co-management

### Required app compliance policy for co-managed devices

Define compliance policy rules in Configuration Manager for required applications. This app assessment is part of the overall compliance state sent to Microsoft Intune for co-managed devices.

For more information, see [Co-management workloads](../../../comanage/workloads).

### Improvement to co-management dashboard

The co-management dashboard is enhanced with the following more detailed information:

- The **Co-management enrollment status** tile includes additional states
- A new **Co-management status** tile with a funnel chart shows states of the enrollment process
- A new tile with counts of **Enrollment errors**

![Co-management dashboard screenshot showing the top four tiles](media/1358980-comgmt-dashboard.png)

For more information, see [Co-management dashboard](../../../comanage/how-to-monitor#co-management-dashboard).

### Improvements to internet-based client setup

This release further simplifies the Configuration Manager client setup process for clients on the internet. The site publishes additional Azure Active Directory (Azure AD) information to the cloud management gateway (CMG). An Azure AD-joined client gets this information from the CMG during the ccmsetup process, using the same tenant to which it's joined. This behavior further simplifies enrolling devices to co-management in an environment with more than one Azure AD tenant. Now the only two required ccmsetup properties are **CCMHOSTNAME** and **SMSSiteCode**.

For more information, see [How to prepare internet-based devices for co-management](../../../comanage/how-to-prepare-win10#install-the-configuration-manager-client).

## Application management

### Convert applications to MSIX

Starting in version 1806, Configuration Manager supports deployment of the new Windows 10 app package (.msix) format. Now you can convert your existing Windows Installer (.msi) applications to the MSIX format.

For more information, see [Create Windows applications](../../../apps/get-started/creating-windows-applications#bkmk_msix).

### Repair applications

Specify a repair command line for Windows Installer and Script Installer deployment types. Then if you enable the option on the deployment, a new button is available in Software Center to **Repair** the application. When you configure an application with a repair program, users can start the command from Software Center.

For more information, see [Create applications](../../../apps/deploy-use/create-applications#bkmk_dt-content) and [Deploy applications](../../../apps/deploy-use/deploy-applications#bkmk_deploy-settings).

### Approve application requests via email

Configure email notifications for application approval requests. When a user requests an application, you receive an email. Click links in the email to approve or deny the request, without requiring the Configuration Manager console.

For more information, see [Approve applications](../../../apps/deploy-use/app-approval).

### Detection methods don't load Windows PowerShell profiles

You can use Windows PowerShell scripts for detection methods on applications and settings in configuration items. When these scripts run on clients, the Configuration Manager client now calls PowerShell with the `-NoProfile` parameter. This option starts PowerShell without profiles.

A PowerShell profile is a script that runs when PowerShell starts. You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.

Note

This change in behavior doesn't apply to [Scripts](../../../apps/deploy-use/create-deploy-scripts) or [CMPivot](../../servers/manage/cmpivot). Both of these features already use this PowerShell parameter.

For more information, see [Create applications](../../../apps/deploy-use/create-applications) and [Create custom configuration items](../../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client).

## OS deployment

### Task sequence support of Windows Autopilot for existing devices

[Windows Autopilot for existing devices](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) is now available with Windows 10, version 1809 or later. This new feature allows you to reimage and provision a Windows 7 device for [Windows Autopilot user-driven mode](/en-us/windows/deployment/windows-autopilot/user-driven) using a single, native Configuration Manager task sequence.

For more information, see [Windows Autopilot for existing devices](/en-us/autopilot/existing-devices).

### Specify the drive for offline OS image servicing

Now specify the drive that Configuration Manager uses when adding software updates to OS images and OS upgrade packages. This process can consume a large amount of disk space with temporary files, so this option gives you flexibility to select the drive to use.

For more information, see [Manage OS images](../../../osd/get-started/manage-operating-system-images#specify-the-drive-for-offline-os-image-servicing) or [Manage OS upgrade packages](../../../osd/get-started/manage-operating-system-upgrade-packages#specify-the-drive-for-offline-os-image-servicing).

### Task sequence support for boundary groups

When a device runs a task sequence and needs to acquire content, it now uses boundary group behaviors similar to the Configuration Manager client.

For more information, see [Boundary groups](../../servers/deploy/configure/boundary-groups-distribution-points#task-sequence-support).

### Improvements to driver maintenance

Driver packages now have additional metadata fields for **Manufacturer** and **Model**. Use these fields to tag driver packages with information to assist in general housekeeping, or to identify old and duplicate drivers that you can delete.

For more information, see [Manage drivers](../../../osd/get-started/manage-drivers).

### Improvements to Windows 10 servicing plan filters

Additional filters have been added to Windows 10 servicing plans. You can now filter by **Architecture**, **Product Category**, and if the upgrade is **Superseded**.

For more information, see [Windows 10 servicing plan](../../../osd/deploy-use/manage-windows-as-a-service#windows-servicing-plan).

### New task sequence variable for last action name

Along with the task sequence variable \_SMSTSLastActionRetCode, the task sequence also sets a new variable **\_SMSTSLastActionName**. It also logs this value to the smsts.log file. This new variable is beneficial when troubleshooting a task sequence. When a step fails, a custom script can include the step name along with the return code.

For more information, see [Task sequence variables](../../../osd/understand/task-sequence-variables#SMSTSLastActionName).

## Software updates

### Phased deployment of software updates

Create phased deployments for software updates. Phased deployments allow you to orchestrate a coordinated, sequenced rollout of software based on customizable criteria and groups.

For more information, see [Create phased deployments](../../../osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/mem/configmgr/sum/toc.json&amp;bc=/mem/configmgr/sum/breadcrumb/toc.json).

### Improvement to maintenance windows for software updates

The following client setting is in the **Software Updates** group to control the installation behavior of software updates in maintenance windows: **Enable installation of updates in "All deployments" maintenance window when "Software update" maintenance window is available**

By default, this option is **No** to keep consistent with the existing behavior. Change it to **Yes** to allow clients to use other available maintenance windows to install software updates.

For more information, see [Software updates client settings](../../clients/deploy/about-client-settings#bkmk_SUMMaint).

### Improvement to software updates maintenance

WSUS cleanup tasks now run on secondary sites. WSUS cleanup for expired updates is run and superseded updates are declined in WSUS for secondary sites.

For more information, see [WSUS cleanup behavior starting in version 1810](../../../sum/deploy-use/software-updates-maintenance#wsus-cleanup-behavior-starting-in-version-1810)

### Improvement to software update supersedence rules

You can now specify supersedence rules for feature updates separately from non-feature updates. This means your upgrades won't be removed from Configuration Manager before you have completed servicing your Windows 10 clients.

For more information, see [Supersedence rules](../../../sum/get-started/install-a-software-update-point#supersedence-rules).

## Reporting

### Improvement to lifecycle dashboard

The product lifecycle dashboard now includes information for **System Center 2012 Configuration Manager and later**.

There's also a new report, **Lifecycle 05A - Product lifecycle dashboard**. It includes similar information as the in-console dashboard.

For more information on this dashboard, see [Use the Product Lifecycle dashboard](../../clients/manage/asset-intelligence/product-lifecycle-dashboard).

### Improvement to data warehouse

You can now synchronize more tables from the site database to the data warehouse. This change allows you to create more reports based on your business requirements.

For more information, see [Data warehouse](../../servers/manage/data-warehouse).

## Configuration Manager console

### Configuration Manager administrator authentication

You can now specify the minimum authentication level for administrators to access Configuration Manager sites. This feature enforces administrators to sign in to Windows with the required level. To configure this setting, find the **Authentication** tab in **Hierarchy Settings**.

For more information, see [Plan for the SMS Provider](../hierarchy/plan-for-the-sms-provider#authentication).

### Support Center

Use Support Center for client troubleshooting, real-time log viewing, or capturing the state of a Configuration Manager client computer for later analysis. Support Center is a single tool to combine many administrator troubleshooting tools. Find the Support Center installer on the site server in the **cd.latest\SMSSETUP\Tools\SupportCenter** folder.

For more information, see [Support Center](../../support/support-center).

### Management insights dashboard

The **Management Insights** node now includes a graphical dashboard. This dashboard displays an overview of the rule states, which makes it easier for you to show your progress. The dashboard includes the following tiles:

- **Management insights index**: Tracks overall progress on management insights rules. The index is a weighted average. Critical rules are worth the most. This index gives the least weight to optional rules.
- **Management insights groups**: Shows percent of rules in each group.
- **Management insights priority**: Shows percent of rules by priority.
- **All insights**: A table of insights including priority and state.

![Screenshot of management insights dashboard](media/1357979-management-insights-dashboard.png)

For more information, see [Management insights](../../servers/manage/management-insights).

### Improvements to CMPivot

CMPivot includes the following improvements:

- Save **Favorite** queries
- On the Query Summary tab, select the count of Failed or Offline devices, and then select the option to **Create Collection**.

For more information on additional performance and troubleshooting improvements to CMPivot, see Improvements to scripts.

For more information on CMPivot, see [CMPivot](../../servers/manage/cmpivot).

### Improvements to scripts

You can now view detailed script output in raw or structured JSON format. This formatting makes the output easier to read and analyze.

The following performance and troubleshooting improvements apply to both CMPivot and scripts:

- Updated clients return output less than 80 KB to the site over a fast communication channel. This change increases the performance of viewing script or query output.
- Additional logs for troubleshooting

For more information, see the following articles:

- [Create and run PowerShell scripts from the Configuration Manager console](../../../apps/deploy-use/create-deploy-scripts)
- [Troubleshooting CMPivot](../../servers/manage/cmpivot-tsg)

### SMS Provider API

The SMS Provider now provides read-only API interoperability access to WMI over HTTPS, called the **administration service**. This REST API can be used in place of a custom web service to access information from the site.

The **SMS Provider** appears as a role with an option to allow communication over the cloud management gateway. The current use for this setting is to enable application approvals via email from a remote device.

For more information, see [Plan for the SMS Provider](../hierarchy/plan-for-the-sms-provider#administration-service).

## On-premises MDM

### An Intune connection is no longer required for new on-premises MDM deployments

The on-premises MDM prerequisite to configure a Microsoft Intune subscription is no longer required for new deployments. Your organization still requires Intune licenses to use this feature. You can't currently remove the Intune connection from existing on-premises MDM deployments. For more information, see the [Intune support blog post](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

## Other updates

Aside from new features, this release also includes additional changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4482169).

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [PowerShell version 1810 release notes](/en-us/powershell/sccm/1810-release-notes).

The following update rollup (4488598) is available in the console starting on 25 March 2019: [Update rollup 2 for Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4488598). This replaces the prior update rollup, KB 4486457.

### Hotfixes

The following additional hotfixes are available to address specific issues:

| ID | Title | Date | In-console |
| --- | --- | --- | --- |
| [4487960](https://support.microsoft.com/help/4487960) | Microsoft Intune connector certificate does not renew in Configuration Manager | 18 January 2019 | Yes |
| [4490434](https://support.microsoft.com/help/4490434) | Duplicate user discovery columns are created in Configuration Manager | 22 February 2019 | Yes |
| [4490575](https://support.microsoft.com/help/4490575) | Update installations stop responding or never show completion in Configuration Manager, version 1810 | 22 February 2019 | Yes |