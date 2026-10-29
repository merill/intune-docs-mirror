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
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
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