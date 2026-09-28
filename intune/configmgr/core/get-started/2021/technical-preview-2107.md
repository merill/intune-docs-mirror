---
layout: Conceptual
title: Technical preview 2107 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2107
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2107.
ms.date: 2021-07-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 52cb6c30-2c36-2eb6-2cd5-eae240c9d262
document_version_independent_id: 21b37f1b-8f0f-2b5e-4094-37e80dcf19dd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2107.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2107
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2107.md
platformId: 0329a41b-efdc-a406-537e-00f6897fad67
---

# Technical preview 2107 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2107. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Tenant attach: Software updates information

There's a new **Software updates** page for tenant attached devices. This page displays the status for software updates on a device. You can review which updates are successfully installed, failed, and are assigned but not yet installed. Using the timestamp for the update status assists with troubleshooting.

The following actions are available on the **Software update** page for a tenant attached device:

- **Search**: You can search using either a full or partial string in all columns except **Status time**.
- **Sort**: Sort a column by using the arrows after the column name. The default sort order is by **Status time**.
- **Refresh**: Retrieves updated information for the device from the Configuration Manager environment.
- **Export**: Exports all of the available data for the device to a `.csv` file.

[![Screenshot of the software updates page for a tenant attached device](media/6024419-software-updates.png)](media/6024419-software-updates.png#lightbox)

## Publish query to Community hub from CMPivot

You can now publish a CMPivot query to the Community hub directly from the CMPivot window. Submitting your queries directly through CMPivot makes contributing to the Community hub easier.

### Prerequisites:

- Meet all of the [CMPivot prerequisites and permissions](../../servers/manage/cmpivot#prerequisites)
- Enable [Community hub](../../servers/manage/community-hub).
    - If needed, install the Microsoft Edge WebView2 extension from the [Configuration Manager console notification](../../servers/manage/community-hub#bkmk_webview2).
- A GitHub account that's [joined to Community hub](../../servers/manage/community-hub-contribute#join-the-community-hub-to-contribute-content)
    - You must accept the invitation sent in the email otherwise you won't be able to contribute content.

#### Use CMPivot to publish a query to the Community hub

1. Go to the **Assets and Compliance** workspace then select the **Device Collections** node.
2. Select a target collection, target device, or group of devices then select **Start CMPivot** in the ribbon to launch the tool.
3. From the CMPivot window, select the Community hub icon on the menu.

    ![Community hub icon](../../servers/manage/media/7137169-hub-icon.png)
4. Select **Sign in**, then sign in to GitHub.
5. Create a [query](../../servers/manage/cmpivot-overview), then select **Run Query** to verify it functions as expected.

    - Optionally, select the folder icon to access your favorites list to use a query you've already created.
6. Select the **Publish** link at top of CMPivot's Community hub window when you're ready to submit your query. ![Screenshot of the Community hub window in CMPivot showing the publishing tab](media/9965423-publish.png)
7. Give your query a **Name** and **Description**, then select the **Publish** button to send your query to the Community hub.
8. Once the contribution is complete, you can access your query anytime from the **Me** tab.
9. To view the GitHub pull request (PR), go to https://github.com/Microsoft/configmgr-hub/pulls. You can also access the PR link from the **Your hub** page in the **Community hub** node.

    - PRs shouldn't be submitted directly to the GitHub repository.

Note

Community hub is only available in CMPivot when you run it from the Configuration Manager console. Community hub isn't available from [standalone CMPivot](../../servers/manage/cmpivot#install-cmpivot-standalone).