---
layout: Conceptual
title: 'Exercise 3: Create a new report - Configuration Manager | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-3-create-new-configuration-manager-report
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
description: Create a simple report and configure the report properties.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 92af1f07-8489-79f6-b929-9a66b51ff6db
document_version_independent_id: 64351c2d-f8a6-e723-ba59-df4630b061de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/exercise-3-create-new-configuration-manager-report.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/exercise-3-create-new-configuration-manager-report
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/exercise-3-create-new-configuration-manager-report.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: c47c5715-4720-10b9-8c0d-f1231d136fca
---

# Exercise 3: Create a new report - Configuration Manager | Microsoft Learn

In this exercise, you'll create a simple report in Microsoft SQL Server Report Builder, and configure the report properties.

The report displays all collections that administrative users have created, and excludes the built-in collections. The results will display the collection ID and name, the last collection refresh time and the date of the last collection membership change.

## To create a new report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports**.
3. In the **Home** tab, in the **Create** group, select **Create Report**.
4. On the **Information** page of the Create Report Wizard, select **SQL-based Report**, and then configure the following properties:

    - **Name:** Enter **All collections created by administrative users**.
    - **Description:** Enter **Displays all collections that were created by an administrative user (excludes built-in collections).**
    - **Path:** Select **Browse**, and then select the **Site � General** folder to store the report.
5. Select **Next**.
6. On the **Summary** page of the Create Report Wizard, review the actions that will be taken and then select **Next**.
7. On the **Completion** page of the wizard, review any messages and then select **Close**.
8. Report Builder opens. In the **Report Data** pane, right-click **Datasets**, and then select **Add Dataset**.
9. On the **Query** page of the **Dataset Properties** dialog box, select **Use a dataset embedded in my report**.
10. In the **Data source** drop-down list, select the data source you want to use for the report. This is typically automatically generated and will begin with **AutoGen\_**.
11. Select a query type of **Text**, and then enter the following query in the **Query** field.

    ```sql
    SELECT
    v_Collections.CollectionID,
    v_Collections.CollectionName, 
    v_Collections.LastRefreshTime, 
    v_Collections.LastMemberChangeTime
    FROM
    V_Collections
    WHERE
    IsBuiltIn=0
    ```
12. Select **OK** to close the **Dataset Properties** dialog box.
13. In Report Builder, on the **Insert** tab, in the **Data Regions** group, select **Table**, and then select **Table Wizard**.
14. On the **Choose a dataset** page of the **New Table or Matrix** wizard, select **Choose an existing dataset in this report or a shared dataset**, and then select the dataset you previously created, **Dataset1**.
15. Select **Next**.
16. On the **Arrange fields** page of the **New Table or Matrix** wizard, drag **CollectionID**, **CollectionName**, **LastRefreshTime** and **LastMemberChangeTime** from the **Available fields** field to the **Values** field.
17. Select **Next**.
18. On the **Choose the layout** page of the **New Table or Matrix** wizard, select **Next**.
19. On the **Choose a style** page of the wizard, choose one of the available themes for the report, and then select **Finish**.
20. Verify that the data in the report is as expected.
21. Save and close the report in Report Builder.

The new report is now available in the Configuration Manager console.