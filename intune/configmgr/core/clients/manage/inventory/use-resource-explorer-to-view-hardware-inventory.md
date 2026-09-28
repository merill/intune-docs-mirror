---
layout: Conceptual
title: How to use Resource Explorer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory
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
description: Use Resource Explorer to view hardware inventory in Configuration Manager.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f58362c2-c020-87e8-421b-80386d3c134c
document_version_independent_id: 8c7d3aad-3441-4718-a83f-a25f392d2c7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md
cmProducts: []
platformId: 8efe941b-e7b2-128e-3245-def2c0647004
---

# How to use Resource Explorer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use Resource Explorer in Configuration Manager to view information about hardware inventory. The site collects this information from clients in your hierarchy.

Tip

Resource Explorer doesn't display any data until a hardware inventory cycle runs on the client to which you're connecting.

## Overview

Resource Explorer has the following sections related to hardware inventory:

- **Hardware**: Shows the most recent hardware inventory collected from the specified client device.

    - The **Workstation Status** node shows the time and date of the last hardware inventory from the device.
- **Hardware History**: A history of inventoried items that changed since the last hardware inventory cycle.

    - Expand an item to see a **Current** node and one or more nodes with the historical date. Compare the information in the current node to one of the historical nodes to see the items that changed.

Note

By default, Configuration Manager deletes hardware inventory data that's been inactive for 90 days. Adjust this number of days in the **Delete Aged Inventory History** site maintenance task. For more information, see [Maintenance tasks](../../../servers/manage/maintenance-tasks).

## How to open Resource Explorer

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node. You can also select any collection in the **Device Collections** node.
2. Select a device. In the ribbon, on the **Home** tab and **Devices** group, click **Start**, and then select **Resource Explorer**.

Tip

In Resource Explorer, right-click an item in the right results pane for additional actions. Click **Properties** to view that item in a different format.

## Use of large integer values

In Configuration Manager versions 1802 and prior, hardware inventory has a limit for integers larger than 4,294,967,296 (2^32). This limit can be reached for attributes such as hard drive sizes in bytes. The management point doesn't process integer values above this limit, so no value is stored in the database.

Starting in version 1806, the limit is increased to 18,446,744,073,709,551,616 (2^64).

For a property with a value that doesn't change, like total disk size, you may not immediately see the value after upgrading the site. Most hardware inventory is a delta report. The client only sends values that change. To work around this behavior, add another property to the same class. This action causes the client to update all properties in the class that changed.