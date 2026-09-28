---
layout: Conceptual
title: International support - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/international-support
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
description: Configure Configuration Manager to comply with specific international requirements.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 669b7daa-5735-1250-0809-18062b01c61a
document_version_independent_id: eacd7da7-83db-65e7-4ff6-0b2bb20473cc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/international-support.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/international-support
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/international-support.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 980a62d4-79ab-7530-3735-a0bb244e3e8c
---

# International support - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The following sections provide technical details to help you make Configuration Manager compliant with specific international requirements.

## GB18030 Requirements

Configuration Manager meets the standards that are defined in GB18030 so that you can use Configuration Manager in China. A Configuration Manager deployment must have the following configurations to meet the GB18030 requirements:

- Each site server computer and SQL Server computer that you use with Configuration Manager must use a Chinese operating system.
- Each site database and each instance of SQL Server in the hierarchy must use the same collation, and must be one of the following:

    - Chinese\_Simplified\_Pinyin\_100\_CI\_AI
    - Chinese\_Simplified\_Stroke\_Order\_100\_CI\_AI

    Note

    These database collations are an exception to the requirements that are noted in [Supported configurations for SQL Server](../configs/supported-configurations-for-sql-server).
- You must place a file with the name **GB18030.SMS** in the root folder of the system volume of each site server computer in the hierarchy. This file does not contain any data and can be an empty text file that is named to meet this requirement.