---
layout: Conceptual
title: SQL Server views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager
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
description: A Microsoft SQL Server view is a virtual table whose contents are based on the result from a SQL query.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms:assetid: a1924bed-b5fc-49a8-80ee-30b4e96defaa
ms.collection: tier3
locale: en-us
document_id: ea173a5e-6252-e68f-d56b-095154c14eed
document_version_independent_id: 72024bcc-bf58-c691-84b3-484fd9ffbd8f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: b737398b-d40f-77ab-bbcd-6964e8e24986
---

# SQL Server views - Configuration Manager | Microsoft Learn

A Microsoft SQL Server view is a virtual table whose contents are based on the result from a SQL query. A view consists of a set of named columns and rows of data. However, the contents of a view aren't stored in the SQL Server database. The rows and columns of data come from tables or other SQL Server views referenced in the query that defines the view and are produced dynamically when the query is run. The query that defines the view can be from one or more tables or from other views in one or more databases. Distributed queries (queries that access data from multiple data sources) can also be used to define views that pull data from multiple heterogeneous sources (data stored in multiple formats), such as data stored in a SQL Server database, a text file, or a Microsoft Excel spreadsheet.

During setup, Configuration Manager creates the following SQL Server view types:

- Views against static (unchanging) tables.
- Views that use data from tables with a dynamic (changing) schema.

For a dynamic schema, setup creates a number of SQL Server stored procedures that create the views. These stored procedures are run by Configuration Manager to refresh the views when the schema of underlying tables changes. Collection evaluation, discovery, and inventory data are examples of data for which new tables or new properties in existing tables might be created during the operation of a Configuration Manager site.

## Reporting in Configuration Manager

Configuration Manager uses Microsoft SQL Server Reporting Services to allow you to generate and run reports against the Configuration Manager database, from the Configuration Manager console. This service now replaces the method used to create reports in Configuration Manager 2007, and gives the following advantages:

- Uses an industry standard reporting system to query the Configuration Manager database.
- SQL Server Reporting Services offers higher performance, availability, and scalability over the previous reporting method.
- Enables users who aren't familiar with Configuration Manager reporting to generate unplanned reports.
- Enables users to subscribe to reports; for example, a manager could automatically be e-mailed a report each day, detailing the status of a software update rollout.
- Simplifies the creation of SQL-based reports in Configuration Manager.
- Enables users to export reports in different kinds of popular formats.

For more information about using reports from the Configuration Manager console, see [Introduction to reporting](../../../../core/servers/manage/introduction-to-reporting).

## Configuration Manager SQL Server view schema

To create effective reports, accurate SQL statements based on the appropriate Configuration Manager views need to be used to retrieve the required data and to display the expected output. Knowing the Configuration Manager database view schema is an important first step in learning how to create these reports.

Much of the Configuration Manager SQL Server view schema maps to the SMS Provider WMI schema, which is used when building WQL-based queries and collections in the Configuration Manager console. However, querying the views directly can be much faster than using WMI and WQL, which receive a query request and in turn query the SQL Server database for the information. By using SQL Server views directly, you eliminate the intermediate step and gain a faster path to the data. For more information about the SMS Provider WMI schema, see [SMS Provider WMI Schema Reference in Configuration Manager](sms-provider-wmi-schema-reference-configuration-manager).

## Configuration Manager SQL Server view categories

To effectively create reports with the required output, it's essential to know what data each of the Configuration Manager SQL Server views contains and how the views are related to each other. The following topics in this section provide detailed information about each of the view categories, what kind of data each of the views contains, and what columns can be used to **JOIN** views in SQL statements.