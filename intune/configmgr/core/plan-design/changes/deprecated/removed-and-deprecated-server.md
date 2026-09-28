---
layout: Conceptual
title: Deprecated for site servers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-server
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
description: Learn about the products and operating systems that Configuration Manager no longer supports for site servers and database servers.
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 3c66fedb-44e0-9dd4-f26d-cd895b9058ae
document_version_independent_id: 6fe80668-7df6-63a0-c2db-4280aa30b477
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-server.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e7da69c0-ccd8-dc0a-905e-37251dbdcfa8
---

# Deprecated for site servers - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article describes products and operating systems that are removed from support for Configuration Manager site servers, or will be removed in a future update (deprecated). It provides early notice about future changes that might affect your use of Configuration Manager.

This information may change in the future. It might not include each deprecated feature, product, or OS.

## Client OS

| Operating systems | Deprecation first announced | Support removed |
| --- | --- | --- |
| Windows 10 22H2 | Oct 2021 | Version 2509 |

## Server OS

| Operating systems | Deprecation first announced | Support removed |
| --- | --- | --- |
| Windows Server 2008 R2 with SP1 | July 2015 | Version 1702 |
| Windows Server 2008 with SP2 | July 2015 | Version 1511 |

## SQL Server

| SQL Server versions | Deprecation first announced | Support removed |
| --- | --- | --- |
| Sql Server 2014 | Oct 2024 | Version 2409 |
| SQL Server 2012 | July 2021 | The first release after July 1, 2022 |
| SQL Server 2008 R2 | July 2015 | Version 1702 |
| SQL Server 2008 | July 2015 | Version 1511 |

If you need to upgrade your version of SQL Server, we recommend the following methods, from easy to more complex:

1. [Upgrade SQL Server in-place](../../../servers/manage/upgrade-on-premises-infrastructure#upgrade-sql-server) (recommended).
2. Install a new version of SQL Server on a new computer. Then to point your site server at the new SQL Server, [use the database move option](../../../servers/manage/modify-your-infrastructure#bkmk_dbconfig) of Configuration Manager setup.
3. Use [backup and recovery](../../../servers/manage/backup-and-recovery).

Note

Make sure to also upgrade versions of SQL Server Express at secondary sites.