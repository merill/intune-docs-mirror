---
layout: Conceptual
title: Accessibility - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/accessibility-features
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
description: Learn about the features that make Configuration Manager accessible for everyone.
ms.date: 2021-07-21T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection:
- tier3
- essentials-accessibility
locale: en-us
document_id: 3c716226-0e14-c71e-3a72-7f6836ef2744
document_version_independent_id: 3d23cfa7-8631-e6d4-af80-b5911eb9a19b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/accessibility-features.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/accessibility-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/accessibility-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: a58c6684-4198-3691-61be-16b167105bac
---

# Accessibility - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager includes features to help make it accessible for everyone.

Note

To improve the accessibility features of the Configuration Manager console, update .NET to version 4.7 or later on the computer running the console. 

For more information on the accessibility changes made in .NET 4.7.1 and 4.7.2, see [What's new in accessibility in the .NET Framework](/en-us/dotnet/framework/whats-new/whats-new-in-accessibility).

## Keyboard shortcuts

### Console workspaces

To access a workspace, use the following keyboard shortcuts:

| Keyboard shortcut | Workspace |
| --- | --- |
| `Ctrl` + `1` | Assets and Compliance |
| `Ctrl` + `2` | Software Library |
| `Ctrl` + `3` | Monitoring |
| `Ctrl` + `4` | Administration |

### Other console shortcuts

| Keyboard shortcut | Purpose |
| --- | --- |
| `Ctrl` + `M` | Set the focus on the main (central) pane. |
| `Ctrl` + `T` | Set the focus to the top node in the navigation pane. If the focus was already in that pane, the focus is set to the last node you visited. |
| `Ctrl` + `I` | Set the focus to the breadcrumb bar, below the ribbon. |
| `Ctrl` + `L` | Set the focus to the **Search** field, when available. |
| `Ctrl` + `D` | Set the focus to the details pane, when available. |
| `Alt` | Change the focus in and out of the ribbon. |

### CMPivot shortcuts

Most [web browser keyboard shortcuts](https://support.microsoft.com/topic/internet-explorer-ease-of-access-options-037270c1-db10-7ca8-ccba-ebd83ea6ace9) will work in [CMPivot](../servers/manage/cmpivot-overview).

| Keyboard shortcut | Purpose |
| --- | --- |
| `Ctrl` + `1` | Set the focus on the first tab. |
| `Alt` + `<` | To back to the address |

### Collection relationship diagram shortcuts

When you [view collection relationships](../clients/manage/collections/view-relationships) in the Configuration Manager console, use the **TAB** key to change the focus. By default, the focus is on the page number controls. When the focus is on the graph itself (navigator), use the following keyboard shortcuts to navigate:

| Navigator shortcut | Purpose |
| --- | --- |
| `Ctrl` + `W` | Scroll up |
| `Ctrl` + `S` | Scroll down |
| `Ctrl` + `A` | Scroll left |
| `Ctrl` + `D` | Scroll right |
| `Ctrl` + `+` | Zoom in |
| `Ctrl` + `-` | Zoom out |

Use the following keyboard shortcuts to quickly move focus to different areas of the window:

| Keyboard shortcut | Purpose |
| --- | --- |
| `Alt` + `P` | Dependent page |
| `Alt` + `B` | Back |
| `Alt` + `H` | Home |
| `Alt` + `N` | Collection name |
| `Alt` + `T` | Filter |

## Other accessibility features

- To navigate the navigation pane, type the letters of a node name.
- Keyboard navigation through the main view and the ribbon is circular.
- Keyboard navigation in the details pane is circular. To return to the previous object or pane, use `Ctrl` + D, then Shift + TAB.
- After refreshing a Workspace view, the focus is set to the main pane of that workspace.
- To access a workspace menu, select the Tab key until the Expand/Collapse icon is in focus. Then, select the Down arrow key to access the workspace menu.
- To navigate through a workspace menu, use the arrow keys.
- To access different areas in the workspace, use the Tab key and Shift+Tab keys. To navigate within an area of the workspace, such as the ribbon, use the arrow keys.
- To access the address bar when your focus is in the tree node, use Shift+Tab three times.
- On a wizard or property page, you can move between the boxes with keyboard shortcuts. Select the Alt key plus the underlined character (Alt+\_) to select a specific box.
- To navigate to the different nodes of a workspace, enter the first letter of the name of a node. Each key press moves the cursor to the next node that begins with that letter. When you're using a screen reader, the reader reads out the name of that node.