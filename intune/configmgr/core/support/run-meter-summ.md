---
layout: Conceptual
title: Run Meter Summarization Tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/run-meter-summ
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
description: Use the Run Meter Summarization Tool to trigger the software metering summarization tasks in Configuration Manager.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: fc6be7c8-81ec-c73f-12eb-0bc06f07ab16
document_version_independent_id: a6011379-51c2-5981-fb28-0e040f21bf56
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/run-meter-summ.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/run-meter-summ
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/run-meter-summ.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: d9f7a1b7-65ce-eb91-80fc-25dfe692ce96
---

# Run Meter Summarization Tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Run Meter Summarization Tool is one of the [Configuration Manager tools](tools). Use it to immediately trigger the maintenance tasks for software metering summarization on primary sites. By default, these tasks run as scheduled in **Site Maintenance** tasks, which start after 12:00 AM every day.

These tasks summarize the data in the **MeterData** SQL Server table, and write the summary results into the **FileUsageSummary** and **MonthlyUsageSummary** tables. Then you see the summarized result in software metering reports. Any Configuration Manager administrative user who can connect to the primary site database can use this tool to run summarization.

This tool runs the **File Usage Summary** and **Monthly Usage Summary** software metering data summarization tasks. It summarizes all existing meter data without the usual 12-hour waiting period. Run it on the SQL Server that hosts the site database. If summarization is successful, the exit code is set to `0`. If there was an error, the exit code is `1`.

## Usage

### Command Line

`runmetersumm  [sms database name]  <delay in hours for summarization <default=0>>`

### Options

#### Database name

The name of the site database on the SQL Server.

#### Delay in hours for summarization

The tool summarizes the software metering usage generated before the delay. By default, this delay is zero.

### Example

#### Summarize the software metering usage generated 12 hours ago

`runmetersumm CCM_ABC <12>`