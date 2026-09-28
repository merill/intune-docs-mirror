---
layout: Conceptual
title: Tenant attach - Resource explorer the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/resource-explorer
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
description: View hardware inventory for uploaded Configuration Manager devices using resource explorer in the admin center.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 142143a8-2eb3-4414-b944-a707b991e033
document_version_independent_id: b41d271d-1b5d-3202-250b-81846d19328d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/resource-explorer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/resource-explorer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/resource-explorer.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6728dcc0-bc2b-5945-8a8c-d181ee5e6ec7
---

# Tenant attach - Resource explorer the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. From the Microsoft Endpoint Management admin center, you can view hardware inventory for uploaded Configuration Manager devices by using resource explorer.

[![Resource explorer in Microsoft Intune admin center](media/6479284-resource-explorer.png)](media/6479284-resource-explorer.png#lightbox)

## Prerequisites

The following items are required to use resource explorer from the admin center:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details).
- A supported version of Configuration Manager version and the corresponding version of the console installed.
    - Historical inventory data requires Configuration Manager version 2103, or later.
- Upgrade the target devices to the latest version of the Configuration Manager client.

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission for the device's **Collection** in Configuration Manager.
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

## Launch resource explorer

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Resource explorer** to view hardware inventory.
5. Search for or select a class to retrieve information from the client.

    [![Resource explorer with the motherboard class selected](media/6479284-resource-explorer-details.png)](media/6479284-resource-explorer-details.png#lightbox)

## Historical inventory data in resource explorer

*Applies to Configuration Manager 2103, or later*

Resource explorer can display a historical view of the device inventory in the Microsoft Intune admin center. When troubleshooting, having historical inventory data can provide valuable information about changes to the device.

1. From the Microsoft Intune admin center, select **Resource explorer**.
2. Select a class.
3. Enter a custom date in the date time picker to get historical inventory data.

[![Screenshot of choosing a date from Resource explorer in the Microsoft Intune admin center ](media/9546584-resource-explorer-historical-inventory.png)](media/9546584-resource-explorer-historical-inventory.png#lightbox)

## Close resource explorer

To close resource explorer and return to the device information, use the `X` icon in the top right of resource explorer.

[![Close resource explorer with the x icon in Microsoft Intune admin center](media/6479284-close-resource-explorer.png)](media/6479284-close-resource-explorer.png#lightbox)