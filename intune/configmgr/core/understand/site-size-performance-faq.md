---
layout: FAQ
title: Site size and performance FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/site-size-performance-faq
summary: >
  <p><em>Applies to: Configuration Manager (current branch)</em></p>

  <p>This document addresses frequently asked questions about Configuration Manager site sizing guidance and common performance issues.</p>
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
description: Answers to common Configuration Manager questions about site sizing and performance.
ms.topic: faq
ms.date: 2022-02-15T00:00:00.0000000Z
locale: en-us
document_id: 78ab3e28-1e25-a0b4-70b7-f02c34ac6f97
document_version_independent_id: 73ee4954-c982-bc93-ff1b-6ef75f133490
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/site-size-performance-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/site-size-performance-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/site-size-performance-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: e15aea89-9304-38da-5034-44234132dbc7
---

# Site size and performance FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This document addresses frequently asked questions about Configuration Manager site sizing guidance and common performance issues.

## Machine and disk configuration

### How should I format the disks on my site server and SQL Server?

Separate the Configuration Manager inboxes and SQL Server files on at least two different volumes. This separation lets you optimize cluster allocation sizes for the different kinds of I/O they perform.

For the volume hosting your sites server inboxes, use NTFS with 4K or 8K allocation units. ReFS writes 64k even for small files. Configuration Manager has many small files, so ReFS can produce unnecessary disk overhead.

For disks containing SQL Server database files, use either NTFS or ReFS formatting, with 64K allocation units.

### How and where should I lay out my SQL Server database files?

Modern arrays of solid-state drives (SSD) and Azure Premium Storage can provide high IOPS on a single volume, with few disks. You typically add more drives to an array for additional storage, not additional throughput. If you're using physical spindle-based disks, you may need more IOPS than you can generate on a single volume. You should allocate 60% of the total recommended IOPS and disk space for the *.mdf* file, 20% for the *.ldf* file, and 20% for the log and data temp files. The *.ldf* and temp files can all reside on a single volume with 40% (20% + 20%) of your allocated IOPS.

SQL Server versions earlier than SQL Server 2016 created by default only one temp data file. You should create more, to avoid SQL Server locks and waiting for access to a single file. Community opinions vary on the best number of temp data files to create, from four to eight. Testing reveals little difference between four to eight, so you can create four *equally sized* temp data files. Your tempdb data files should be up to 20-25% the size of your full database.

### Are there any other recommendations for disk setup?

When configurable, set RAID controller memory to 70% allocation for write operations and 30% for read operations. In general, use a RAID 10 array configuration for the site database. RAID 1 is also acceptable for small-scale sites with low I/O requirements, or if you use fast SSDs. With larger disk arrays, configure spare disks to automatically replace failing disks.

**Example: Physical machine with physical disks**

