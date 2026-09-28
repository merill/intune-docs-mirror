---
layout: Conceptual
title: How to run reports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/how-to-run-configuration-manager-reports
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
description: Information about how to access reports in the Configuration Manager console or by using Report Manager.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d7378aa8-ba07-602c-84c2-bbba80713f1a
document_version_independent_id: e028a282-9a0e-50ef-bb22-853a09ebfe0c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/how-to-run-configuration-manager-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/how-to-run-configuration-manager-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/how-to-run-configuration-manager-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: c4906475-1305-5143-4e1d-e4da3eea3c5b
---

# How to run reports - Configuration Manager | Microsoft Learn

Reports in Configuration Manager are stored in SQL Server Reporting Services, and the data rendered in the report is retrieved from the Configuration Manager site database. You can access reports in the Configuration Manager console or by using Report Manager, which you access in a web browser. You can open reports on any computer that has access to the computer that is running SQL Server Reporting Services, and you must have sufficient rights to view the reports. When you run a report, the report title, description, and category are displayed in the language of the local operating system.

## How to run a Configuration Manager report

Use the following procedures to run a Configuration Manager report.

Warning

To run reports, you must have **Read** rights for the **Site** permission and the **Run Report** permission that is configured for specific objects.

Report Manager is a web-based report access and management tool that you use to administer a single report server instance on a remote location over an HTTP connection. You can use Report Manager for operational tasks, for example, to view reports, modify report properties, and manage associated report subscriptions. This topic provides the steps to view a report and modify report properties in Report Manager, but for more information about the other options that Report Manager provides, see Report Manager in SQL Server 2008 Books Online.

### To run a report in the Configuration Manager console

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then select **Reports** to list the available reports.

    Tip

    If no reports are listed, verify that the reporting services point is installed and configured. For more information, see the topic [Configuring Reporting in Configuration Manager](../../../../core/servers/manage/configuring-reporting).
3. Select the report that you want to run, and then on the **Home** tab, in the **Report Group** section, select **Run** to open the report.
4. When there are required parameters, specify the parameters, and then select **View Report**.

### To run a report in a web browser

1. In your web browser, enter the Report Manager URL, for example, `http://Server1/Reports`. You can determine the Report Manager URL on the **Report Manager URL** page in Reporting Services Configuration Manager.
2. In Report Manager, select the report folder for Configuration Manager, for example, ConfigMgr\_CAS.

    Tip

    If no reports are listed, verify that the reporting services point is installed and configured. For more information, see the topic [Configuring Reporting in Configuration Manager](../../../../core/servers/manage/configuring-reporting).
3. Select the report category for the report that you want to run, and then select the link for the report. The report opens in Report Manager.
4. When there are required parameters, specify the parameters, and then select **View Report**.