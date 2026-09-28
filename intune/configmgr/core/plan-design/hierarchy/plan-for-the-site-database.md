---
layout: Conceptual
title: Plan the site database - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-site-database
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
description: Consider the site database and the site database server role as you plan your Configuration Manager hierarchy.
ms.date: 2020-10-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 0098acf6-a144-6848-564e-a2363f803070
document_version_independent_id: 7ebfc378-ab51-8807-8cce-6c23d3e7e21a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/plan-for-the-site-database.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/plan-for-the-site-database
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/plan-for-the-site-database.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 047b5d02-ebf3-4d89-fe80-86d946895a0b
---

# Plan the site database - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The site database server is a computer that runs a supported version of Microsoft SQL Server. SQL Server is used to store information for Configuration Manager sites. Each site in a Configuration Manager hierarchy contains a site database and a server that is assigned the site database server role.

- For central administration sites and primary sites, you can install SQL Server on the site server, or you can install SQL Server on a computer other than the site server.
- For secondary sites, you can use SQL Server Express instead of a full SQL Server installation. The database server must, however, be run on the secondary site server.
- For SQL Server Always On availability groups, set the database recovery model to FULL.
- For non-availability group configurations, set the database recovery model to SIMPLE.

Further information on SQL Server Recovery Modes can be found in [Recovery Models (SQL Server)](/en-us/sql/relational-databases/backup-restore/recovery-models-sql-server).

The following SQL Server configurations can be used to host the site database:

- The default instance of SQL Server
- A named instance on a single computer running SQL Server
- A named instance on a failover cluster instance of SQL Server
- A SQL Server Always On availability group

To host the site database, SQL Server must meet the [supported version](../configs/support-for-sql-server-versions) and [configuration](../configs/supported-configurations-for-sql-server) requirements.

## Remote database server location considerations

If you use a remote database server computer, ensure that the intervening network connection is a high-availability, high-bandwidth network connection. The site server and some site system roles must constantly communicate with the remote server that is hosting the site database.

- The amount of bandwidth required for communications to the database server depends on a combination of many different site and client configurations. Therefore, the actual bandwidth required cannot be adequately predicted.
- Each computer that runs the SMS Provider and that connects to the site database increases network bandwidth requirements.
- The computer that runs SQL Server must be located in a domain that has two-way trust with the site server and all computers running the SMS Provider.
- You can't use a failover cluster instance of SQL Server for the site database server when the site database is co-located with the site server.

Typically, a site system server supports site system roles from only a single Configuration Manager site. You can, however, use different instances of SQL Server to host a database from different Configuration Manager sites. To support databases from different sites, configure each instance of SQL Server to use unique ports for communication.