[Sizing guidelines](../plan-design/configs/site-size-performance-guidelines#general-sizing-guidelines) for a colocated site server and SQL Server with **100,000** clients are 1200 IOPS for site server inboxes and 5000 IOPS for SQL Server files.

Your resulting disk configuration might look like:

| Drives^1^ | RAID | Format | Volume contents | Minimum IOPS needed | Approx. IOPS supplied^2^ |
| --- | --- | --- | --- | --- | --- |
| 2x10k | 1 | - | Windows |  | - |
| 6x15k | 10 | NTFS 8k | ConfigMgr inboxes | 1700 | 1751 |
| 12x15k | 10 | 64k ReFS | SQL .mdf | 60%\*5000 = 3000 | 3476 |
| 8x15k | 10 | 64k ReFS | SQL .ldf, temp files | 40%\*5000 = 2000 | 2322 |

1. Doesn't include recommended spare disks.
2. This value is from [Example disk configurations](../plan-design/configs/site-size-performance-guidelines#example-disk-configurations).

### I use Hyper-V on Windows Server. How should I configure the disks for my Configuration Manager VMs for best performance?

Hyper-V delivers similar performance to a physical server, if hardware resources (CPU cores and pass-through storage) are 100% dedicated to the virtual machine (VM). Using fixed-size *.vhd* or *.vhdx* disk files causes a minimal 1-5% I/O performance impact. Using dynamically expanding *.vhd* or *.vhdx* disk files causes up to 25% I/O performance impact for the Configuration Manager workload. If you need dynamically expanding disks, compensate by adding an additional 25% IOPS performance to the array.

When running your Configuration Manager site server or SQL Server inside a VM, isolate the Hyper-V host OS drives from the VM OS and data drives.

For more information about optimizing VMs, see [Performance Tuning Hyper-V Servers](/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/).

**Example: Hyper-V VM-based site server**

[Sizing guidelines](../plan-design/configs/site-size-performance-guidelines#general-sizing-guidelines) for a colocated site server and SQL Server with **150,000** clients are 1800 IOPS for site server inboxes and 7400 IOPS for SQL Server files.

Your resulting disk configuration might look like:

| Drives^1^ | RAID | Format^2^ | Volume contents | Minimum IOPS needed | Approx. IOPS supplied^3^ |
| --- | --- | --- | --- | --- | --- |
| 2x10k | 1 | - | Hyper-V host OS | - | - |
| 2x10k | 1 | - | (VM) site server OS | - | - |
| 2xSSD SAS | 1 | NTFS 8k | (VM) ConfigMgr inboxes | 1800 | 7539 |
| 4xSSD SAS | 10 | 64k ReFS | (VM) Host SQL Server (all files) | 7400 | 14346 |

1. Doesn't include recommended spare disks.
2. Fixed-size, pass-through *.vhdx* for the VM drive dedicated to the underlying volume.
3. This value is from [Example disk configurations](../plan-design/configs/site-size-performance-guidelines#example-disk-configurations).

### Are there any suggestions for Configuration Manager environments in Microsoft Azure?

Start by reading the [Configuration Manager on Azure frequently asked questions](configuration-manager-on-azure).

Azure infrastructure as a service (IaaS) VMs that leverage Premium Storage-based disks can have high IOPS. On these VMs, configure additional disks for anticipated disk space needs, rather than for additional IOPS.

Azure storage is inherently redundant and doesn't require multiple disks for availability. You can stripe disks in Disk Manager or Storage Spaces to provide additional space and performance.

For more information and recommendations on how to maximize Premium Storage performance and run SQL Servers in Azure IaaS VMs, see:

- [Optimize application performance](/en-us/azure/storage/storage-premium-storage-performance#optimize-application-performance)
- [Disks guidance](/en-us/azure/azure-sql/virtual-machines/windows/performance-guidelines-best-practices-checklist#storage)

**Example: Azure-based site server**

[Sizing guidelines](../plan-design/configs/site-size-performance-guidelines#general-sizing-guidelines) for a colocated site server and SQL Server with **50,000** clients are 8 cores, 32 GB, and 1200 IOPS for site server inboxes, and 2800 IOPS for SQL Server files.

Your resulting Azure machine might be a DS13v2 (8 cores, 56 GB) with the following disk configuration:

| Drives | Format | Contains | Minimum IOPS needed | Approx. IOPS supplied^1^ |
| --- | --- | --- | --- | --- |
| &lt;standard&gt; | - | Site server OS | - | - |
| 1xP20 (512 GB) | NTFS 8k | ConfigMgr inboxes | 1200 | 2334 |
| 1xP30 (1024 GB) | 64k ReFS | SQL Server (all files^2^) | 2800 | 3112 |

1. This value is from [Example disk configurations](../plan-design/configs/site-size-performance-guidelines#example-disk-configurations).
2. [Azure guidance](/en-us/azure/azure-sql/virtual-machines/windows/performance-guidelines-best-practices-checklist#storage) allows for placing the TempDB on the local, SSD-based *D:* drive, given it won't exceed available space and allows for additional disk I/O distribution.

**Example: Azure-based site server (for instant performance increase)**

Azure disk throughput is limited by the size of the VM. The configuration in the preceding Azure example may limit future expansion or additional performance. If you add additional disks during initial deployment of your Azure VM, you can upsize your Azure VM for increased processing power in the future, with minimal upfront investment. It's much simpler to plan ahead to increase site performance as requirements change, instead of later needing to do a more complicated migration.

Change the disks in the preceding Azure example to see how the IOPS change.

**DS13v2**

| Drives^1^ | Format | Contains | Minimum IOPS needed | Approx. IOPS supplied^2^ |
| --- | --- | --- | --- | --- |
| &lt;standard&gt; | - | Site server OS | - | - |
| 2xP20 (1024 GB) | NTFS 8k | ConfigMgr inboxes | 1200 | 3984 |
| 2xP30 (2048 GB) | 64k ReFS | SQL Server (all files^3^) | 2800 | 3984 |

1. Disks are striped using Storage Spaces.
2. This value is from [Example disk configurations](../plan-design/configs/site-size-performance-guidelines#example-disk-configurations). VM size limits performance.
3. [Azure guidance](/en-us/azure/azure-sql/virtual-machines/windows/performance-guidelines-best-practices-checklist#storage) allows for placing the TempDB on the local, SSD-based *D:* drive, given it won't exceed available space and allows for additional disk I/O distribution.

If you need more performance in future, you can upsize your VM to a DS14v2, which doubles CPU and memory. The additional disk bandwidth allowed by that VM size also instantly boosts the available disk IOPS on your previously configured disks.

**DS14v2**

| Drives^1^ | RAID | Format | Contains | Minimum IOPS needed | Approx. IOPS supplied^2^ |
| --- | --- | --- | --- | --- | --- |
| &lt;standard&gt; | - | Site server OS | - | - |  |
| 2xP20 (1024 GB) | NTFS 8k | ConfigMgr inboxes | 1200 | 4639 |  |
| 2xP30 (2048 GB) | 64k ReFS | SQL Server (all files^3^) | 2800 | 6182 |  |

1. Disks are striped using Storage Spaces.
2. This value is from [Example disk configurations](../plan-design/configs/site-size-performance-guidelines#example-disk-configurations). VM size limits performance.
3. [Azure guidance](/en-us/azure/azure-sql/virtual-machines/windows/performance-guidelines-best-practices-checklist#storage) allows for placing the TempDB on the local, SSD-based *D:* drive, given it won't exceed available space and allows for additional disk I/O distribution.

## SQL Server performance

### Is it better to run with SQL Server colocated with the site server, or run it on a remote server?

Both can perform adequately, assuming the single server is appropriately sized, or network connectivity is sufficient between the two servers.

Remote SQL Server requires the upfront and operational cost of an additional server, but is typical among the majority of large-scale customers. Benefits of this configuration include:

- Increased site availability options, such as SQL Server Always On
- Ability to run heavy reporting with less overheard to site processing
- Simpler disaster recovery in some situations
- Easier security management
- Role separation for SQL Server management, such as with a separate DBA team

Colocated SQL Server requires a single server, and is typical for most small-scale customers. Benefits of this configuration include:

- Lower costs for machines, licenses, and maintenance
- Fewer points of failure in the site
- Better control for planning downtime

### How much RAM should I allocate for SQL?

By default, SQL Server uses all available memory on your server, potentially starving the OS and other processes on the machine. To avoid potential performance issues, it's important to allocate memory to SQL Server explicitly. On site servers colocated with SQL Server, make sure the OS has enough RAM for file caching and other operations. Make sure there's enough RAM remaining for SMSExec and other Configuration Manager processes. When running SQL Server on a remote server, you can allocate the *majority* of the memory to SQL, but not all. Review the [sizing guidelines](../plan-design/configs/site-size-performance-guidelines#general-sizing-guidelines) for initial guidance.

SQL Server memory allocation should be rounded to whole GB. Also, as RAM increases to large amounts, you can let SQL Server have a higher percentage. For example, when 256 GB or more of RAM is available, you can configure SQL Server for up to 95%, as that still preserves plenty of memory for the OS. Monitoring the page file is a good way to ensure there is enough memory for the OS and any Configuration Manager processes.

### Cores are cheap these days. Should I just add a bunch of them to my SQL Server?

You may run into memory contention issues if there are more than 16 physical cores and not enough RAM on your SQL Server. The Configuration Manager workload performs better when at least 3-4 GB of RAM per core is available for SQL. When adding cores to your SQL Server, be sure to increase RAM in proportional amounts.

### Will a SQL Server Always On availability group impact my performance?

In general, availability groups have negligible effect on performance of the system when sufficient networking is available between the replica servers. You can have rapid database log *.ldf* file growth in a busy availability group environment. However, log file space is automatically released after a successful database backup. Add a SQL Server job for the Configuration Manager database to perform a backup, for example every 24 hours, and an *.ldf* backup every six hours. For more information about availability groups and Configuration Manager, including more about SQL Server backup strategies, see [Prepare to use a SQL Server Always On availability group](../servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

### Should I enable SQL Server compression on my database?

SQL Server compression isn't recommended for the Configuration Manager database. While there are no functional issues with enabling compression on a Configuration Manager database, test results don't show much size savings compared to the potential sizable performance impact to the system.

### Should I enable SQL Server encryption on my database?

Any secrets in the Configuration Manager database are already stored securely, but adding SQL Server encryption can add yet another layer of security. There are no functional issues with enabling encryption on your database, but there can be up to a 25% performance degradation. Therefore, encrypt with caution, especially in large-scale environments. Also remember to update your backup and recovery plans to ensure you can successfully recover the encrypted data.

### What version of SQL Server should I run?

For supported versions of SQL, see [Support for SQL Server versions](../plan-design/configs/support-for-sql-server-versions). From a performance standpoint, all supported versions of SQL Server meet required performance criteria. Upgrading SQL Server in place doesn't update compatibility levels.

If you see unusual timeouts or slowness on certain SQL queries on SQL Server 2016 or later, such as when using RBAC in the Admin Console, try changing the SQL Server compatibility level on the Configuration Manager database to 110. Running at SQL Server compatibility level 110 on SQL Server 2014 and newer versions of SQL Server is fully supported. For more information, see [SQL query times out or console slow on certain Configuration Manager database queries](/en-us/troubleshoot/mem/configmgr/console-management/sql-query-times-out-or-console-slow-performance).

As of January 2018, you should *avoid* the following SQL Server versions, because of various known performance-related or other potential issues:

- SQL Server 2012 SP3 CU1 to CU5
- SQL Server 2014 SP1 CU6 to SP2 CU2
- SQL Server 2016 RTM to CU3, SP1 CU3 to CU5

### Should I implement any additional SQL Server maintenance tasks?

The built-in ["Rebuild Indexes" maintenance task](../servers/manage/reference-for-maintenance-tasks#rebuild-indexes) rebuilds only highly fragmented indexes. The Query Optimizer then updates statistics on related objects as described in [After Maintenance Operations](/en-us/sql/relational-databases/statistics/statistics#after-maintenance-operations) section in SQL documentation. Therefore, if you rely solely on this built-in task, statistics may not be updated on some tables and views, leading to suboptimal query plans and poor performance.

You should perform [index maintenance](/en-us/sql/relational-databases/indexes/reorganize-and-rebuild-indexes) as often as once a week and [update statistics](/en-us/sql/t-sql/statements/update-statistics-transact-sql) of tables and views as often as once a day to maintain SQL Server performance.

There is no one-size-fits-all approach to database maintenance. The optimal strategy depends on factors such as database size, workload characteristics, and operational requirements. Engaging an in-house SQL Server expert or a Microsoft Cloud Solution Architect (CSA) can help you design the maintenance strategy tailored to your environment.

Additional guidance is available from the Configuration Manager and SQL Server communities, including non-Microsoft maintenance scripts. The [SQL Recommendations for MECM](https://github.com/stephaneserero/Sql-recommendations-for-MECM) whitepaper summarizes Microsoft CSAs' field experience on SQL maintenance and tuning.

In large sites, some database tables, such as CI\_CurrentComplianceStatusDetails, HinvChangeLog, might be large, depending on your usage patterns. You may need to reduce or alter your approach to maintain these one by one.

### When should I use full SQL Server instead of SQL Server Express on my secondary sites?

SQL Server Express doesn't have any significant performance implications on secondary sites, and it's adequate for most customers. It's also easy to deploy and manage, and is the recommended configuration for nearly all customers at any size.

There's one situation where a full SQL Server installation might be needed. If you have a large number of distribution points and packages or sources in your environment, it's possible to exceed the 10-GB size limit of SQL Server Express. If the number of packages times the number of distribution points is more than 4,000,000, such as 2,000 DPs with 2,000 pieces of content, consider using full SQL Server at your secondary sites.

### Should I change MaxDOP settings on my database?

Leaving your setting at 0 (use all available processors) is optimal for overall processing performance in most circumstances.

Many Configuration Manager administrators follow the guidance at [Recommendations and guidelines for the "max degree of parallelism" configuration option in SQL Server](/en-us/sql/database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option). On most modern large hardware, this guidance leads to a suggested maximum setting of eight. However, if you run many smaller queries compared to your number of processors, it may help to set it to a higher number. Limiting yourself to eight isn't necessarily the best setting on larger sites when more cores are available.

On SQL Servers with greater than eight cores, start with a setting of 0, and only make changes if you experience performance issues or excessive locking. If you need to change MaxDOP because you are encountering performance issues at 0, start with a new value at least greater than or equal to the minimum recommended number of cores for that site's SQL Server sizing. Going lower than this value nearly always has negative performance implications. For example, a remote SQL Server for a 100,000 client site needs at least 12 cores. If your SQL Server has 16 cores, start testing your MaxDOP setting with a value of 12.

## Anti-malware configuration

### Which folders on the site server (or other roles) should I exclude for antivirus software?

Take care when disabling antivirus protection on any system. In high volume and secure environments, we recommend disabling *active monitoring* for optimum performance.

For more information about recommended antivirus exclusions, see [Recommended antivirus exclusions for Configuration Manager site servers, site systems, and clients](/en-us/troubleshoot/mem/configmgr/endpoint-protection/recommended-antivirus-exclusions).

## WSUS Maintenance

### What can I do to make WSUS perform better when it's used with Configuration Manager?

Changing a few key IIS settings, such as WsusPool Queue Length and WsusPool Private Memory limit, can improve WSUS performance, even on smaller installations. For more information, see [WSUS note at Recommended hardware](../plan-design/configs/recommended-hardware#bkmk_note2).

Also make sure you have the latest updates installed for the operating system running WSUS:

- Windows Server 2012: Any non "Security only" cumulative update released October 2017 or later. ([KB4041690](https://support.microsoft.com/help/4041690/windows-server-2012-update-kb4041690))
- Windows Server 2012 R2: Any non "Security only" cumulative update released August 2017 or later. ([KB4039871](https://support.microsoft.com/help/4039871/windows-8-1-windows-server-2012-r2-update-kb4039871))
- Windows Server 2016: any non "Security only" cumulative update released August 2017 or later. ([KB4039396](https://support.microsoft.com/help/4039396/windows-10-update-kb4039396))

### What type of maintenance should I run on my WSUS servers?

See [The complete guide to Microsoft WSUS and Configuration Manager SUP maintenance](/en-us/troubleshoot/mem/configmgr/update-management/wsus-maintenance-guide).

### I want to set up basic performance monitoring for my site. What should I watch?

Traditional server performance monitoring works effectively for general Configuration Manager. You can also leverage monitoring solutions like the Azure Monitor to monitor basic health of your servers: see [ConfigMgr Performance Baseline the Easy Way](https://techcommunity.microsoft.com/blog/coreinfrastructureandsecurityblog/configmgr-performance-baseline-the-easy-way/1583081) blog post. You can also directly monitor the Windows Performance Monitor (PerfMon) counters Configuration Manager provides. Monitor the backlogs in the various inboxes for early warning signs of potential site performance issues or backlogs.