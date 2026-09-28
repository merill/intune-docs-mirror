---
layout: Conceptual
title: Asset intelligence deprecation - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/deprecation
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
description: More information about the deprecation of the asset intelligence feature of Configuration Manager.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a2f873ba-362b-8f9f-0e4a-491c5f98665b
document_version_independent_id: a2f873ba-362b-8f9f-0e4a-491c5f98665b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/deprecation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/deprecation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/deprecation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 889edcde-52b2-10cf-fea3-b2baf47d7e2e
---

# Asset intelligence deprecation - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in November 2021, the asset intelligence feature of Configuration Manager is [deprecated](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). This article provides more detail about the specific functional areas of asset intelligence that are deprecated or still supported.

## Deprecated functionality

The following functional areas are deprecated and may be removed in a future version. Support for these areas will end November 2022.

- The [asset intelligence catalog](introduction-to-asset-intelligence#BKMK_AssetIntelligenceCatalog), which includes the following functionality:

    - Cloud updates to the predefined software title information such as product name and vendor
    - Cloud updates to the predefined [software categories](introduction-to-asset-intelligence#BKMK_SoftwareCategories) and [software families](introduction-to-asset-intelligence#BKMK_SoftwareFamilies) and the associated SQL views and reports
    - Cloud updates to the predefined [hardware requirements](introduction-to-asset-intelligence#BKMK_HardwareRequirements) for software titles and the associated SQL views and reports
- The [asset intelligence synchronization point](introduction-to-asset-intelligence#AssetIntelligenceSycnronizationPoint), which includes the following functionality:

    - Catalog synchronization
    - The ability to [request catalog updates](operations-for-asset-intelligence#BKMK_RequestCatalogUpdate) for uncategorized software
- The [Microsoft Volume License import and reconciliation](configuring-asset-intelligence#BKMK_ImportSoftwareLicenseInformation) including the associated SQL views and reports

## Supported functionality

The following functional areas aren't currently included in the deprecation and will remain supported:

- The [inventoried software titles](introduction-to-asset-intelligence#BKMK_InventoriedSoftwareTitles), which includes the following functionality:

    - [Asset intelligence hardware inventory reporting WMI classes](../../../../develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes)
    - The associated SQL views:

        - [Asset intelligence hardware inventory views](../../../../develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager#asset-intelligence-hardware-inventory-views)
        - [Asset intelligence status view](../../../../develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager#asset-intelligence-status-view)
    - The associated reports
- The [product lifecycle dashboard](product-lifecycle-dashboard) and its associated reports
- The [General License Statement import and reconciliation](configuring-asset-intelligence#BKMK_CreateGeneralLicenseStatement) and the associated SQL views and reports
- The ability to view the asset intelligence inventory in the console from the **Inventoried Software** node
- The existing static, predefined software title information provided with setup for new and existing sites:

    - Product name
    - Vendor
    - Product category
    - Product family
    - Hardware requirement
- The ability to customize the inventoried software title information such as the product name and vendor
- The ability to add custom software categories, families, and labels to inventoried software titles
- The ability for an administrator to add custom hardware requirements to inventoried software titles

## References

[Asset intelligence reports](../../../servers/manage/list-of-reports#asset-intelligence)

[Asset intelligence client WMI classes](../../../../develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes)

[Asset intelligence views](../../../../develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager)