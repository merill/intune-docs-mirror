---
layout: Conceptual
title: What's new in version 2111 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2111
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
description: Get details about changes and new capabilities introduced in version 2111 of Configuration Manager current branch.
ms.date: 2021-12-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 058d894e-5689-5579-28fb-4c40acc5c685
document_version_independent_id: 058d894e-5689-5579-28fb-4c40acc5c685
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2111.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2111
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2111.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2313e8b8-d04d-b51b-5dd0-79d27e62c2ee
---

# What's new in version 2111 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2111 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2006 or later.  This article summarizes the changes and new features in Configuration Manager, version 2111.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2111](../../servers/manage/checklist-for-installing-update-2111). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2111#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Application management

### Improvements to application groups

Tip

Starting with this release, app groups are no longer a [pre-release](../../servers/manage/pre-release-features) feature.

This release includes the following improvements to application groups:

- Now when you deploy an app group as required to a device or user collection, you can specify that it automatically uninstalls when the resource is removed from the collection.
- More app approval behaviors are now supported with app groups.

For more information, see [Create application groups](../../../apps/deploy-use/create-app-groups).

### Implicit uninstall for user collections

In Configuration Manager current branch version 2107, you can enable an application deployment to support implicit uninstall.

Starting in this release, this behavior also applies to deployments to user collections. If a user is in a collection, the application installs. Then when you remove the user from the collection, the application uninstalls.

