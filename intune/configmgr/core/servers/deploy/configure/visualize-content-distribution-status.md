---
layout: Conceptual
title: Visualize content distribution status - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/visualize-content-distribution-status
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
description: Monitor content distribution path and status in a graphical format, to help you more easily understand the status of your content package distribution.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f1cfbe2f-ba7a-ba50-bbbe-55d7dc310072
document_version_independent_id: f1cfbe2f-ba7a-ba50-bbbe-55d7dc310072
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/visualize-content-distribution-status.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/visualize-content-distribution-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/visualize-content-distribution-status.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6c8144a4-d434-98b0-680b-763f13b9e6d8
---

# Visualize content distribution status - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in version 2203, you can monitor content distribution path and status in a graphical format. The graph shows distribution point type, distribution state, and associated status messages. This visualization allows you to more easily understand the status of your content package distribution. It helps you answer questions like:

- Has the site successfully distributed the content?
- Is the content distribution in progress?
- Which distribution points have already processed the content?

![Visualization of content distribution status of the Configuration Manager client package in an example hierarchy.](media/9495651-view-content-distribution.png)

This example shows a graph for the content distribution status of the Configuration Manager client package in an example hierarchy. It lets you easily see the following information:

- The solid blue line from the site server to each distribution point indicates that the rate limit is **Unlimited**. For more information, see [Rate limits](install-and-configure-distribution-points#bkmk_config-rate).
- The green check mark on `DP01` and `DP02` indicates that the content was successfully distributed to these site systems.
- The red `X` on `DP03` and both cloud distribution points indicates that there's an error in distributing the content to these site systems.

## View content distribution

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand **Distribution Status** and select the **Content Status** node.
2. If this node doesn't show anything, first [distribute content](deploy-and-manage-content#bkmk_distribute).
3. Select a distributed content item. For example, the **Configuration Manager client package**.
4. In the ribbon, select **View Content Distribution**. This action displays the distribution graph for the selected content.

    - Hover over the status icon to quickly view more information. Select the path or the status icon to view status messages for the content.
    - Hover over the title of the site system to quickly view more information. Select it to drill through to the **Distribution Points** node.

## Navigation tips

Use the following tips to navigate the relationship viewer:

- Select the plus (`+`) or minus (`-`) icons next to the server name to expand or collapse members of a node.
- The style and color of the line between the servers determines the type of distribution. If you hover over a specific line, a tooltip shows the type.
- The maximum number of child nodes displayed depends upon the level of the graph:

    - First level: five nodes
    - Second level: three nodes
    - Third level: two nodes
    - Fourth level: one node

    If there are more objects than the graph can display at that level, you'll see the **More** icon.
- When the size of the tree is larger than the window, use the green arrows to view more.
- When a node of the tree is larger than the available space, select **More** to change the view to just that node.
- To navigate to a prior view, select the **Back** arrow. Select the **Home** icon to return to the main page.
- Use the **Search** box to locate a server in the current tree view.
- Use the **Navigator** to zoom and pan around the tree. You can also print the current view.

Tip

Hold the **Ctrl** key and scroll the mouse wheel to zoom the graph.

For more information on how to navigate the graph with a keyboard, see [Accessibility features](../../../understand/accessibility-features#collection-relationship-diagram-shortcuts) for the collection relationship diagram.