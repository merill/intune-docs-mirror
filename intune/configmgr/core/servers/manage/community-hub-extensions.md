---
layout: Conceptual
title: Console extensions from Community hub - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/community-hub-extensions
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
description: Learn about managing Community hub console extensions for Configuration Manager
ms.date: 2022-10-31T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 099100d7-a9f7-7657-e469-527f6fbe1403
document_version_independent_id: 1b98fd90-3f06-a85a-3109-0bdd4f5ede3e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/community-hub-extensions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/community-hub-extensions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/community-hub-extensions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 904ba9f3-05ca-8b5c-a42b-80c27a5ee748
---

# Console extensions from Community hub - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in March 2023, this feature of Configuration Manager is being removed. All future versions, starting with 2303 will not have the Community hub node in the admin console. The Community hub node in older versions will be redirected to [deprecated features](../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

When you use Configuration Manager version 2103 or later, you can download console extensions from the [Community hub](community-hub) and have it applied to all consoles connected to a hierarchy. The **Console extensions** node allows you to start managing the approval and installation of console extensions used in your environment. Getting an extension from community hub doesn't make it immediately available. First, an administrator has to approve the extension for the site. Then console users can install the extension to their local console.

After you approve an extension, when you open the console, you'll see a console notification. From the notification, you can start the extension installer. After the installer completes, the console restarts automatically, and then you can use the extension. 

## Find extensions in Community hub

Extensions in Community hub are recognizable by their icon. When browsing **All objects** in the Community hub, you can easily notice if a new extension has been added.The following icon is used for extensions:

![Screenshot of the extension icon used in Community hub. A teal square is surrounded by a broken outline of a square in gray and purple.](media/3555909-extension-icon.png)

You can also use a search filter to find an extension in Community hub. Start with the search filter for `type:extension`, then add additional filters as needed. If you're not finding an extension that's known to be available, double check the [displayed categories hierarchy setting](community-hub#bkmk_category) for Community hub.

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

## Download and deploy the extension

You'll download the extension from Community hub, then use the **Console Extensions** node to test the extension and deploy it to other Configuration Manager console users. In-depth instructions for the deployment process and managing extensions can be found in the [Console Extensions](admin-console-extensions) article. Below is a high-level overview of the extension deployment process:

1. Once you've found an extension in Community hub that you want in your environment, select **Download**.
2. The downloaded extension will appear in the [**Console Extensions**](admin-console-extensions) node.
3. Change the security scope for the extension, approve it, then install and test it on a local console. For more information on this process, see [Install and test an extension on a local console](admin-console-extensions#bkmk_local_install).
4. When testing is complete, [enable user notifications](admin-console-extensions#bkmk_enable-notifications) for installation.

## Console extension installation notifications

Users are notified when console extensions are approved for installation. These notifications occur for users in the following scenarios:

- The Configuration Manager console requires a built-in extension, such as WebView2, to be installed or updated.
- Console extensions are approved and notifications are enabled from **Administration** &gt; **Overview** &gt; **Updates and Servicing** &gt; **Console Extensions**.
    - When notifications are enabled, users within the [security scope](../../understand/fundamentals-of-role-based-administration#security-scopes) for the extension receive the following prompts:

1. In the upper-right corner of the console, select the bell icon to display Configuration Manager console notifications.

    ![Notifications in the Configuration Manager console](media/3555909-notification.png)
2. The notification will say **New custom console extensions are available**.

    ![New custom console extensions are available notification](media/3555909-extension-notification.png)
3. Select the link **Install custom console extensions** to launch the install.
4. When the install completes, select **Close** to restart the console and enable the new extension.

    ![Console extension completed install](media/3555909-extension-installed.png)

Note

When you upgrade to Configuration Manager 2107, you will be prompted to install the WebView2 console extension again. For more information about the WebView2 installation, see the [WebView2 installation](community-hub#bkmk_webview2) section if the Community hub article.