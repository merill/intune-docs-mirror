---
layout: Conceptual
title: Install Power BI sample reports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/powerbi-sample-reports
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
description: Learn how to install the Power BI sample reports in Configuration Manager
ms.date: 2021-11-03T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 266131e1-466d-ec44-35d2-e1f4fc08d27c
document_version_independent_id: 063515f6-2ea9-0d47-455b-982e14ea5580
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/powerbi-sample-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/powerbi-sample-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/powerbi-sample-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
platformId: 73f5fac5-4ecf-237e-2b07-fdfdf1b09fea
---

# Install Power BI sample reports - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can integrate [Power BI Report Server](/en-us/power-bi/report-server/get-started) with Configuration Manager reporting. There are sample reports available for download that you can install in Configuration Manager. This article explains how to install the Power BI sample reports in Configuration Manager.

## Prerequisites

- Configuration Manager reporting services point with [Power BI Report Server integrated](powerbi-report-server)
- Microsoft Power BI Desktop (Optimized for Power BI Report Server). Use a version released between September 2019 and January 2021. For versioning information, see the [Change log for Power BI Report Server](/en-us/power-bi/report-server/changelog). 

    Important

    Use versions of Power BI Desktop:

    - That are from the [Microsoft Download Center](https://www.microsoft.com/download/). Don't use a version from the Microsoft Store
    - [That states they're **Optimized for Power BI Report Server**](/en-us/power-bi/report-server/install-powerbi-desktop). Don't use versions that aren't **Optimized for Power BI Report Server**.
    - That were released no earlier than September 2019 and no later than January 2021. Microsoft Power BI Desktop (Optimized for Power BI Report Server - January 2021) is recommended.

## Download the sample reports

To download the sample reports:

1. Download the Power BI sample reports from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=101452).
2. Save the `ConfigMgrSamplePowerBIReports.exe` file.
3. Move the file to a computer with Microsoft Power BI Desktop (Optimized for Power BI Report Server) installed if you downloaded it from a different device.
4. Run the `ConfigMgrSamplePowerBIReports.exe` file to extract the .pbit files.

Note

Some of the sample reports are also available for download in [Community hub](community-hub).

## Install the sample reports

To install the sample reports:

1. On the Power BI Report server, create a new folder called `Sample Reports` in the root Configuration Manager reporting folder.

    [![Creating the Sample Report folder in the root Configuration Manager reporting folder from ](media/create-sample-reports-folder.png)](media/create-sample-reports-folder.png#lightbox)
2. Launch Microsoft Power BI Desktop (Optimized for Power BI Report Server).
3. Select **File** then **Open** and navigate to where you saved the extracted .pbit files.
4. Select one of the .pbit files you extracted from the `ConfigMgrSamplePowerBIReports.exe` file.
5. Specify your Configuration Manager database name and database server name when prompted, then select **Load**.

    [![Specify the database and database server name](media/sample-report-database.png)](media/sample-report-database.png#lightbox)

    Note

    When loading or applying the data model, ignore any errors if you come across one. For example, if you see the following error: "Connecting to tables from more than one database isn't supported in DirectQuery mode", select **Close**. Then refresh the data source settings:

    1. In Power BI Desktop, in the ribbon, select **Edit Queries**, and then select **Data source settings**.
    2. Select **Change Source**, confirm your server and database names, and select **OK**.
    3. Close the data source settings window, and then select **Apply changes**.
6. When the report data is loaded, select **File** &gt; **Save As**, then select **Power BI Report Server**.

    [![Save as Power BI Report Server](media/save-powerbi-report-server.png)](media/save-powerbi-report-server.png#lightbox)
7. Save the report to the `Sample Reports` folder you created on the reporting point.

    [![Save to the Sample Reports folder](media/save-sample-report.png)](media/save-sample-report.png#lightbox)
8. Repeat the steps for any other sample reports. When you're done, close Microsoft Power BI Desktop (Optimized for Power BI Report Server).
9. In the Configuration Manager console, go to **Monitoring** &gt; **Power BI Reports** &gt; **Sample Reports**.
10. Right-click on one of the reports and select **Run in Browser** to launch the report.

    [![Run the sample report from the Configuration Manager console](media/view-powerbi-report.png)](media/view-powerbi-report.png#lightbox)

## Sample reports

The following sample Power BI reports are included in the download:

- Software Update Compliance Status
- Software Update Deployment Status
- Client Status
- Content Status
- Microsoft Edge Management