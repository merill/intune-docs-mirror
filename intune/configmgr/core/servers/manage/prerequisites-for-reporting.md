---
layout: Conceptual
title: Prerequisites for reporting - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/prerequisites-for-reporting
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
description: Understand various dependencies that impact your use of reporting in Configuration Manager.
ms.date: 2020-04-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: da2d4992-1cdf-be96-27d0-edea9c8c8b5d
document_version_independent_id: b1e15695-7633-2ba6-9ca7-5ce09d60f624
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/prerequisites-for-reporting.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/prerequisites-for-reporting
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/prerequisites-for-reporting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: aec54a20-2d29-56bd-abb6-783360c0aaab
---

# Prerequisites for reporting - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Reporting in Configuration Manager has the following dependencies:

- SQL Server Reporting Services
- Reporting services point
- Power BI Report Server (optional, starting in version 2002)

## SQL Server Reporting Services

Before you can use reporting in Configuration Manager, install and configure SQL Server Reporting Services.

For more information about planning and deploying Reporting Services, see the [Install SQL Server Reporting Services](/en-us/sql/reporting-services/install-windows/install-reporting-services).

Install the Reporting Services database on either the default instance or a named instance of a 64-bit SQL Server installation. Colocate the SQL Server instance with the site system server, or configure it on a remote computer.

Configuration Manager supports the same versions of SQL Server for reporting as it does for the site database. For more information, see [Supported SQL Server versions](../../plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).

## Reporting services point

Before you can use reporting in Configuration Manager, configure the reporting services point site system role.

For more information, see [Site and site system prerequisites](../../plan-design/configs/site-and-site-system-prerequisites#reporting-services-point).

## Power BI Report Server

Starting in version 2002, you can integrate reporting with Power BI Report Server. For more information including prerequisites, see [Integrate with Power BI Report Server](powerbi-report-server).