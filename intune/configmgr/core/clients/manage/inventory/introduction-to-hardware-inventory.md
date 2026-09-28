---
layout: Conceptual
title: Hardware inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory
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
description: Understand the basics of hardware inventory in Configuration Manager.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 9fc66e45-9e0b-a8f0-b231-09639b6fdd3f
document_version_independent_id: 36eea4d4-2e44-b711-091a-97c98b8125d4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory.md
cmProducts: []
platformId: fe4515e3-7239-cf14-cfb9-4414e9ac1314
---

# Hardware inventory - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use hardware inventory in Configuration Manager to collect information about the hardware configuration of client devices in your organization. To collect hardware inventory, you must select the **Enable hardware inventory on clients** setting in client settings.

After hardware inventory is enabled and the client runs a hardware inventory cycle, the client sends the information to a management point in the client's site. The management point then forwards the inventory information to the Configuration Manager site server, which stores the inventory information in the site database. Hardware inventory runs on clients according to the schedule that you specify in client settings.

## View hardware inventory

You can use several methods to view the hardware inventory data that Configuration Manager collects:

- [Create queries that return devices that are based on a specific hardware configuration](../../../servers/manage/introduction-to-queries).
- [Create query-based collections that are based on a specific hardware configuration](../collections/introduction-to-collections). Query-based collection memberships automatically update on a schedule. You can use collections for several tasks, including software deployment.
- [Run reports that display specific details about hardware configurations in your organization](../../../servers/manage/introduction-to-reporting).
- [Use Resource Explorer](use-resource-explorer-to-view-hardware-inventory) to view detailed information about the hardware inventory that's collected from client devices.

When hardware inventory runs on a client device, the first inventory data that the client returns is always a full inventory. The next set of inventory data contains only delta inventory information. The site server processes delta inventory information in the order received. If delta information for a client is missing, the site server rejects more delta information and directs the client to run a full inventory cycle.

Configuration Manager provides limited support for dual-boot computers. Configuration Manager can discover dual-boot computers but returns inventory information only from the OS that's active when the inventory cycle runs.

## Extend inventory

To collect more information than what Configuration Manager inventories by default, you can also use one of these methods to extend hardware inventory:

- Enable, disable, add, and remove inventory classes for hardware inventory from the Configuration Manager console.
- Use NOIDMIF files to collect information about client devices that can't be inventoried by Configuration Manager. For example, you might want to collect device asset number information that exists only as a label on the device. NOIDMIF inventory is automatically associated with the client device that it was collected from.
- Use IDMIF files to collect information about assets that aren't associated with a Configuration Manager client, for example, projectors, photocopiers, and network printers.
- Starting in version 2107, you can use the administration service to set custom properties on devices. You can then use the custom properties in Configuration Manager for reporting or to create collections. For more information, see [Custom properties for devices](../../../../develop/adminservice/custom-properties).