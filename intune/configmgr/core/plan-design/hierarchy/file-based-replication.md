---
layout: Conceptual
title: File-based replication - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/file-based-replication
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
description: Learn how Configuration Manager uses file-based replication to transfer data between sites in your hierarchy
ms.date: 2019-08-09T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ba90da2c-368a-36de-849e-7d432f49c019
document_version_independent_id: 77a8a10b-46a1-5137-e417-984fed0287be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/file-based-replication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/file-based-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/file-based-replication.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5e6a0bec-e889-3b4f-80e3-ded93dfd42bd
---

# File-based replication - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager uses file-based replication to transfer file-based data between sites in your hierarchy. This data includes applications and packages that you want to deploy to distribution points in child sites. It also handles unprocessed discovery data records that the site transfers to its parent site and then processes.

File-based communication between sites uses the *server message block* (SMB) protocol on TCP/IP port 445. To control the amount of data the site transfers across the network, specify bandwidth throttling and pulse mode. Use schedules to control when to send data across the network.

## Routes

The following information can help you set up and use file replication routes.

### File replication route

Each file replication route identifies a destination site to which a site transfers file-based data. Each site supports one file replication route to a specific destination site.

To manage a file replication route, go to the **Administration** workspace. Expand the **Hierarchy Configuration** node, and then select **File Replication**.

You can change the following settings for file replication routes:

#### File replication account

This account connects to the destination site, and writes data to that site's **SMS\_Site** share. The receiving site processes the data written to this share. By default, when you add a site to the hierarchy, Configuration Manager assigns the new site server's computer account as its file replication account. It then adds this account to the destination site's `SMS_SiteToSiteConnection_<sitecode>` group. This group is local to the computer that grants access to the SMS\_Site share. You can change this account to be a Windows user account. If you change the account, make sure you add the new account to the destination site's `SMS_SiteToSiteConnection_<sitecode>` group.

Note

Secondary sites always use the computer account of the secondary site server as the **File Replication Account**.

#### Schedule

Set the schedule for each file replication route. This action restricts the type of data and time when data can transfer to the destination site.

#### Rate limits

Specify rate limits for each file replication route. This action controls the network bandwidth the site uses when it transfers data to the destination site:

- **Pulse mode**: Specify the size of the data blocks that the site sends to the destination site. You can also specify a time delay between sending each data block. Use this option when you must send data across a low-bandwidth network connection to the destination site.

    For example, you have constraints to send 1 KB of data every five seconds, but not 1 KB every three seconds. This constraint is regardless of the speed of the link or its usage at a given time.
- **Limited to maximum transfer rates by hour**: The site sends data to a destination site by using only the percentage of time that you specify. Configuration Manager doesn't identify the network's available bandwidth. It divides the time it can send data into slices of time. It then sends the data in a short block of time, which is followed by blocks of time when it doesn't send data.

    For example, you set the maximum rate to **50%**. Configuration Manager transmits data for an amount of time followed by an equal period of time when it doesn't send any data. It doesn't manage the actual size of the data block that it sends. The site only manages the amount of time during which it sends data.

Caution

By default, a site can use up to three **concurrent sendings** to transfer data to a destination site. When you enable rate limits for a file replication route, it limits the **concurrent sendings** to that site to one. This behavior applies even when the **Limit available bandwidth (%)** is set to **100%**. For example, if you use the default settings for the sender, this reduces the transfer rate to the destination site to be one-third of the default capacity.

#### Routes between secondary sites

Configure a file replication route between two secondary sites to route file-based content between those sites.

### Sender

Each site has one sender. The sender manages the network connection from one site to a destination site. It can establish connections to multiple sites at the same time. To connect to a site, the sender uses the file replication route to the site and identifies the account it uses to establish the network connection. The sender also uses this account to write data to the destination site's SMS\_Site share.

By default, the sender writes data to a destination site by using multiple **concurrent sendings**, or a *thread*. Each thread can transfer a different file-based object to the destination site. When the sender begins to send an object, it continues to write blocks of data for that object until it sends the entire object. After it sends all the data for the object, a new object can begin to send on that thread.

To manage the sender for a site, go to the **Administration** workspace, and expand the **Site Configuration** node. Select the **Sites** node, and then select **Properties** for the site you want to manage. Switch to the **Sender** tab to change the sender settings.

You can change the following settings for a sender:

#### Maximum concurrent sendings

By default, each site uses five concurrent sendings (threads). Three threads are available for use when it sends data to any one destination site. When you increase this number, you can increase the throughput of data between sites. More threads mean that Configuration Manager can transfer more files at the same time. Increasing this number also increases the demand for network bandwidth between sites.

#### Retry settings

By default, each site retries a problem connection two times, with a one-minute delay between connection attempts. You can modify the number of connection attempts the site makes, and how long to wait between attempts.