For more information, see [implicit uninstall](../../../apps/deploy-use/uninstall-applications#implicit-uninstall).

## Software updates

### Approvals for orchestration group scripts

Tip

Starting with this release, orchestration groups are no longer a [pre-release](../../servers/manage/pre-release-features) feature.

Pre and post-scripts for orchestration groups now require approval to take effect. If you select a script from a file, author, or modify your own script, approval for the script is required from another admin. When selecting an approved script from the **Scripts** library, no other approval is needed. To assist you with script approval, the following two tabs were added to the details pane for **Orchestration Groups**:

- **Summary**: Contains information about the selected orchestration group, including the **Approval State** of scripts.
- **Scripts**: Lists information about pre and post-scripts, including the timeout, approver, and approval state for each script.

For more information, see [Approvals for orchestration group scripts](../../../sum/deploy-use/create-orchestration-groups#approvals-for-orchestration-group-scripts).

### Improvements to ADR search criteria

We've added the following options in the **Date Released or Revised** search criteria for automatic deployment rules:

- Older than 30 days
- Older than 60 days
- Older than 90 days
- Older than 6 months
- Older than 1 year

For more information, see [Automatically deploy software updates](../../../sum/deploy-use/automatically-deploy-software-updates).

### Enable update notifications from Microsoft 365 Apps

You can now configure the end-user experience for Microsoft 365 Apps updates. This client setting allows you to enable or disable notifications from Microsoft 365 Apps for these updates. The new **Enable update notifications from Microsoft 365 Apps** option has been added to the **Software Updates** group of client settings.

For more information, see [About client settings in Configuration Manager](../../clients/deploy/about-client-settings#enable-update-notifications-from-microsoft-365-apps).

## Cloud-attached management

### Simplified cloud attach configuration

We've simplified the process to cloud attach your Configuration Manager environment. You can now choose to use a streamlined set of recommended defaults when cloud attaching your environment. By using the recommended default settings, your eligible devices will be cloud attached and you'll enable capabilities like rich analytics, cloud console, and real-time device querying.

For more information, see the [Overview for cloud attach](../../../cloud-attach/overview) and [Enable cloud attach](../../../cloud-attach/enable).

### Improvements to cloud management gateway

Starting in this release, cloud management gateway (CMG) deployments with a virtual machine scale set support Azure US Government cloud environments.

For more information, see [CMG - Virtual machine scale sets](../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets).

## Site infrastructure

### Improvements to external notifications

Starting in Configuration Manager current branch version 2107, you could enable the site to send notifications to an external system or application. This feature used a PowerShell script to manage the status filter rules and subscriptions.

This release adds support in the Configuration Manager console to create or edit a subscription for external notifications. It supports events for status filter rules and application approval requests.

For more information, see [External notifications](../../servers/manage/external-notifications).

### .NET version 4.6.2 prerequisite check is an error

Configuration Manager current branch version 2107 has a warning prerequisite rule that checks for Microsoft .NET Framework version 4.6.2. This version of .NET is required on site servers, specific site systems, clients, and the Configuration Manager console.

Starting in this release, this prerequisite rule for .NET 4.6.2 is an error. Until you upgrade .NET, you can't continue installing or updating the site to this version of Configuration Manager.

For more information, see [List of prerequisite checks for Configuration Manager](../../servers/deploy/install/list-of-prerequisite-checks#required-version-of-microsoft-net-framework-error).

Important

When the Configuration Manager client updates to version 2111 or later, client notifications are dependent upon .NET 4.6.2 or later. Until you update .NET to version 4.6.2 or later, and restart the device, users won't see notifications from Configuration Manager. Other client-side functionality may be affected until the device is updated and restarted. For more information, see [More details about Microsoft .NET](../../clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#more-details-about-microsoft-net).

### Improvements to VPN boundary types

If you use the **VPN** boundary type, you can now match the start of a connection name or description instead of the whole string. Some third-party VPN drivers dynamically create the connection, which starts with a consistent string but also has a unique connection identifier. For example, `Virtual network adapter #19`. When you use the **Connection name** or **Connection description** options, also use the new **Starts with** option.

For more information, see [Define network locations as boundaries](../../servers/deploy/configure/boundaries#vpn).

### Status messages for console extensions

To improve the visibility and transparency of console extensions, the site now creates status messages for related events. These status messages have IDs from **54201** to **54208**.

For more information, see [Manage Configuration Manager console extensions](../../servers/manage/admin-console-extensions#status-messages-for-console-extensions).

## Client management

### Improvements to client health dashboard

This release includes multiple improvements to the **Client health dashboard**.

![An example of the updated Client Health Dashboard.](media/5728069-client-health-dashboard-small.png)

- New actions in the ribbon:

    - **Choose Default Collection**: Set a persistent user preference
    - **Client Status Settings**: Configure the periods of time to evaluate client health
- More prominent **Overall client health** tile
- Filters condensed on a single tile
- The **Combined (All)** and **Combined (Any)** scenarios are replaced by a new tile, **Clients with any failure**
- New tile for **Health trends by scenario**

For more information, see [Client health dashboard](../../clients/manage/client-health-dashboard).

## Software Center

### Software Center notifications display with logo

If you enable Software Center customizations, the logo that you specify for Windows notifications is separate from the Software Center logo. This logo helps users to trust these notifications. When you deploy software to a client, the user sees notifications with your logo. For example:

![New software is available notification with custom logo.](media/4993167-notification-with-logo.png)

For more information, see [About client settings: Software Center](../../clients/deploy/about-client-settings#software-center) and [Plan for Software Center](../../../apps/plan-design/plan-for-software-center#brand-software-center).

## OS deployment

### Task sequence check for TPM 2.0

To help you better deploy Windows 11, the **Check Readiness** step in the task sequence now includes checks for TPM 2.0.

For more information, see [Task sequence steps: Check Readiness](../../../osd/understand/task-sequence-steps#BKMK_CheckReadiness).

### Improvements to the Windows servicing dashboard

We now display a **Windows 11 Latest Feature Updates** chart in the **Windows Servicing** dashboard. The new chart makes it easier to determine how many of your Windows 11 clients are on the latest feature update. To display the dashboard, go to **Software Library** &gt; **Overview** &gt; **Windows Servicing**.

For more information, see [The Windows servicing dashboard](../../../osd/deploy-use/manage-windows-as-a-service#bkmk_2103-dashboard).

## Configuration Manager console

### Custom properties for devices in the console

In Configuration Manager current branch version 2107, you can use the administration service to set custom properties on devices. These custom properties let you add external data to a device to help with deployment targeting, collection building, and reporting.

Starting in this release, you can create and edit these custom properties in the Configuration Manager console. This new user interface makes it easier to view and edit these properties. You can still use the administration service interface to automate the process from an external system.

For more information, see [Custom properties for devices](../../../develop/adminservice/custom-properties).

### Export to CSV

You can now export the contents of a grid view in the console along with the column headers to a comma-separated values (CSV) file that can be used to import to Excel or other applications. While you could previously cut and paste from a grid view, exporting to CSV makes extracting a large number of rows faster and easier.

For more information, see [Configuration Manager console changes and tips](../../servers/manage/admin-console-tips#bkmk_csv).

### Import console extensions wizard

There's a new wizard for importing console extensions that are managed for the hierarchy. You no longer need to use a PowerShell script to import a signed or unsigned console extension.

For more information, see [Import Configuration Manager console extensions](../../servers/manage/import-admin-console-extensions).

### Require installation of a console extension

You can now require a console extension to be installed before it connects to the site. After you require an extension, it automatically installs for the local console the next time an admin launches it.

For more information, see [Manage Configuration Manager console extensions](../../servers/manage/admin-console-extensions#require-installation-of-a-console-extension).

### Send product feedback from wizard and property dialogs

Wizards and some property pages now include an icon to provide feedback. When you select the feedback icon, the **Send a smile** and **Send a frown** options are displayed in the drop-down menu. The other feedback locations allow you to quickly send feedback right from your current activity. The feedback icon in the admin console's ribbon has also been updated to the new icon.

For more information, see [Product feedback for Configuration Manager](../../understand/product-feedback).

### Power BI sample reports

The following reports were recently added to the **Configuration Manager Sample Power BI Reports**:

- Client Status
- Content Status
- Microsoft Edge Management

For more information, see [Install Power BI sample reports](../../servers/manage/powerbi-sample-reports).

### Console improvements

In this release we've made the following improvements to the Configuration Manager console:

- Independent Software Vendors (ISVs) can create applications that extend Configuration Manager. They can use Configuration Manager to assign a certificate to an ISV proxy, which enables custom communication with the management point. To simplify the management of these ISV proxy certificates, you can now copy its GUID in the Configuration Manager console. For more information, see [ISV proxy solutions and PKI certificates](../security/cryptographic-controls-technical-reference#isv-proxy-solutions-and-pki-certificates).
- When you show the members of a device collection, and select a device in the list, switch to the **Collections** tab in the details pane. This new view shows the list of collections of which the selected device is a member. It makes it easier for you to see this information. For more information about improvements to the console, see [Configuration Manager console changes and tips](../../servers/manage/admin-console-tips#assets-and-compliance-workspace).
- When viewing a collection, you could previously see the amount of time the site took to evaluate the collection membership. This data is now also available in the **Monitoring** workspace. When you select a collection in either subnode of the **Collection Evaluation** node, the details pane displays this collection evaluation time data. For more information about improvements to the console, see [Configuration Manager console changes and tips](../../servers/manage/admin-console-tips#monitoring-workspace).
- There's a new built-in device collection for **Co-management Eligible Devices**. The **Co-management Eligible Devices** collection uses incremental updates and a daily full update to keep the collection up to date. For more information about improvements to the console, see [Configuration Manager console changes and tips](../../servers/manage/admin-console-tips#assets-and-compliance-workspace).

## Tools

### Options for Support Center Data Collector and Client Tools

New command-line options have been added to the Support Center Data Collector and Client Tools. The following options were added:

- Launch as current user without elevation
- Specify machine name
- Disable integrated authentication
- Display help

For more information, see [Support Center](../../support/support-center#command-line-options).

### Improvements to Support Center Log File Viewer and OneTrace

The Support Center **Log File Viewer** and **OneTrace** now display status messages in an easy to read format. Entries starting with `>>` are status messages that are automatically converted into a readable format when a log is opened. Search or filter on the `>>` string to find status messages in the log.

For more information, see [Support Center log file viewer](../../support/support-center-ui-reference#support-center-log-file-viewer) and [Support Center OneTrace](../../support/support-center-onetrace).

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

The following features are deprecated. You can still use them now, but Microsoft plans to end support in the future.

- Managing apps from the **Microsoft Store for Business and Education** with Configuration Manager
- **Asset intelligence**
- **On-premises MDM**

For more information, see [Removed and deprecated features for Configuration Manager](deprecated/removed-and-deprecated-cmfeatures).

As previously announced, version 2111 drops support for the following features:

- Third-party add-ons that use Microsoft .NET Framework version 4.6.1 or earlier, and rely on Configuration Manager libraries. Such add-ons need to use .NET 4.6.2 or later. For more information, see [External dependencies require .NET 4.6.2](../../../develop/core/changes/whats-new-sdk#external-dependencies-require-net-462).

## Other updates

Starting with this version, the following features are no longer [pre-release](../../servers/manage/pre-release-features):

- [Application groups](../../../apps/deploy-use/create-app-groups)
- [Orchestration groups](../../../sum/deploy-use/orchestration-groups)

Similarly, the [Microsoft Connected Cache with Configuration Manager](../hierarchy/microsoft-connected-cache) is now generally available for production use.

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [version 2111 release notes](/en-us/powershell/sccm/2111-release-notes).

Aside from new features, this release also includes other changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 2111](../../../hotfix/2111/11052354).