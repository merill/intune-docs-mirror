---
layout: Conceptual
title: Collections prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/prerequisites-for-collections
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
description: Get prerequisites for using collections in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f1248341-eb2c-0c21-a908-fae7d9eae627
document_version_independent_id: 2f586dd3-8c4f-0ad5-9be4-6b17602ac9e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/prerequisites-for-collections.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/prerequisites-for-collections
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/prerequisites-for-collections.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: baaba477-8879-45ca-3073-cf5c68ae60a8
---

# Collections prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Collections in Configuration Manager contain only dependencies within the product.

## Configuration Manager dependencies

| Dependency | More information |
| --- | --- |
| Reporting services point | The reporting services point site system role must be installed before you can run reports for collections. For more information, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting). |
| Specific security permissions must have been granted to manage collections | You must have the following security permissions to manage compliance settings: - To create and manage collections: **Create**, **Delete**, **Modify**, **Modify Folder**, **Move Object**, **Read** and **Read Resource** for the **Collection** Object. - To manage collection settings: **Modify Collection Setting** for the **Collection** Object. The **Modify Folder** permission is required for all collection folders, including the root folder. |