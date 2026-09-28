---
layout: Conceptual
title: Diagnostics and usage data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data
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
description: Learn about the diagnostics and usage data that Configuration Manager collects about itself.
ms.date: 2021-08-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 66697413-ec02-c896-4da0-7ae2a03b22b0
document_version_independent_id: b08e6e09-c609-ee05-9bb0-eed7e3c5dbcd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 51262ba7-232e-abf2-33ce-9454c5fe49b5
---

# Diagnostics and usage data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager collects diagnostics and usage data about itself, which is used by Microsoft to improve the installation experience, quality, and security of future releases. With version 2509, no further changes or updates are planned for diagnostic and usage data collection.

Each Configuration Manager hierarchy enables diagnostics and usage data. It consists of SQL Server queries that run on a weekly basis on each primary site and at the central administration site (CAS). When the hierarchy uses a CAS, child primary sites replicate their data to that CAS. At the top-level site of your hierarchy, the [service connection point](../../servers/deploy/configure/about-the-service-connection-point) submits this information when it checks for updates. If the service connection point is in offline mode, you transfer the information by using the [service connection tool](../../servers/manage/use-the-service-connection-tool).

Note

Configuration Manager collects data only from the site's SQL Server database, and it doesn't collect data directly from clients or site servers.

For more information, see the [Microsoft privacy statement](https://privacy.microsoft.com/privacystatement).

Next, learn about how Microsoft uses the diagnostics and usage data that Configuration Manager collects:

Tip

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](/en-us/powershell/sccm/privacy-statement).

Some of the tools that are included with Configuration Manager collect usage data. For more information, see [Diagnostic usage data for tools](tools).