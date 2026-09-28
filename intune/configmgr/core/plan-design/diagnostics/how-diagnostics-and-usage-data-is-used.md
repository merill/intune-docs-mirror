---
layout: Conceptual
title: Use of diagnostics data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used
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
description: Learn about how Microsoft uses the diagnostics and usage data that Configuration Manager collects.
ms.date: 2021-08-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ff5ff690-68aa-6c00-7920-da2387d6b6f8
document_version_independent_id: 0257ef76-38ee-654a-2aad-d4205122c4fe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: c5550770-6ba4-630d-6346-285fb9095035
---

# Use of diagnostics data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Diagnostic and usage data that Configuration Manager collects provides Microsoft nearly immediate feedback about how the product is working and is used to adjust future updates. Microsoft can also see configuration data that helps them engineer and test the configurations that you use in production. For example:

- The Windows server versions used on site servers
- Installed language packs
- The delta of the SQL Server schema against the product default

This data helps the engineering team plan future tests to make sure you have the best experience with the most common configurations. This data is crucial to quickly adjust and adapt with a frequent release cycle.

Equally important is how the diagnostics and usage data isn't used. Microsoft doesn't use this data for:

- Licensing audits, such as comparing customer usage against license agreements
- Auditing of products that are out of support
- Advertising based on available data such as feature usage or geolocation (time zone)

Microsoft uses available data to improve the product. For example:

- The initial support offered by the current branch of Configuration Manager limited the support timeline for Windows Server 2008 R2. Microsoft examined the usage data from customers who had upgraded to the Configuration Manager current branch. They then identified the need to revise and extend this timeline to support customers who still use this OS.
- Microsoft improved the prerequisite checks for installing an update. They removed obsolete rules, accounted for additional cases, and automatically remediated some issues.

Next, learn about how Configuration Manager collects diagnostics and usage data about itself: