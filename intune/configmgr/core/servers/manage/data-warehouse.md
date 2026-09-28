---
layout: Conceptual
title: Data warehouse - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/data-warehouse
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
description: Data warehouse service point and database for Configuration Manager
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0d184266-085d-3d81-f0c6-c0132b3a0901
document_version_independent_id: ede0e2bf-2e01-cd7f-67a2-be46671a0619
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/data-warehouse.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/data-warehouse
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/data-warehouse.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: e4301358-9c9a-ad83-bf38-e74ebf9fece6
---

# Data warehouse - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the data warehouse service point to store and report on long-term historical data for your Configuration Manager deployment.

The data warehouse supports up to 2 TB of data, with timestamps for change tracking. The data warehouse stores data by automatically synchronizing data from the Configuration Manager site database to the data warehouse database. This information is then accessible from your reporting service point. Data synchronized to the data warehouse database is kept for three years. Periodically, a built-in task removes data that's older than three years.

Data that is synchronized includes the following from the global data and site data groups:

- Infrastructure health
- Security
- Compliance
- Malware
- Software deployments
- Inventory details (however, inventory history isn't synchronized)

When the site system role installs, it installs and configures the data warehouse database. It also installs several reports so you can easily search for and report on this data.

## Prerequisites

- The data warehouse site system role is supported only at the top-tier site of your hierarchy. For example, a central administration site (CAS) or standalone primary site.
- Starting in version 2107, the server where you install this site system role requires .NET version 4.6.2, and version 4.8 is recommended. In version 2103 and earlier, this role requires .NET 4.5.2 or later. For more information, [Site and site system prerequisites](../../plan-design/configs/site-and-site-system-prerequisites#net-version-requirements).
- Grant the **Reporting Services Point Account** the **db\_datareader** permission on the data warehouse database.
- To synchronize data with the data warehouse database, Configuration Manager uses the computer account of the site system role. This account requires the following permissions:

    - **Administrator** on the computer that hosts the data warehouse database.
    - **DB\_Creator** permission on the data warehouse database.
    - Either **DB\_owner** or **DB\_reader** with **execute** permissions to the top-tier site's database.
- The data warehouse database requires the use of SQL Server 2012 or later. The edition can be Standard, Enterprise, or Datacenter. The SQL Server version for the data warehouse doesn't need to be the same as the site database server.
- The warehouse database supports the following SQL Server configurations:

    - A default or named instance
    - SQL Server Always On availability group
    - SQL Server Always On failover cluster instance
- If you use [distributed views](../../plan-design/hierarchy/database-replication#distributed-views), install the data warehouse service point on the same server that hosts the CAS's database.

For more information on SQL Server licensing, see the [product and licensing FAQ](../../understand/product-and-licensing-faq).

Size the data warehouse database the same as your site database. While the data warehouse is smaller at first, it will grow over time. 

## Install

Each hierarchy supports a single instance of this role, on any site system of the top-tier site. The SQL Server that hosts the database for the warehouse can be local to the site system role, or remote. The data warehouse works with the reporting services point installed at the same site. You don't need to install the two site system roles on the same server.

To install the role, use the **Add Site System Roles Wizard** or the **Create Site System Server Wizard**. For more information, see [Install site system roles](../deploy/configure/install-site-system-roles). On the **System Role Selection** page of the wizard, select the **Data Warehouse service point** role.

When you install the role, Configuration Manager creates the data warehouse database for you on the instance of SQL Server that you specify. If you specify the name of an existing database, Configuration Manager doesn't create a new database. Instead it uses the one you specify. This process is the same as when you move the data warehouse database to a new SQL Server.

### Configure properties

#### General page

- **SQL Server fully qualified domain name**: Specify the full qualified domain name (FQDN) of the server that hosts the data warehouse service point database.
- **SQL Server instance name, if applicable**: If you don't use a default instance of SQL Server, specify the named instance.
- **Database name**: Specify a name for the data warehouse database. Configuration Manager creates the data warehouse database with this name. If you specify a database name that already exists on the instance of SQL Server, Configuration Manager uses that database.
- **SQL Server port used for connection**: Specify the TCP/IP port number used by the SQL Server that hosts the data warehouse database. The data warehouse synchronization service uses this port to connect to the data warehouse database. By default, it uses SQL Server port **1433** for communication.
- **Data warehouse service point account**: Set the **User name** that SQL Server Reporting Services uses when it connects to the data warehouse database.

#### Synchronization settings page

- **Data Synchronization custom setting**: Choose the option to **Select tables**. In the Database tables window, select the table names to synchronize to the data warehouse database. Use the filter to search by name, or select the drop-down list to choose specific groups. Select **OK** when complete to save.

    Note

    You can't remove tables that the role selects by default.
- **Start time**: Specify the time that you want the data warehouse synchronization to start.
- **Recurrence pattern**

    - **Daily**: Specify that synchronization runs every day.
    - **Weekly**: Specify a single day each week, and weekly recurrence for synchronization.

## Reporting

After you install a data warehouse service point, several reports become available on the reporting services point for the site. If you install the data warehouse service point before installing a reporting services point, the reports are automatically added when you later install the reporting services point.

Note

The data warehouse point supports alternative credentials. Specify credentials that SQL Server Reporting Services uses to connect to the data warehouse database. Data warehouse reports don't open until you add credentials.

To specify an account, set the **User name** for the data warehouse service point account in the role properties. For more information, see Configure properties.

The data warehouse site system role includes the following reports, under the **Data Warehouse** category:

- **Application Deployment - Historical**: View details for application deployment for a specific application and machine.
- **Endpoint Protection and Software Update Compliance - Historical**: View computers that are missing software updates.
- **General Hardware Inventory - Historical**: View all hardware inventory for a specific machine.
- **General Software Inventory - Historical**: View all software inventory for a specific machine.
- **Infrastructure Health Overview - Historical**: Displays an overview of the health of your Configuration Manager infrastructure.
- **List of Malware Detected - Historical**: View malware that has been detected in the organization.
- **Software Distribution Summary - Historical**: A summary of software distribution for a specific advertisement and machine.

## Exclude data warehouse reporting tables from synchronization

(*Introduced in version 2203*)

When you install the data warehouse, it synchronizes a set of default tables from the site database. These tables are required for data warehouse reports. While troubleshooting issues, you may want to stop synchronizing these default tables. Starting in version 2203, you can exclude one or more of these required tables from synchronization. To exclude tables from synchronization:

1. From the **Administration** workspace, open **Site Configuration** &gt; **Servers and Site System Roles**.
2. Select the server where the data warehouse service point is installed.
3. In the **Site System Roles** details pane, select the **Data Warehouse service point** role, then select **Properties**.
4. On the **Synchronization settings** page, choose **Select tables**.
5. In the **Database tables** window, deselect one or more tables of type **Required**.
6. The console will prompt you to confirm the change, since some reports may no longer work correctly.

## Site expansion

Before you can install a CAS to expand an existing standalone primary site, first uninstall the data warehouse service point role. After you install the CAS, you can then install the site system role at the CAS.

Unlike a move of the data warehouse database, this change results in a loss of the historic data you have previously synchronized at the primary site. It isn't supported to back up the database from the primary site and restore it at the CAS.

## Move the database

Use the following steps to move the data warehouse database to a new SQL Server:

1. Use SQL Server Management Studio to back up the data warehouse database. Then, restore that database to a SQL Server on the new computer that hosts the data warehouse.

    Note

    After you restore the database to the new server, make sure the database access permissions are the same on the new data warehouse database as they were on the original data warehouse database.
2. Use the Configuration Manager console to remove the data warehouse service point role from the current server.
3. Reinstall the data warehouse service point. Specify the name of the new SQL Server and instance that hosts the restored data warehouse database.
4. After the site system role installs, the move is complete.

## Troubleshoot

### Log files

Use the following logs to investigate problems with the installation of the data warehouse service point, or synchronization of data:

- **DWSSMSI.log** and **DWSSSetup.log**: Use these logs to investigate errors when installing the data warehouse service point.
- **Microsoft.ConfigMgrDataWarehouse.log**: Use this log to investigate data synchronization between the site database to the data warehouse database.

### Set up failure

When the data warehouse service point role is the first one that you install on a remote server, installation fails for the data warehouse.

To work around this issue, make sure that the computer on which you install the data warehouse service point already hosts at least one other role.

### Synchronization failed to populate schema objects

Synchronization fails with the following message in **Microsoft.ConfigMgrDataWarehouse.log**: `failed to populate schema objects`

To work around this issue, make sure that the computer account of the site system role is a **db\_owner** on the data warehouse database.

### Reports fail to open

Data warehouse reports fail to open when the data warehouse database and reporting service point are on different site systems.

To work around this issue, grant the **Reporting Services Point Account** the **db\_datareader** permission on the data warehouse database.

### Error opening reports

When you open a data warehouse report, it returns the following error:

```Output
An error has occurred during report processing. (rsProcessingAborted)
Cannot create a connection to data source 'AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_'. (rsErrorOpeningConnection)
A connection was successfully established with the server, but then an error occurred during the pre-login handshake. (provider: SSL Provider, error: 0 - The certificate chain was issued by an authority that is not trusted.)
```

This issue should only occur when the site database and data warehouse database are on separate SQL Servers.

To work around this issue, use the following steps to configure certificates:

1. On the server that hosts the data warehouse database:

    1. Create a self-signed certificate. Open IIS, select **Server Certificates**, and then select the **Create Self-Signed Certificate** action. Specify the "friendly name" of the certificate name as **Data Warehouse SQL Server Identification Certificate**. Select the certificate store as **Personal**.

    Tip

    If this server doesn't already have IIS, install it first.

    1. Manage the certificate. Open the Microsoft Management Console (MMC), and add the **Certificates** snap-in. Select **Computer account** of the local machine. Expand the **Personal** folder, and select **Certificates**.

        1. Give the SQL Server service account read permissions to the certificate. Select the **Data Warehouse SQL Server Identification Certificate** certificate, then go to the **Action** menu, select **All Tasks**, and select **Manage Private Keys**. Add the SQL Server service account, and allow **Read** permission.
        2. Export the **Data Warehouse SQL Server Identification Certificate** as a **DER encoded binary X.509 (.CER)** file.
    2. Reconfigure SQL. Open **SQL Server Configuration Manager**.

        1. Under **SQL Server Network Configuration**, right-click to select **Properties** under **Protocols for MSSQLSERVER**. Switch to the **Certificate** tab, select **Data Warehouse SQL Server Identification Certificate** as the certificate, and then save the changes.
        2. Under **SQL Server Services**, restart the **SQL Server service**. If SQL Server Reporting Services is also installed on the server that hosts the data warehouse database, restart **Reporting Service** services as well.
2. On the server that hosts SQL Server Reporting Services, open the MMC, and add the **Certificates** snap-in. Select **Computer account**. Under the **Trusted Root Certificate Authorities** folder, import the **Data Warehouse SQL Server Identification Certificate**.

## Data flow

[![Diagram showing the logical data flow between site components for the data warehouse.](media/datawarehouse.png)](media/datawarehouse.png#lightbox)

### Data storage and synchronization

| Step | Details |
| --- | --- |
| **1** | The site server transfers and stores data in the site database. |
| **2** | Based on its schedule and configuration, the data warehouse service point gets data from the site database. |
| **3** | The data warehouse service point transfers and stores a copy of the synchronized data in the data warehouse database. |

### Reporting flow

| Step | Details |
| --- | --- |
| **A** | Using built-in reports, a user requests data. This request is passed to the reporting service point using SQL Server Reporting Services. |
| **B** | Most reports are for current information, and these requests are run against the site database. |
| **C** | When a report requests historical data by using one of the reports with a *Category* of **Data Warehouse**, the request runs against the data warehouse database. |