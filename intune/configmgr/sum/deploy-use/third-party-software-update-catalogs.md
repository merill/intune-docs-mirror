---
layout: Conceptual
title: Available third-party software update catalogs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/third-party-software-update-catalogs
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
description: List of third-party update catalogs available for import into Configuration Manager
ms.date: 2024-04-18T00:00:00.0000000Z
ms.subservice: software-updates
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 675af475-6082-11d4-8540-daf0c6f1636e
document_version_independent_id: 6b484365-3805-5c3f-cafb-7163066f1219
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/third-party-software-update-catalogs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/third-party-software-update-catalogs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/third-party-software-update-catalogs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7ddd0ba-08b8-4055-8ab8-0da61f3dfbb3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/5cf7e60a-ca26-4c6f-befd-5e90eae977f5
platformId: 41b7faad-03ef-72bb-f9e8-0037e8b0f9c0
---

# Available third-party software update catalogs - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The **Third-Party Software Update Catalogs** node in the Configuration Manager console allows you to subscribe to third-party catalogs, publish their updates to your software update point (SUP), and then deploy them to clients. You can [add custom catalogs](third-party-software-updates#add-a-custom-catalog) from third-party vendors.

## Third-party update catalogs available for import

To make it easier to find custom catalogs, we're providing a list of links as a convenience. Some catalogs are freely available and some catalogs have an additional cost associated with them. This list includes catalogs that may only work with [System Center Updates Publisher](../tools/updates-publisher) and not the **Third-Party Software Update Catalogs** node in the Configuration Manager console. Check with the catalog provider for details including pricing, support, and if the catalog supports in-console third-party updates.

| Custom catalog provider | URL |
| --- | --- |
| Adobe | Multiple catalogs are available from Adobe. https://www.adobe.com/devnet-docs/acrobatetk/tools/DesktopDeployment/sccm.html |
| Centero Software Manager | https://docs.software-manager.com/docs/csm-for-sccm |
| Dell | *Partner catalog* available in the **Third-Party Software Update Catalogs** node https://www.dell.com/support/article/sln311138/https://downloads.dell.com/Catalog/DellSDPCatalogPC.cabhttps://downloads.dell.com/Catalog/DellSDPCatalog.cab |
| Fujitsu | https://support.ts.fujitsu.com/GFSMS/globalflash/FJSVUMCatalogForSCCM.cab |
| HP | *Partner catalog* available in the **Third-Party Software Update Catalogs** node https://hpia.hpcloud.hp.com/downloads/sccmcatalog/HpCatalogForSms.latest.cab`http://ftp.hp.com/pub/softlib/software/sms_catalog/HpCatalogForSms.latest.cab` |
| Ivanti Patch for MEM | https://www.ivanti.com.au/products/patch-management-for-mem |
| Lenovo | *Partner catalog* available in the **Third-Party Software Update Catalogs** node https://download.lenovo.com/luc/v3/LenovoUpdatesCatalogv3.cab Lenovo updates catalog V3 information https://thinkdeploy.blogspot.com/2020/06/lenovo-updates-catalog-v3-for-sccm.html Lenovo Patch https://www.lenovo.com/us/en/software/lenovo-patch-sccm |
| ManageEngine Patch Connect Plus | https://www.manageengine.com/sccm-third-party-patch-management |
| Patch My PC | Full catalog https://patchmypc.com/third-party-patch-management-for-sccm-and-intune Limited catalog https://patchmypc.com/frequently-asked-questions#trial-catalog |
| SolarWinds Patch Manager | https://www.solarwinds.com/patch-manager/use-cases/third-party-patch-management-sccm |

## Open this article from the Configuration Manager console

Starting in Configuration Manager 2107, you can choose **More Catalogs** from the ribbon in the **Third-party software update catalogs** node to get to this article. Right-clicking on **Third-Party Software Update Catalogs** node displays a **More Catalogs** menu item. Selecting **More Catalogs** opens a link to this page.

![Screenshot of the Third-Party Software Update Catalogs node with the More Catalogs icon in the ribbon](media/9989251-more-catalogs.png)