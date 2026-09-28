---
layout: Conceptual
title: 'Exercise 2: Modify an existing report - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-2-modify-existing-configuration-manager-report
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
description: Modify a Configuration Manager report and then run the modified report.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ae26d02a-815a-3a43-bb76-34a734ca907a
document_version_independent_id: dcb92834-7c2f-da52-b127-d38d0e148ec1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/exercise-2-modify-existing-configuration-manager-report.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/exercise-2-modify-existing-configuration-manager-report
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/exercise-2-modify-existing-configuration-manager-report.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: f94b2050-e5f3-cf15-0950-de03e0efde3e
---

# Exercise 2: Modify an existing report - Configuration Manager | Microsoft Learn

In this exercise, you will modify a Configuration Manager report and then run the modified report. The report SQL statement will be modified in the report properties to remove an existing report column and add two new report columns.

## To modify a Configuration Manager report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. From the list of reports, select the report that you want to modify and then, in the **Home** tab, in the **Report Group** group, select **Edit**.
4. Report Builder opens. In Report Builder, make any modifications you require to the report.
5. Save the report and close Report Builder. You can now run the modified report from the Configuration Manager console.