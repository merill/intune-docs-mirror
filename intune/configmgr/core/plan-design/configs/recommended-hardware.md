---
layout: Conceptual
title: Recommended hardware - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/recommended-hardware
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
description: Get hardware recommendations to help you scale your Configuration Manager environment beyond a basic deployment.
ms.date: 2021-03-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 71c362cc-3c61-a76f-63e9-0959247b1f47
document_version_independent_id: e5bfb6ea-af69-cf8b-85ce-a5b9bddc8ddd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/recommended-hardware.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/recommended-hardware
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/recommended-hardware.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 63d5e452-3649-abf9-5acb-56b4d520fbb9
---

# Recommended hardware - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The following recommendations are guidelines to help you scale your Configuration Manager environment to support more than a very basic deployment of sites, site systems, and clients. They aren't intended to cover all possible site and hierarchy configurations.

Use the information in the following sections as a guide to help you plan for hardware. Make sure your hardware can meet the processing loads for clients and sites that use the available Configuration Manager features.

## Site systems

This section provides recommended hardware configurations for Configuration Manager site systems. Use these recommendations to support the maximum number of clients and use most or all Configuration Manager features. If your environment supports less than the maximum number of clients, and doesn't use all available features, it might require less resources. In general, the following key factors limit performance of the overall system:

1. Disk I/O performance
2. Available memory
3. CPU

For best performance, use RAID 10 configurations for all data drives and a 1-Gbps Ethernet network.

### Site servers

| Site configuration | CPU (cores) | Memory (GB) | Memory allocation for SQL Server (%) |
| --- | --- | --- | --- |
| Stand-alone primary site server with a database site role on the same server ^Note 1^ | 16 | 96 | 80 |
| Stand-alone primary site server with a remote site database | 8 | 16 | - |
| Remote database server for a stand-alone primary site | 16 | 72 | 90 |
| Central administration site server with a database site role on the same server ^Note 1^ | 20 | 128 | 80 |
| Central administration site server with a remote site database | 8 | 16 | - |
| Remote database server for a central administration site | 16 | 96 | 90 |
| Child primary site with a database site role on the same server | 16 | 96 | 80 |
| Child primary site server with a remote site database | 8 | 16 | - |
| Remote database server for a child primary site | 16 | 72 | 90 |
| Secondary site server | 8 | 16 | - |

#### Note 1: Collocated SQL

When you install the site server and SQL Server on the same computer, the deployment supports the maximum [sizing and scale numbers](size-and-scale-numbers) for sites and clients. This configuration can limit [high availability options](../../servers/deploy/configure/high-availability-options), like using a SQL Server Always On failover cluster instance. If you have a larger environment, because of the higher I/O requirements to support both roles on the same computer, consider using a remote SQL Server.

### Remote site system servers

The following guidance is for computers that hold a single site system role. Plan to adjust when you install multiple site system roles on the same computer.

| Site system role | CPU (cores) | Memory (GB) | Disk space (GB) |
| --- | --- | --- | --- |
| Management point | 4 | 8 | 50 |
| Distribution point | 2 | 8 | As required by the OS and to store content that you deploy |
| Software update point ^Note 2^ | 8 | 16 | As required by the OS and to store updates that you deploy |
| All other site system roles | 4 | 8 | 50 |

#### Note 2: WSUS configurations

The computer that hosts a software update point requires the following configurations for IIS application pools:

- Increase the **WsusPool Queue Length** to **2000**.
- Increase the **WsusPool Private Memory limit** by four times, or set it to **0** (unlimited).

### Disk space for site systems

Disk allocation and configuration contribute to the performance of Configuration Manager. Because each Configuration Manager environment is different, the values that you implement can vary from the following guidance.

For the best performance, place each object on a separate, dedicated RAID volume. For all data volumes for Configuration Manager and its database files, use RAID 10 for the best performance.

| Data usage | Minimum disk space | 25,000 clients | 50,000 clients | 100,000 clients | 150,000 clients | 700,000 clients (central administration site) |
| --- | --- | --- | --- | --- | --- | --- |
| Configuration Manager application and log files | 25 GB | 50 GB | 100 GB | 200 GB | 300 GB | 200 GB |
| Site database .mdf file | 75 GB for every 25,000 clients | 75 GB | 150 GB | 300 GB | 500 GB | 2 TB |
| Site database .ldf file | 25 GB for every 25,000 clients | 25 GB | 50 GB | 100 GB | 150 GB | 100 GB |
| Temp database files (.mdf and .ldf) | As needed | As needed | As needed | As needed | As needed | As needed |

For the Windows system disk, see sizing guidance for the installed OS version.

For content on distribution points, it depends upon your deployments. This guidance doesn't include the disk space required for the content library on the site server or distribution points. For more information, see [The content library](../hierarchy/the-content-library).

When you plan for disk space requirements, consider the following guidelines:

- Each client requires about 5-10 MB of space in the database. This number depends upon the hierarchy type, the configuration, and the number of clients. The size can be less for larger environments. Smaller sites have greater database usage per client.
- For the primary site's temp database, plan for a combined size that is 25% to 30% of the site database .mdf file. The actual size can be smaller or larger. It depends on the performance of the site server and the volume of incoming data over both short and long periods of time.

    Note

    When you have 50,000 or more clients at a site, plan to use four or more temp database .mdf files.
- The temp database size for a central administration site is typically much smaller than for a primary site.
- If you use SQL Server Express for the secondary site database, it limits the database size to 10 GB.

## Clients

This section provides recommended hardware configurations for computers that you manage by using Configuration Manager client software.

### Client for Windows computers

The following minimum requirements are for Windows-based computers that you manage by using Configuration Manager, including embedded editions:

- **Processor and memory:** Refer to the processor and RAM requirements for the OS.
- **Disk space:** 500 MB of available disk space, with 5 GB recommended for the Configuration Manager client cache. If you use customized settings to install the Configuration Manager client, less disk space is required.

    - Use the client.msi property **SMSCACHESIZE** to set a cache size smaller than the default of 5120 MB. The minimum size is 1 MB. The following example creates a 2-MB cache: `CCMSetup.exe SMSCACHESIZE=2`

        For more information, see [About client installation properties](../../clients/deploy/about-client-installation-properties).

        Tip

        Installing the client with minimal disk space is useful for Windows Embedded devices that typically have smaller disk sizes than standard Windows computers.

The following minimum hardware requirements are for optional functionality in Configuration Manager:

- **OS deployment:** At least 384 MB of RAM
- **Software Center:** At least a 500-MHz processor
- **Remote Control:** For an optimal experience, at least a Pentium 4 Hyper-Threaded 3 GHz (single core) or comparable CPU, with at least 1-GB RAM.

## Configuration Manager console

The following minimum hardware requirements apply to each computer that runs the Configuration Manager console:

- Intel i3 or comparable CPU
- 2 GB of RAM
- 2 GB of disk space

| DPI setting | Minimum resolution |
| --- | --- |
| 96 / 100% | 1024 x 768 |
| 120 /125% | 1280 x 960 |
| 144 / 150% | 1600 x 1200 |
| 196 / 200% | 2500 x 1600 |

## Lab deployments

Use the following minimum hardware recommendations for lab and test deployments of Configuration Manager. These recommendations apply to all site types, up to 100 clients:

| Role | CPU (cores) | Memory (GB) | Disk space (GB) |
| --- | --- | --- | --- |
| Site and database server | 2 - 4 | 8 - 12 | 100 |
| Site system server | 1 - 4 | 2 - 4 | 50 |
| Client | 1 - 2 | 1 - 3 | 30 |