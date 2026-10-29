---
layout: Conceptual
title: 'Exercise 1: Run an existing report - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report
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
description: Run an existing Configuration Manager report and review specific report elements.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3f3f375c-4580-f42a-1f08-6be6b764406e
document_version_independent_id: a969ce4d-930f-8d56-db70-e7517466cce7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 827d7edf-fa6b-37d2-909f-4a55eae8ccf9
---

# Exercise 1: Run an existing report - Configuration Manager | Microsoft Learn

In this exercise, you will run an existing Configuration Manager report and review specific report elements.

For more information about how to work with reports in Configuration Manager, see [Introduction to reporting](../../../../core/servers/manage/introduction-to-reporting).

## To run an existing Configuration Manager report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the list of reports, find and select the report, **Processor information for a specific computer**.

    Tip

    To make it easier to find a report, you can select a column title to sort the reports, or you can type the name, or a partial name for the report in the search box, and then select **Search**.
4. On the **Home** tab, in the **Report Group** group, select **Run**.
5. Specify any required parameters (in this case, a computer name), and then select **View Report**.

The report is displayed. Review the processor information and then close the report.