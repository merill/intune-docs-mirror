---
layout: Conceptual
title: Integrate with Power BI Report Server - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/powerbi-report-server
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
description: Integrate Power BI Report Server with Configuration Manager reporting for modern visualization and better performance.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: eb13fff2-41ef-fa3d-4685-7b5b17c6b2a7
document_version_independent_id: 7e541e95-40de-b779-dd3e-b03f5fb5b911
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/powerbi-report-server.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/powerbi-report-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/powerbi-report-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: 73c76898-90e2-81ac-e703-6ce0d21285d3
---

# Integrate with Power BI Report Server - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can integrate [Power BI Report Server](/en-us/power-bi/report-server/get-started) with Configuration Manager reporting. This integration gives you modern visualization and better performance. It adds console support for Power BI reports similar to what already exists with SQL Server Reporting Services.

Save Power BI Desktop report files (.PBIX) and deploy them to the Power BI Report Server. This process is similar as with SQL Server Reporting Services report files (.RDL). You can also launch the reports in the browser directly from the Configuration Manager console.

## Prerequisites

- Power BI Report Server license. For more information, see [Licensing Power BI Report Server](/en-us/power-bi/report-server/get-started#licensing-power-bi-report-server).
- Download [Microsoft Power BI Report Server-September 2024](https://www.microsoft.com/download/details.aspx?id=105945), or later.

    - Don't install Power BI Report Server right away. For the proper process based on your environment, see Configure the reporting services point.
    - It's recommended that you use a [supported version of Power BI Report Server](/en-us/power-bi/report-server/support-timeline). For versioning information, see the [Change log for Power BI Report Server](/en-us/power-bi/report-server/changelog).
- Download Microsoft Power BI Desktop (Optimized for Power BI Report Server - September 2019), or later. It's recommended that you use a [supported version](/en-us/power-bi/report-server/support-timeline). For versioning information, see the [Change log for Power BI Report Server](/en-us/power-bi/report-server/changelog).

    Use versions of Power BI Desktop:

    - That are from the [Microsoft Download Center](https://www.microsoft.com/download/). Don't use a version from the Microsoft Store.
    - [That states they're **Optimized for Power BI Report Server**](/en-us/power-bi/report-server/install-powerbi-desktop). Don't use versions that aren't **Optimized for Power BI Report Server**.

    Note

    When using Configuration Manager version 2111 or earlier with Power BI Desktop (Optimized for Power BI Report Server - May 2021) or later, you may notice the following behavior:

    - You might experience delays updating the data source on newly updated reports.
    - You may receive `The remote server returned an error; (400) Bad Request.` errors in the **SRSRP.log**. For more information about the relevant change to Power BI Desktop (optimized for Power BI Report Server) May 2021, see [Change data source connection strings in Power BI reports](/en-us/power-bi/report-server/connect-data-source-apis). The version before the connection change ocurred is January 2021.
- Power BI integration uses the same role-based administration for reporting.

    - Power BI Report Server doesn't support reports that are enabled for role-based access. All report viewers will see the same results, whatever their assigned scope.

## Configure the reporting services point

This process varies depending upon whether you already have this role in the site.

### You have a reporting services point

Only use this process if you already have a reporting services point in the site. Do all steps of this process on the same server:

1. In **Reporting Services Configuration Manager**, back up the **Encryption Keys**. For more information, see [SSRS Encryption Keys - Back Up and Restore Encryption Keys](/en-us/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys).

    Warning

    If you skip this step, you'll lose access to any custom reports in SQL Server Reporting Services.
2. Remove the reporting services point role from the site.
3. Uninstall SQL Server Reporting Services, but keep the database.
4. Install Power BI Report Server.
5. Configure the Power BI Report Server

    1. Use the previous report server database.
    2. Use **Reporting Services Configuration Manager** to restore the **Encryption Keys**.

    - Before you add the reporting services point role in Configuration Manager, use SQL Server Reporting Services Configuration Manager to test and verify the configuration. For more information, see [Verify SQL Server Reporting Services installation](configuring-reporting#verify-sql-server-reporting-services-installation).
6. Add the reporting services point role in Configuration Manager.

### You don't have a reporting services point

Only use this process if you don't already have a reporting services point in the site. Do all steps of this process on the same server:

1. Install Power BI Report Server.
2. Add the reporting services point role in Configuration Manager. For more information, see [Configure reporting](configuring-reporting).

## Configure the Configuration Manager console

1. On a computer that has the Configuration Manager console, update the Configuration Manager console to the latest version.
2. Install Power BI Desktop. Make sure the language is the same and verify the versioning prerequisites.
3. After it installs, launch Power BI Desktop at least once before you open the Configuration Manager console.

## Create Power BI reports

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand **Reporting**, and select the new **Power BI Reports** node.
2. In the ribbon, select **Create Report**. This action opens Power BI Desktop.
3. Create a report in Power BI Desktop.

    - In Power BI Desktop, when you connect to a data source, select **DirectQuery** for the Connection settings.
    - Only use supported SQL views in these reports. For more information, see [Creating custom reports by using SQL Server views in Configuration Manager](../../../develop/core/understand/sqlviews/create-custom-reports-using-sql-server-views).
4. When the report is ready to save, go to the **File** menu, select **Save as**, then choose **Power BI Report Server**.
5. In the **Power BI Report Server Selection** window, enter the URL for the reporting services point as the **New report server address**. For example, `https://rsp.contoso.com/Reports`. Select **OK**.
6. In the **Save report** window, double-click the `ConfigMgr_<SiteCode>` folder. For example, `ConfigMgr_PS1`, where `PS1` is the ConfigMgr site code. You can optionally choose or create (from the report server) a sub folder to store it in.

    Tip

    Reports and report folders with Power BI reports must be located in the `ConfigMgr_<SiteCode>` folder on the report server or they won't appear in the Configuration Manager console.
7. In **File name**, enter a name for the report.

In the Configuration Manager console, you see the new report in the list of Power BI Reports. If you don't see your reports, verify that you saved the reports to the `ConfigMgr_<SiteCode>` folder.

There are sample reports available for download. For more information, see [Install Power BI sample reports](powerbi-sample-reports).

## Power BI report templates in Community hub

Using [Community hub](community-hub), you can share Power BI report templates you've created and download templates that others have shared.

### Contributing a Power BI report template (PBIT) files to Community hub

1. Open the Configuration Manager console and go to **Community** &gt; **Community hub**
2. If needed, select **Sign in** to sign in to GitHub. You'll see the **Your hub** link after signing in.
3. Select **Your hub** then **Add an item** to launch the **Contribute item wizard**.
4. For the **Type**, choose **Power BI Report Template** then select **Browse**.
5. Choose the `.pbit` file you want to contribute, then select **Open**.
6. Edit the **Name** and **Description** for the report template then select **Next** when done.
7. On the **Organization** page, select the **GitHub Organization** to use for [organization branding](community-hub-contribute#bkmk_brand) if needed. Select **Next** to upload the template.
8. Once the item is uploaded, you'll be given the pull request URL of the change for monitoring.
9. Select **Close** when you're done to exit the wizard.

### Downloading a Power BI report template (PBIT) file from Community hub

1. Open the Configuration Manager console, go to **Community** &gt; **Community hub**.
2. From **All objects** or a search, choose a Power BI report template, then select **Download**.
3. Select a file location to save the downloaded `.pbit` file and choose **Save**.
4. If Power BI Desktop (Optimized for Power BI Report Server) is installed, you'll be prompted to open the `.pbit` file.
5. Select **Yes** and Power BI Desktop (Optimized for Power BI Report Server) will load the `.pbit` file.
6. Specify your Configuration Manager database name and database server name when prompted, then select **Load**.

    Note

    When loading or applying the data model, ignore any errors if you come across one. For example, if you see the following error: "Connecting to tables from more than one database isn't supported in DirectQuery mode", select **Close**. Then refresh the data source settings:

    1. In Power BI Desktop, in the ribbon, select **Edit Queries**, and then select **Data source settings**.
    2. Select **Change Source**, confirm your server and database names, and select **OK**.
    3. Close the data source settings window, and then select **Apply changes**.
7. When the report data is loaded, select **File** &gt; **Save As**, then select **Power BI Report Server**.
8. Save the report to a folder on the root Configuration Manager reporting folder on the reporting point. You may want to create a `Downloaded Reports` folder for these items.
9. Repeat the steps for any other report templates that were downloaded. When you're done, close Microsoft Power BI Desktop (Optimized for Power BI Report Server).

## Known issues

There's a known issue with Power BI Report Server and email subscriptions. After you configure the email settings in the Reporting Services Configuration Manager, when you try to create a new subscription, the option to deliver a report by **Email** isn't available. To work around this issue, restart the Power BI Report Server service.