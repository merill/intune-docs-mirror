---
layout: Conceptual
title: What's new in version 2203 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2203
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
description: Get details about changes and new capabilities introduced in version 2203 of Configuration Manager current branch.
ms.date: 2022-04-26T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: fc51f77d-9942-44cc-2c0c-b0629cf5c59f
document_version_independent_id: fc51f77d-9942-44cc-2c0c-b0629cf5c59f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2203.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2203
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2203.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6af2f3e8-41f7-d223-637e-47f8ce04613e
---

# What's new in version 2203 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2203 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2010 or later.  When installing a new site, this version of Configuration Manager will also be available as a [baseline version](../../servers/manage/updates#bkmk_note1) soon after global availability of the in-console update. This article summarizes the changes and new features in Configuration Manager, version 2203.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2203](../../servers/manage/checklist-for-installing-update-2203). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2203#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Cloud-attached management

### Prefer cloud-based software update points

Clients now prefer to scan against a cloud management gateway (CMG) software update point (SUP) over an on-premises SUP when the boundary group uses the **Prefer cloud based source over on-premises source** option. To reduce the performance effect of this change, existing clients don't automatically switch to a cloud-based software update point.

For more information, see [Boundary groups and software update points](../../servers/deploy/configure/boundary-groups-software-update-points#bkmk_prefer_cmgsup).

## Site infrastructure

### Visualize content distribution status

You can now monitor content distribution path and status in a graphical format. The graph shows distribution point type, distribution state, and associated status messages. This visualization allows you to more easily understand the status of your content package distribution. It helps you answer questions like:

- Has the site successfully distributed the content?
- Is the content distribution in progress?
- Which distribution points have already processed the content?

![Visualization of content distribution status of the Configuration Manager client package in an example hierarchy.](media/9495651-view-content-distribution-small.png)

For more information, see [Visualize content distribution status](../../servers/deploy/configure/visualize-content-distribution-status).

### Improvements to Power BI Report Server integration

We've made the following improvements for Power BI Report Server integration:

- You can now use Microsoft Power BI Desktop (Optimized for Power BI Report Server) versions that were released after January 2021
- Configuration Manager now correctly handles Power BI reports saved by Power BI Desktop (optimized for Power BI Report Server) May 2021 or later.

For more information, see [Integrate with Power BI Report Server](../../servers/manage/powerbi-report-server).

### Exclude data warehouse reporting tables from synchronization

When you install the [data warehouse](../../servers/manage/data-warehouse), it synchronizes a set of default tables from the site database. These tables are required for data warehouse reports. While troubleshooting issues, you may want to stop synchronizing these default tables. Starting in this release, you can exclude one or more of these required tables from synchronization.

For more information, see [Exclude data warehouse reporting tables from synchronization](../../servers/manage/data-warehouse#bkmk_exclude).

### Improvements to management insights

The following improvements have been made to management insights:

- A new management insights group was added to **Management Insights**. The **Deprecated and unsupported features** group contains rules that will help you manage and remove deprecated features. The prerequisite checker will also check for deprecated and unsupported features during site installs and upgrades.
- A new rule for detecting Windows Server 2012 and 2012 R2 was added to the **Proactive Maintenance** group.

For more information, see [Management insights for deprecated and unsupported features](../../servers/manage/management-insights#deprecated-and-unsupported-features) and [Management insights for proactive maintenance](../../servers/manage/management-insights#proactive-maintenance).

## Client management

### Deployment Status client notification actions

You can now perform client notification actions, including **Run Scripts**, from the **Deployment Status** view.

For more information, see [Review deployment details](../../../apps/deploy-use/monitor-applications-from-the-console#review-deployment-details).

## Collections

### Delete collection references

Previously, when you would delete a collection with dependent collections, you first had to delete the dependencies. The process of finding and deleting all of these collections could be difficult and time consuming. Now when you delete a collection, you can review and delete its dependent collections at the same time.

For more information, see [Delete collection references](../../clients/manage/collections/manage-collections#delete-collection-references).

## Software updates

### LEDBAT support for software update points

You can now enable Windows Low Extra Delay Background Transport (LEDBAT) for your software update points. LEDBAT adjusts download speeds during client scans against WSUS to help control network congestion.

For more information, see [Install a software update point](../../../sum/get-started/install-a-software-update-point#bkmk_ledbat).

### Pre-download content for available software updates

You can now pre-download content for software updates that are included in available deployments. Required deployments already pre-download content by default. Enabling this new setting reduces installation wait times for clients since installation notifications won't be visible in Software Center until the content has fully downloaded.

For more information, see [Deploy software updates](../../../sum/deploy-use/manually-deploy-software-updates#process-to-manually-deploy-the-software-updates-in-a-software-update-group).

### Customize maximum run time for other software update types

Previously, software updates that didn't belong to the following update categories defaulted to a maximum run time of 60 minutes (or 10 minutes prior to version 2103):

- Windows feature updates
- Windows non-feature updates
- Office 365 updates

You can now customize the maximum run time for all other software updates, which includes third-party updates.

For more information, see [Maximum run time](../../../sum/plan-design/plan-for-software-updates#bkmk_maxruntime) and [Install and configure a software update point](../../../sum/get-started/install-a-software-update-point#bkmk_maxruntime).

### ADR scheduling improvements for deployments

The **Software available time** and **Installation deadline** for deployments created by an automatic deployment rule (ADR) are now calculated based on the time the ADR evaluation is scheduled and starts. Previously, these times were calculated based on when the ADR evaluation completed. This change makes the **Software available time** and **Installation deadline** consistent and predictable for deployments.

For more information, see [Automatic deployment rules (ADR)](../../../sum/deploy-use/automatically-deploy-software-updates).

### Added folder support for nodes in the Software Library

You can now organize software update groups and packages by using folders. This change allows for better categorization and management of software updates.

For more information, see [Deploy software updates](../../../sum/deploy-use/deploy-software-updates#bkmk_folder).

### Alerts for orchestration groups

If an orchestration group fails, an alert is now displayed in in **Monitoring** &gt; **Alerts** &gt; **Active Alerts**. For more information, see [Monitor orchestration groups](../../../sum/deploy-use/monitor-orchestration-groups#bkmk_alerts).

## OS deployment

### Escrow BitLocker recovery password to the site during a task sequence

You can now configure the **Enable BitLocker** step of a task sequence to escrow the BitLocker recovery information for the OS volume to Configuration Manager. Previously, you had to escrow to Active Directory, or wait for the Configuration Manager client to receive BitLocker management policy after the task sequence. This new option makes sure that the device is fully protected by BitLocker when the task sequence completes, and that you can recover the OS volume immediately.

For more information, see [Task sequence steps: Enable BitLocker](../../../osd/understand/task-sequence-steps#enable-bitlocker).

### Custom icon support for task sequences and packages

Previously, task sequences and legacy packages would always display a default icon in Software Center. Based on your feedback, you can now add custom icons for task sequences and legacy packages. These icons appear in Software Center when you deploy these objects. Instead of a default icon, a custom icon can improve the user experience to better identify the software.

For more information, see [Manage task sequences](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks#more-options-tab) and [Packages and programs](../../../apps/deploy-use/packages-and-programs#custom-icons-for-packages).

## Application management

### Improvements to implicit uninstall

If you deploy an application or app group to a user collection that's based on a security group, and you enable implicit uninstall, changes to the security group are now honored. When the site discovers the change in group membership, Configuration Manager uninstalls the app for the user that you removed from the security group.

For more information, see [implicit uninstall](../../../apps/deploy-use/uninstall-applications#implicit-uninstall).

## Community hub

### Delete a contribution you made to Community hub

You can now delete contributions you've made to the Community hub. For more information, see [Contribute to Community hub](../../servers/manage/community-hub-contribute#bkmk_delete).

### Search filter list

The console now displays a list of filters you can use when searching the Community hub. For more information, see [Filter Community hub content when searching](../../servers/manage/community-hub#bkmk_search).

## Configuration Manager console

### Dark theme for the console

The Configuration Manager console now offers a dark theme. For more information, see [How to use the Configuration Manager console](../../servers/manage/admin-console#bkmk_dark).

### Improvements for sending feedback

- You now have the ability to connect feedback you send to Microsoft through the Configuration Manager console to an authenticated Azure Active Directory (Azure AD) user account or Microsoft Account (MSA). User authentication will help Microsoft ensure the privacy of your feedback and diagnostic data.
- The feedback button is now displayed in other console locations.

For more information, see [Product feedback](../../understand/product-feedback#recent-changes-to-feedback).

### Improvements to dashboards

Dashboards, such as the **Windows Servicing** and **Microsoft Edge Management** dashboards, now use the Microsoft Edge WebView2 Runtime. To use dashboards, install the WebView2 console extension, then reopen the console.

For more information, see the [WebView2 console extension](../../servers/manage/admin-console-extensions#bkmk_notification).

### Console and user experience improvements

Based on your feedback, we've made a few improvements to the console and user experience.

- When using temporary device nodes, device actions like **Run Scripts** are now available to make the experience in the console consistent.
- Other management insights rules now have drill-through actions.
- Copy/paste is available for more objects from details panes.
- The **Name** property is added to the details pane for configuration items, configuration item related policies, and applications.
- Software update search results and the search criteria are now cached when you navigate to another node. When you navigate back to the **All Software Updates** node, your search criteria and results are preserved from your last query.
- Added a search filter to the **Products** and **Classifications** tabs in the **Software Update Point Component Properties**
- You can now exclude subcontainers when doing **Active Directory System Discovery** and **Active Directory User Discovery** in untrusted domains
- Added a **Cloud Sync** column to collections to indicate if the collection is synchronizing with Azure Active Directory
- Added the **Collection ID** to the collection summary details tab
- Increased the size of the **Membership Rules** pane in the **Properties** page for collections
- Added a **View Script** option for **Run PowerShell Script** steps when using the **View** action for a task sequence

For more information, see [Console changes and tips](../../servers/manage/admin-console-tips#bkmk_2203).

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

The following features are deprecated. You can still use them now, but Microsoft plans to end support in the future.

- The Configuration Manager client for **macOS** and Mac client management. For more information, see [Supported clients: Mac computers](../configs/supported-operating-systems-for-clients-and-devices#mac-computers)
- The site system roles for on-premises MDM and macOS clients: **enrollment proxy point and enrollment point**

As previously announced, version 2203 drops support for the following features:

- The ability to deploy a cloud management gateway (CMG) as a **cloud service (classic)**. All CMG deployments should use a [virtual machine scale set](../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets).
- The following compliance settings for **Company resource access**: 

    - Certificate profiles and the certificate registration point site system role
    - VPN profiles
    - Wi-Fi profiles
    - Windows Hello for Business settings
    - Email profiles
    - Co-management resource access workload

        For more information, see [Frequently asked questions about resource access deprecation](../../../protect/plan-design/resource-access-deprecation-faq).

## Other updates

Starting with this version, the following features are no longer [pre-release](../../servers/manage/pre-release-features):

- [Task sequence debugger](../../../osd/deploy-use/debug-task-sequence)

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [version 2203 release notes](/en-us/powershell/sccm/2203-release-notes).

Aside from new features, this release also includes other changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 2203](../../../hotfix/2203/13174460).