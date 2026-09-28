---
layout: Conceptual
title: View software inventory with Resource Explorer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory
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
description: Use Resource Explorer to view software inventory in Configuration Manager.
ms.date: 2020-04-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 12c9f632-8479-2e14-803b-da7cf1ff3624
document_version_independent_id: 2d4994c2-3a84-9f76-928f-49e2faef6d5a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 595f2a9f-e854-a85b-aaba-b023e5e98914
---

# View software inventory with Resource Explorer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use Resource Explorer in Configuration Manager to view information about software inventory that has been collected from computers in your hierarchy.

Note

Resource Explorer will not display any inventory data until a software inventory cycle has run on the client.

Resource Explorer provides the following software inventory information:

- **Software**:

    - **Collected Files** - Files that were collected during software inventory.
    - **File Details** - Files that were inventoried during software inventory that are not associated with a specific product or manufacturer.
    - **Last Software Scan** - Date and time of the last software inventory and file collection for the client computer.
    - **Product Details** - Software products that were inventoried by software inventory, grouped by manufacturer.

## To run Resource Explorer from the Configuration Manager console

1. In the Configuration Manager console, choose **Assets and Compliance**
2. In the **Assets and Compliance** workspace, choose **Devices** or open any collection that displays devices.
3. Choose the computer containing the inventory that you want to view and then, in the **Home** tab &gt; **Devices** group, choose **Start** &gt; **Resource Explorer**.
4. You can right-click any item in the right-pane of the Resource Explorer window and choose **Properties** to view the collected inventory information in a more readable format.

## View and manage collected diagnostic files

Starting in Configuration Manager version 2002, use Resource Explorer to view and manage the files gathered when you use client notification to [collect client logs](../client-notification#client-diagnostics).

1. From the **Devices** node, right-click on the device you want to view logs for.
2. Select **Start**, then **Resource Explorer**.
3. From **Resource Explorer**, click on **Diagnostic Files**.
4. In the **Diagnostic Files** list, you can see the collection date for the files. The name format of the client logs is `Support_<guid>.zip`.
5. Right-click on the zip file and select one of the following options:
    - **Open Support Center**: Launches [Support Center](../../../support/support-center).
    - **Copy**: Copies the row information from Resource Explorer.
    - **View file**: Opens the folder where the zip file is located with File Explorer.
    - **Save**: Opens a Save File dialog for the selected file.
    - **Export**: Saves the Resource Explorer columns shown in **Diagnostic Files**.
    - **Refresh**: Refreshes the file list.
    - **Properties**: Returns the properties on the selected file.

[![Review and save client logs from Resource Explorer](../media/4226618-view-collected-client-logs.png)](../media/4226618-view-collected-client-logs.png#lightbox)