---
layout: Conceptual
title: Manage settings for software updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/manage-settings-for-software-updates
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
description: Learn about the client settings that are appropriate for software updates at your site after you install the software update point.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: 41d9647c-11a2-b092-6f37-2176a3f8562d
document_version_independent_id: 416a59b0-946c-48aa-a82b-95b74572334a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/get-started/manage-settings-for-software-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/get-started/manage-settings-for-software-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/get-started/manage-settings-for-software-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6a94c32-e46a-1068-29c0-4e10206838b8
---

# Manage settings for software updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you synchronize software updates in Configuration Manager, configure and verify the settings in the following sections.

## Client settings for software updates

After you install the software update point, software updates is enabled on clients by default. The settings on the **Software Updates** page in client settings have default values. The client settings are used site-wide. They affect when software updates are scanned for compliance, and how & when software updates are installed on client computers. Before you deploy software updates, verify that the client settings are appropriate for software updates at your site.

Important

- The **Enable software updates on clients** setting is enabled by default. If you clear this setting, Configuration Manager removes the existing deployment policies from the client under certain conditions.

- Starting with the September 2020 cumulative update, HTTP-based Windows Server Update Services (WSUS) servers are secure by default. A client scanning for updates against an HTTP-based WSUS isn't allowed to leverage a user proxy by default. If you still require a user proxy despite the security trade-offs, a new [software updates client setting](../../core/clients/deploy/about-client-settings#software-updates) is available to allow these connections. For more information about the changes for scanning WSUS, see [September 2020 changes to improve security for Windows devices scanning WSUS](https://go.microsoft.com/fwlink/?linkid=2144403). So the best security protocols are in place, Microsoft recommends that you use the TLS/SSL protocol to help [secure your software update infrastructure](software-update-point-ssl).

For information about how to configure client settings, see [How to configure client settings](../../core/clients/deploy/configure-client-settings).

For more information about the client settings, see [About client settings](../../core/clients/deploy/about-client-settings).

## Software Updates Best Practices

### Conflicting configurations

The Configuration Manager client sets local group policies to control the software update workflow and scan for update compliance. When domain group policy objects (GPO) are used for Windows Updates, it overrides the equivalent setting used by our client. The client expects specific registry values to remain in place without any other platform changing the settings. Domain GPO's can cause the component to go into an error state, even if the setting is perceived to be the same.

For example, if a domain group policy sets the WSUS Server, Configuration Manager can't configure or access the setting and might not operate properly. This behavior causes clients to have scan failures and issues reporting compliance back to the site.

### Remove older deployments and software update groups

To optimize site performance and improve compliance accuracy, remove older deployments and software update groups. Since updates are cumulative, there's no need to keep older updates deployed. Keeping old deployments negatively affects your environment.

### Remove any unnecessary Products & Categories in the Software Update Properties

Selecting too many products & categories for sync can cause negative performance. Remember, devices have to scan every update in the SUSDB, whether it's deployed or not. So, only select products that are relevant and necessary.

Many products and categories shown in the list are only for WSUS. Configuration Manager can't deploy them. So, don't select these items. Some examples include:

- Dynamic Updates
- Servicing Drivers
- Silverlight
- Legacy operating systems that are no longer supported, like Windows 7, Windows 8, etc.
- 'Rollups' category, 'Feature Packs' category, 'Service Packs' category, etc.

### Software Updates Scan Cycle and Deployment Cycle

When the scan cycle or deployment cycle client settings are less than the default of once per 7 days, it can have have negative performance effect because of excessive scanning. In general, it's not necessary to scan more than once a week. Devices already have a built-in mechanism to scan for updates when they receive a deployment.

### Self Update

When Automatic Updates is enabled on client computers, the Windows Update Agent (WUA) automatically performs a self-update when a newer version becomes available or when there are problems with a WUA component. When Automatic Updates isn't configured or is disabled, and client computers have an earlier version of the WUA, the client computers must run the WUA installation file.

## Software updates properties

The software update properties provide information about software updates and associated content. You can also use these properties to configure settings for software updates. When you open the properties for multiple software updates, only the **Maximum Run Time** and **Custom Severity** tabs are displayed.

Use the following procedure to open software update properties.

#### To open software update properties

1. In the Configuration Manager console, click **Software Library**.
2. In the Software Library workspace, expand **Software Updates**, and click **All Software Updates**.
3. Select one or more software updates, and then, on the **Home** tab, click **Properties** in the **Properties** group.

    Note

    On the **All Software Updates** node, Configuration Manager displays only the software updates that have a **Critical** and **Security** classification, and that have been released in the last 30 days.

### Review software updates information

In software update properties, you can review detailed information about a software update. The detailed information isn't shown when you select more than one software update. The following sections describe the information that is available for a selected software update.

#### Software update details

In the **Update Details** tab, you can view the following summary information about the selected software update:

