---
layout: Conceptual
title: Diagnostics data collection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected
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
description: Learn about how Configuration Manager collects diagnostics and usage data about itself.
ms.date: 2021-08-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 1b3d4def-2754-91b4-bf50-1deca28d5de0
document_version_independent_id: de695606-8217-53b2-a57d-656a119dda10
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: a811a6ed-d278-b660-ec89-574d00cc07fd
---

# Diagnostics data collection - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To collect diagnostics and usage data for Configuration Manager, each primary site runs SQL Server queries on a weekly basis. In a multi-site hierarchy, the data is replicated to the central administration site.

At the top-level site of a hierarchy, the service connection point submits this information when it checks for updates. The mode of the service connection point determines how the data is transferred:

- **Online**: Once a week, the service connection point automatically sends diagnostics and usage data to the cloud service.
- **Offline**: You manually transfer diagnostics and usage data with the [service connection tool](../../servers/manage/use-the-service-connection-tool).

For more information, see [About the service connection point](../../servers/deploy/configure/about-the-service-connection-point).

Next, you can view diagnostic and usage data to confirm that your Configuration Manager hierarchy contains no sensitive information:

Tip

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](/en-us/powershell/sccm/privacy-statement).

Some of the tools that are included with Configuration Manager collect usage data. For more information, see [Diagnostic usage data for tools](tools).