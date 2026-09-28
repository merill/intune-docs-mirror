---
layout: Conceptual
title: Diagnostic usage data for tools - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/tools
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
description: Learn about the diagnostics and usage data that Configuration Manager collects for its tools.
ms.date: 2021-08-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8047e3b4-8310-7a1e-0bbb-13b605312886
document_version_independent_id: 8047e3b4-8310-7a1e-0bbb-13b605312886
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/tools.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/tools
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/tools.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a72086ac-ff14-8831-7f12-44a770388475
---

# Diagnostic usage data for tools - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Some of the tools that are included with Configuration Manager collect usage data. Microsoft uses this data to improve the quality of these tools, and better understand customer usage. Microsoft collects data for the following Configuration Manager tools:

- Client tools
- Server tools
- Support Center
- CMTrace

For more general information about these tools, see [Configuration Manager Tools](../../support/tools).

Note

The **ConfigurationManager** PowerShell module also collects usage data. For more information, see [Configuration Manager cmdlet library privacy statement](/en-us/powershell/sccm/privacy-statement).

The following data is collected for these tools:

- Version
- Start and stop times to calculate duration of use

Because these tools can run on any Windows device, they all use the Windows diagnostic data channel. They don't rely on Configuration Manager diagnostic data collection. The device on which the tool runs needs to be configured for at least **Optional** diagnostic data. If you configure the device for any other setting, Windows won't collect data for these Configuration Manager tools. For more information on these Windows diagnostic data levels, see the following articles:

- [Windows 10, version 1709 and newer optional diagnostic data](/en-us/windows/privacy/windows-diagnostic-data)
- [Configure Windows diagnostic data in your organization](/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization)

Next, see the frequently asked questions about diagnostic and usage data for Configuration Manager: