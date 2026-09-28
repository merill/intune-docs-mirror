---
layout: Conceptual
title: Community hub and GitHub - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/community-hub
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
description: Enable and use Community hub in Configuration Manager
ms.date: 2022-06-20T00:00:00.0000000Z
ms.subservice: other
ms.topic: article
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 6fac7d23-fe47-b861-656a-8fedddf87246
document_version_independent_id: 0bb21e00-8a0c-cdb1-2f0c-1f0e5a738a1b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/community-hub.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/community-hub
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/community-hub.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9bdc1705-9b40-49d6-8377-caa0b71fda66
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/686ed158-d915-41e9-9760-efa46ba88f6d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
platformId: f99528f0-fc28-6cf6-96b6-6cada682f3b0
---

# Community hub and GitHub - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in March 2023, this feature of Configuration Manager is being removed. All future versions, starting with 2303 will not have the Community hub node in the admin console. The Community hub node in older versions will be redirected to [deprecated features](../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

The IT Admin community has developed a wealth of knowledge over the years. Rather than reinventing items like Scripts and Reports from scratch, we've built a **Community hub** in Configuration Manager where IT Admins can share with each other. By leveraging the work of others, you can save hours of work. The Community hub fosters creativity by building on others work and having other people build on yours. GitHub already has industry-wide processes and tools built for sharing. Now, the Community hub can leverage those tools directly in the Configuration Manager console as foundational pieces for driving this new community.

## About Community hub

Community hub supports the following objects:

- CMPivot queries
- Applications
- Task sequences
- Configuration items
- Configuration baselines, including child configuration items 
    - Baselines with software updates or version-specific references aren't supported
- PowerShell Scripts
- Reports
- Power BI report templates
    - For information about sharing and using Power BI report templates with Community hub, see [Integrate with Power BI Report Server](powerbi-report-server#bkmk_community_hub).
- [Console extensions](community-hub-extensions) are available for download, but contributions are currently limited 
    - Content for console extensions isn't hosted by Microsoft. Currently, the source download location displays in the [verbose SmsAdminUi.log](../../plan-design/hierarchy/about-log-files#configuration-manager-console-logging-options) for the console that initiates the download.

## What's new

- Support for downloading signed console extensions and limited contribution, added in July 2021
- Filter content when using search, added in June 2021
- Support for configuration baselines including child configuration items, added in March 2021
- Support for Power BI reports, added in February 2021

## Prerequisites

- The device running the Configuration Manager console used to access the Community hub needs the following items:

    - .NET Framework version 4.6 or later
        - .NET Framework version 4.6.2 or later is required starting in Configuration Manager 2010
        - Starting in version 2107, the console requires .NET version 4.6.2, and version 4.8 is recommended. For more information, see [Install the Configuration Manager console](../deploy/install/install-consoles#net-version-requirements).
    - A supported version of Windows 10 or later
        - Windows Server isn't supported before version 2010, so the Configuration Manager console needs to be installed on a supported Windows client device separate from the site server.
        - Starting in version 2010, install the Microsoft Edge WebView2 console extension to support Windows Server.
- The [administration service](../../../develop/adminservice/set-up) in Configuration Manager needs to be set up and functional.
- If your organization restricts network communication with the internet using a firewall or proxy device, you need to allow the Configuration Manager console to access internet endpoints. For more information, see [Internet access requirements](../../plan-design/network/internet-endpoints#community-hub).
- A GitHub account is only required to contribute and share content from the **Your hub** page. If you don't wish to share, you can use contributions from others without having a GitHub account, For more information, see [Contribute to Community hub](community-hub-contribute).

    Important

    Configuration Manager versions 2006 and earlier won't be able to sign in to GitHub. Configuration Manager version 2010 or later with the WebView2 console extension installed is required for sign in.

## Permissions

- To import a script: **Create** permission for **SMS\_Scripts** class.
- To import a report: Full Administrator security role.
- Starting in version 2010, Full Administrators can opt in the hierarchy for unreviewed content via hierarchy settings. Lower hierarchy administrators can't opt in the hierarchy for unreviewed hub items. For more information, see the Categorize Community hub content section.

Most [built-in security roles](../../understand/fundamentals-of-role-based-administration) will have access to the **Community hub** node:

| Role name | View the hub | Contribute hub content | Download hub content |
| --- | --- | --- | --- |
| Remote Tools Operator | No | N/A | N/A |
| Read Only Analyst | Yes | No | No |
| All other roles | Yes | Yes | Yes |

## Use the Community hub

1. Go to the **Community hub** node in the **Community** workspace.
2. Select an item to download.
3. You'll need appropriate permissions in your Configuration Manager site to download objects from the hub and import them into the site.
    - To import a script: **Create** permission for SMS\_Scripts class.
    - To import a report: Full Administrator security role.
4. Downloaded reports are deployed to a report folder called **hub** on the reporting services point. Downloaded scripts can be seen in the **Run Scripts** node. Typically, downloaded items are placed in the console node for which they're used.
5. View all items downloaded from the hub by your organization by selecting **Your downloads** from the **Community hub** node.

[![All items downloaded from the Community hub](media/3555935-community-hub-downloads.png)](media/3555935-community-hub-downloads.png#lightbox)

## Filter Community hub content when searching

You can filter content in the Community hub when using search. The following filters are available to use when searching:

| Filter name | Example search | Uses a`like`filter |
| --- | --- | --- |
| **Type** | `type:report` | Yes |
| **Curated** | `curated:false` | No |
| **User** | `user:<GitHubUserName>` | No |
| **Organization** | `org:<GitHubOrganizationName>` | No |
| **Name** | `name:test_report` | Yes |
| **Description** | `desc:description` | Yes |

When filtering Community hub items in search:

- The filtering on some items is done using `like` so you don't need to know the exact name of an item you are trying to find. For instance, using `type:task` would return task sequences.
- You can't use the same filter twice in a search. For instance, using `type:report` and `type:extension` would only return reports since the second filter gets ignored.
- Search filtering respects the hierarchy setting for displaying [Community hub content categories](community-hub#bkmk_category).
    - If your hierarchy is set to **Display Microsoft and curated community content**, then `curated:false` is ignored.
    - If your hierarchy is set to **Display Microsoft content**, then the `curated:` filter is ignored.
- Starting in version 2203, the console displays a list of search filters you can use in Community hub. ![Screenshot of the console displaying Community hub search filters.](media/7281922-search-filter.png)

## Direct links to Community hub items

*(Introduced in version 2006)*

You can navigate to and reference items in the Configuration Manager console **Community hub** node with a direct link. Collaborate with your colleagues easily by sharing direct links to Community hub items. These deep links are currently only for items in the **Community hub** node of the console.

Prerequisites for direct links:

- Configuration Manager console version 2006 or later

Share an item:

1. Go the item in the hub and select **Share**.
2. Paste the copied link and share it with others.

Open a shared link:

1. Open the link from a machine that has the Configuration Manager console installed.
2. Select **Launch the Community hub** when prompted.
3. The console opens directly to the script in the **Community hub** node.

## Categorize Community hub content

*(Introduced in version 2010)*

Starting in Configuration Manager version 2010, Community hub content is grouped into a Microsoft, curated, or unreviewed category to allow admins to choose the types of content their environment displays. Admins can choose from the different categories of content that are provided in the **Community hub** to match their risk profile and their willingness to share and use content from those outside Microsoft and outside their own company. Only **Full Administrators** can opt in the hierarchy for unreviewed content via hierarchy settings.

Community hub content has three categories for content sources:

- **Microsoft curated**: Content provided by Microsoft
- **Community curated**: Content provided by the community that gets reviewed by Microsoft
- **Community unreviewed**: General content from the community that doesn't get reviewed by Microsoft

![The three categories for content sources in Community hub](media/8052494-community-hub-content-sources.png)

Admins can choose the types of content their environment displays from the following options:

- **Display Microsoft content**: Selecting this option means that only content created by Microsoft will be shown in the Community hub. This content has had some basic testing and scanning validation to confirm no malware and inappropriate text.
- **Display Microsoft and curated community content**: Show curated content from both Microsoft and community partners with basic level of review. Selecting this option means that only content that has been curated will be shown. The curation process includes basic review to confirm that the content doesn’t have malware and inappropriate text, but hasn’t necessarily been tested. It will include content from the community, not just from Microsoft.
- **Display all content including unreviewed content**: Selecting this option means that all content is shown. This option includes unreviewed open-source type samples from the community, meaning that the content hasn’t necessarily been reviewed at all. It's provided as-is as open-source type sample content. Doing your own inspection and testing before using is highly encouraged, which is good practice on any content, but especially this class of content.

![Hierarchy settings for allowed content sources for the Community hub](media/8052494-community-hub-content-hierarchy-settings.png)

Since the content is *open-source* style content, admins should always review what is provided before consuming it. The new curation process is intended to vet the material to make sure there aren't obvious quality or compliance issues, but it will be somewhat of a cursory review. All content stored within GitHub and accessed from the Community hub isn’t supported by Microsoft. Microsoft doesn’t validate content collected from or shared by the general community. For more information, see [GitHub Terms of Service](https://help.github.com/terms) and [GitHub Privacy Statement](https://help.github.com/privacy).

### Select the content categories to display in Community hub for the environment

1. In the Configuration Manager console, go to **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Sites**.
2. Select the top-level site in your hierarchy and select **Hierarchy Settings** from the ribbon.
3. On the **General** tab, change the **Community hub** setting to **Display Microsoft content**.
4. Select **Ok** when you're finished changing the hierarchy setting.
5. Open the **Community hub** node in the **Community** workspace.
6. Ensure that only Microsoft content is displayed and available for download.
7. Go back to **Hierarchy Settings** and select another option such as **Display all content, including unreviewed content**.
8. Confirm that only the type of content is displayed and able to be downloaded from the Community hub, that matches the corresponding hierarchy setting category.

## Install the WebView2 console extension

*(Introduced in version 2010)*

The Microsoft Edge WebView2 console extension enables the full functionality for Community hub. If WebView2 isn't installed, a banner is shown when you navigate to the **Community hub** node. The WebView2 console extension:

- Displays the **Community hub** on Windows Server operating systems
- Enables sign in for GitHub
    - GitHub sign-in is needed for [contributing to Community hub](community-hub-contribute) but not for downloading items.

Important

- When you upgrade to Configuration Manager 2107, you will be prompted to install the WebView2 console extension again.
- Configuration Manager versions 2006 and earlier can’t sign in to GitHub but can still download items. Using Community hub on Windows Server requires the WebView2 console extension and Configuration Manager version 2010 or later.

Follow the instructions below to enable the full functionality of Community hub:

1. In the upper-right corner of the console, select the bell icon to display Configuration Manager console notifications.

    ![Notifications in the Configuration Manager console](media/3555909-notification.png)
2. The notification will say **New custom console extensions are available**.

    ![New custom console extensions are available notification](media/3555909-extension-notification.png)
3. Select the link **Install custom console extensions** to launch the install.
4. When the install completes, select **Close** to restart the console.

    ![Console extension completed install](media/3555909-extension-installed.png)
5. Confirm that you can view the **Community hub** node from the machine running the Windows Server operating system.

    - You may also notice that a new folder `AdminConsole\bin\Microsoft.WebView2.FixedVersionRuntime.<version>.x86` was created.
    - The files are automatically downloaded from https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section with the other redistributable files.

Tip

Starting in Configuration Manager version 2103, you can also install the WebView2 extension from the **Console Extensions** node. For more information, see [Install an extension on a local console](admin-console-extensions#bkmk_local_install).

## Known issues

### Community hub doesn't load

The Community hub may not load, or load after a long delay if the WebView2 console extension hasn't been installed. For more information about installing console extensions, see the Install the WebView2 console extension and [Managing console extensions (starting in version 2103)](admin-console-extensions).

### Unhandled exception occurs when loading Community hub

In certain circumstances, you may encounter the following exception when loading Community hub:

`Could not load type 'System.Runtime.InteropServices.Architecture' from assembly 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.`

**Workaround**: To work around this issue, update the .NET Framework to version 4.7.1 or later for the machine running the Configuration Manager console.

### Unable to access Community hub node when running console as a different user

If you're signed in as a user with lower rights and choose **Run as** a different user to open the Configuration Manager console, you may not be able to access the **Community hub** node.

### Downloaded reports don't get removed from your downloads page

If you delete a downloaded report from the **Monitoring** &gt; **Reports** node, the report isn't deleted from the **Community hub** &gt; **Your downloads** page and you're unable to download the report again.

### Unable to download baseline that contains a previously downloaded configuration item

If you previously downloaded a configuration item from Community hub using Configuration Manager 2010, you may receive an error when downloading a baseline after upgrading to Configuration Manager version 2103. A download error can occur when the baseline contains an updated version of the configuration item you previously downloaded with Configuration Manager 2010.

**Workaround**: To work around this issue, delete the configuration item you previously downloaded, then download the baseline with the new version of the configuration item.

### Unable to sign in when single sign on with multifactor authentication is used

When single sign on with multifactor authentication is used, you may not be able to sign in for the following features when using Configuration Manager 2103 and earlier:

- Community hub
- Community hub from CMPivot
- Custom tabs in Software Center that load a website that's subject to Conditional Access policies