---
layout: Conceptual
title: Configuration Manager Console Nodes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes
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
description: Learn how to use XML to define nodes and their content, which you see in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 97f7bce3-95f4-5311-c29f-1a7a5ac29bdc
document_version_independent_id: 88950677-4a12-aca3-74e8-d8986f27ad5c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/about-configuration-manager-console-nodes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 151bfedc-4e55-6c80-18c4-7cb92ab4f553
---

# Configuration Manager Console Nodes - Configuration Manager | Microsoft Learn

Configuration Manager uses XML to define the nodes and their content, that you see in the Configuration Manager console. New nodes can be added anywhere in the existing node hierarchy.

The XML for a node describes the navigation pane, results pane, and action pane, and the resources that are needed by each pane to display the node.

When writing a new node, consider the following:

- **The position of the node in the hierarchy.** Each node is uniquely identified by a GUID. For an example, see [How to Create a Configuration Manager Administrator Console Node](how-to-create-a-configuration-manager-console-node).
- **The node hierarchy.** The node structure is hierarchical, and you can nest nodes as deeply as you require. You can also use regular expressions to determine whether a node should be displayed. For an example, see [How to Create a Configuration Manager Administrator Console Node](how-to-create-a-configuration-manager-console-node).
- **Actions.** You can define actions that the user selects in the Configuration Manager console. You can use an action to launch forms, run programs, call methods, show reports, and define action menus. For more information, see [Configuration Manager Actions](configuration-manager-actions).
- **Queries.** You can define queries that populate the navigation pane and results pane with SMS Provider objects. You can specify regular expressions to pick the properties that are displayed from the objects queried. For an example, see [Configuration Manager Administrator Console RootNodes Element](console-rootnodes-element).
- **Security.** You can secure a node based on security flags that you specify. For an example that sets security for an action, see [Configuration Manager Conditional Actions](conditional-actions).
- **Views.** You can launch views in the Configuration Manager console at desired nodes. For more information about views, see [About console views](about-configuration-manager-console-views).

Note

The Configuration Manager SDK includes a sample XML file and GUID folder for a node that displays the available collections. The GUID folder is the namespace identifier for the tools node

For information about node XML, see [Configuration Manager Console Node XML](console-node-xml).