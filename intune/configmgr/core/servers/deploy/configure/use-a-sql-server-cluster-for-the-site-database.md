---
layout: Conceptual
title: Failover cluster instance - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database
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
description: Use a SQL Server Always On failover cluster instance to host the Configuration Manager site database
ms.date: 2020-10-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d6fe7f76-5de0-b9c0-f51f-0b6007b20b96
document_version_independent_id: 577cde4c-40e2-85ef-331d-3cc827310fdf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 010be7ef-f06e-a99a-ff72-16c8db0757a2
---

# Failover cluster instance - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use a SQL Server Always On failover cluster instance to host the Configuration Manager site database. Failover cluster instances provide failover support for the entire instance of SQL Server and improve the reliability of the site database. However, it doesn't provide additional processing or load-balancing benefits. Failover cluster instances require the use of shared storage, which can be a single point of failure. Degradation in performance can occur, because the site server must find the active node of the failover cluster instance before it connects to the site database.

Important

To successfully set up of a failover cluster instance, use the documentation and procedures for SQL Server. For more information, see [Always On Failover Cluster Instances (SQL Server)](/en-us/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server).

Before you install Configuration Manager, prepare the failover cluster instance to support Configuration Manager. For more information, see Prepare a clustered SQL Server instance.

During Configuration Manager setup, the Windows Volume Shadow Copy Service writer installs on each physical computer node of the Windows Server failover cluster. This service supports the **Backup Site Server** maintenance task.

After the site installs, Configuration Manager checks for changes to the cluster node each hour. Configuration Manager automatically manages any changes it finds that affect its component installs. For example, a node failover or the addition of a new node to the failover cluster instance.

## Supported options

Configuration Manager supports the following options for failover cluster instances used for the site database:

- A single instance cluster
- Multiple instance configurations
- Multiple active nodes
- Both a named or a default instance

## Prerequisites

- The site database server must be remote from the site server. The cluster can't include the site server.

    Note

    The Configuration Manager setup process doesn't block installation of the site server role on a computer with the Windows role for Failover Clustering. SQL Server Always On availability groups require this role, so previously you couldn't colocate the site database on the site server. With this change, you can create a highly available site with fewer servers by using an availability group and a site server in passive mode. For more information, see [High availability options](high-availability-options).
- Add the computer account of the site server to the local **Administrators** group of each server in the cluster.
- To support Kerberos authentication, enable the **TCP/IP** network communication protocol for the network connection of each cluster node. The **Named pipes** protocol isn't required, but can be used to troubleshoot Kerberos authentication issues. The network protocol settings are configured in **SQL Server Configuration Manager**, under **SQL Server Network Configuration**.
- There are specific certificate requirements when you use a failover cluster instance for the site database. For more information, see the following articles:

    - [Install a certificate in an Always On failover cluster instance configuration](/en-us/sql/database-engine/configure-windows/manage-certificates#provision-failover-cluster-cert)
    - [PKI certificate requirements for Configuration Manager](../../../plan-design/network/pki-certificate-requirements#pki-certificates-for-servers)

    Note

    If you don't pre-provision a certificate in SQL Server, Configuration Manager creates and provisions a self-signed certificate for SQL Server.

## Limitations

### Installation and configuration

- Secondary sites can't use a failover cluster instance.
- When you specify a failover cluster instance, you can't set a custom file location for the site database.

### SMS Provider

You can't install the SMS Provider on a failover cluster instance. It's also not supported on a computer that runs as a node participating in the failover cluster instance.

### Data replication options

If you use **Distributed Views**, you can't use a failover cluster instance to host the site database.

### Backup and recovery

Configuration Manager doesn't support System Center Data Protection Manager (DPM) backup for failover cluster instances that use a named instance. It does support DPM backup on failover cluster instances that use the SQL Server default instance.

## Prepare a failover cluster instance

Here are the main tasks to complete to prepare your site database:

- Create the failover cluster instance to host the site database on an existing Windows Server failover cluster environment. For specific steps to install and set up a failover cluster instance, see the documentation specific to your version of SQL Server. For more information, see [Create a new SQL Server Always On failover cluster instance](/en-us/sql/sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup).
- On each computer in the failover cluster instance, place a file in the root folder of each drive where you don't want Configuration Manager to install site components. Name the file `NO_SMS_ON_DRIVE.SMS`. By default, Configuration Manager installs some components on each physical node, to support operations such as backup.
- Add the computer account of the site server to the local **Administrators** group of each Windows Server failover cluster node.
- In the failover cluster instance, assign the **sysadmin** SQL Server role to the user account that runs Configuration Manager setup.

## Install a new site

To install a site that uses a clustered site database, run Configuration Manager setup following your normal process for installing a site. On the **Database Information** page, specify the name of the failover cluster instance. The failover cluster instance name replaces the name of a single computer that runs SQL Server.

Important

Make sure to use the name of the SQL Server Always On failover cluster instance, not the Windows Server failover cluster. If you use the Windows Server failover cluster name, the site database installs on the local hard drive of the active Windows Server failover cluster node. This configuration prevents successful failover if that node fails.