- **Bulletin ID**: Specifies the bulletin ID that is associated with security software updates. You can find security bulletin details by searching on the bulletin ID on the [Microsoft Security Response Center](https://portal.msrc.microsoft.com/) Web page.

Note

The way Microsoft documents security updates is changing. The previous model used security bulletin webpages and included security bulletin ID numbers (e.g. MS16-XXX) as a pivot point. This form of security update documentation, including bulletin ID numbers, is being retired and replaced with the Security Update Guide. Instead of bulletin IDs, the new guide pivots on vulnerability ID numbers and KB Article ID numbers. For more information, see the [Security Update Guide FAQs](https://www.microsoft.com/msrc/faqs-security-update-guide).

- **Article ID**: Specifies the article ID for the software update. The referenced article provides more detailed information about the software update and the issue that the software update fixes or improves.
- **Date revised**: Specifies the date that the software update was last modified.
- **Maximum severity rating**: Specifies the vendor-defined severity rating for the software update.
- **Description**: Provides an overview of what condition the software update fixes or improves.
- **Applicable languages**: Lists the languages for which the software update is applicable.
- **Affected products**: Lists the products for which the software update is applicable.

#### Content information

In the **Content Information** tab, review the following information about the content that is associated with the selected software update:

- **Content ID**: Specifies the content ID for the software update.
- **Downloaded**: Indicates whether Configuration Manager has downloaded the software update files.
- **Language**: Specifies the languages for the software update.
- **Source Path**: Specifies the path to the software update source files.
- **Size (MB)**: Specifies the size of the software update source files.

#### Custom bundle information

In the **Custom Bundle Information** tab, review the custom bundle information for the software update. When the selected software update contains bundled software updates that are contained in the software update file, they are displayed in the **Bundle information** section. This tab doesn't show bundled software updates that are displayed in the **Content Information** tab, such as update files for different languages.

#### Supersedence information

On the **Supersedence Information** tab, you can view the following information about the supersedence of the software update:

- **This update has been superseded by the following updates**: Specifies the software updates that supersede this update, which means that the updates listed are newer. In most cases, you deploy one of the software updates that supersedes the software update. The software updates that are displayed in the list contain hyperlinks to webpages that provide more information about the software updates. When this update isn't superseded, **None** is displayed.
- **This update supersedes the following updates**: Specifies the software updates that are superseded by this software update, which means this software update is newer. In most cases, you deploy this software update to replace the superseded software updates. The software updates that are displayed in the list contain hyperlinks to web pages that provide more information about the software updates. When this update doesn't supersede any other update, **None** is displayed.

### Configure software updates settings

In the properties, you can configure software update settings for one or more software updates. You can configure most software update settings only at the central administration site or stand-alone primary site. The following sections help you to configure settings for software updates.

#### Set maximum run time

In the **Maximum Run Time** tab, set the maximum amount of time a software update is allotted to complete on client computers. If the update takes longer than the maximum run-time value, Configuration Manager creates a status message and stops the software updates installation. You can configure this setting only on the central administration site or a stand-alone primary site.

Configuration Manager also uses this setting to determine whether to initiate the software update installation within a configured maintenance window. If the maximum run-time value is greater than the available remaining time in the maintenance window, the software updates installation is postponed until the start of the next maintenance window. When there are multiple software updates to be installed on a client computer with a configured maintenance window (timeframe), the software update with the lowest maximum run time installs first. Then, the software update with the next lowest maximum run time installs next, and so on. Before it installs each software update, the client verifies that the available maintenance window provides enough time to install the software update. After a software update starts installing, it continues to install, even if the installation goes beyond the end of the maintenance window. For more information about maintenance windows, see the [How to use maintenance windows](../../core/clients/manage/collections/use-maintenance-windows).

On the **Maximum Run Time** tab, you can view and configure the following settings:

- **Maximum run time**: Specifies the maximum number of minutes allotted for a software update installation to complete before Configuration Manager stops the installation. This setting also determines if there's enough available time remaining to install the update before the end of a maintenance window. For service packs, the default setting is 60 minutes. For other software update types, if you did a fresh install of Configuration Manager version 1511 or higher, the default is 10 minutes. It's 5 minutes when you upgraded from a previous version. Values can range from 5 to 9999 minutes.

Important

Be sure to set the maximum run time value smaller than the configured maintenance window time. Or, increase the maintenance window time to a value greater than the maximum run time. Otherwise, the software update installation won't initiate.

#### Set custom severity

In the properties for a software update, you can use the **Custom Severity** tab to configure custom severity values for the software updates. This feature can be necessary if the predefined severity values don't meet your needs. The custom values are listed in the **Custom Severity** column in the Configuration Manager console. You can sort the software updates by the defined custom severity values and can also create queries & reports that can filter on these values. You can configure this setting only on the central administration site or stand-alone primary site.

You can configure the following settings on the **Custom Severity** tab.

- **Custom severity**: Sets a custom severity value for the software updates. Select **Critical**, **Important**, **Moderate**, or **Low** from the list. By default, the custom severity value is empty.

## CRL checking for software updates

By default, the certificate revocation list (CRL) isn't checked when verifying the signature on Configuration Manager software updates. Checking the CRL each time a certificate is used offers more security against using a certificate that has been revoked. But, it introduces a connection delay and incurs additional processing on the computer performing the CRL check.

If used, CRL checking must be enabled on the Configuration Manager consoles that process software updates.

#### To enable CRL checking

On the computer performing the CRL check, from the product DVD, run the following command from a command prompt:

```cmd
\SMSSETUP\BIN\X64\\**<*language*>**\UpdDwnldCfg.exe /checkrevocation
```

For example, for English (US) run `\SMSSETUP\BIN\X64\00000409\UpdDwnldCfg.exe /checkrevocation`.