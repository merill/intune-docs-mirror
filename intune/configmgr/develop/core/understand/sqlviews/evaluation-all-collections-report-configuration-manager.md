---
layout: Conceptual
title: Evaluation of the All collections report - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/evaluation-all-collections-report-configuration-manager
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
description: Information about all of the collections in the Configuration Manager hierarchy.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: af33d413-44ae-2f04-c19c-e1ec79604915
document_version_independent_id: f5e0b92a-92cd-aafd-13e3-759d4c5057cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/evaluation-all-collections-report-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/evaluation-all-collections-report-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/evaluation-all-collections-report-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 5bc531d2-d236-b2be-e417-f2aceed6a483
---

# Evaluation of the All collections report - Configuration Manager | Microsoft Learn

The **All collections** report is one of the built-in reports in Configuration Manager and is a good example of a basic report. This report lists all of the collections in the Configuration Manager hierarchy.

To open the report, use the following procedure:

## To examine the properties of the All collections report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. From the list of reports, select **All collections** and then, in the **Home** tab, in the **Report Group** group, select **Edit**.
4. In the **Report Data** pane of Report Builder, expand **Datasets** and then double-click **DataSet0**.
5. In the **Dataset Properties** dialog box, you can view the SQL query for the report, the fields that will be returned, and the parameters that the report uses.
6. Close the **Dataset Properties** dialog box.
7. Close Report Builder.