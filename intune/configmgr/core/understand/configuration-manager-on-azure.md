---
layout: FAQ
title: Configuration Manager on Azure FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/configuration-manager-on-azure
summary: >
  <p><em>Applies to: Configuration Manager (current branch)</em></p>

  <p>These frequently asked questions (FAQ) about Configuration Manager on Microsoft Azure can help you understand when to use it and how to configure it.</p>
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
description: Frequently asked questions about using Configuration Manager on an Azure environment.
ms.date: 2021-07-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: faq
locale: en-us
document_id: c839c644-12fe-b28c-f269-d833f1d8532b
document_version_independent_id: 2c974db5-592d-0736-e211-dcb762f3527c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/configuration-manager-on-azure.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/configuration-manager-on-azure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/configuration-manager-on-azure.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 01d056a4-d2df-18de-ed96-403cbd174618
---

# Configuration Manager on Azure FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

These frequently asked questions (FAQ) about Configuration Manager on Microsoft Azure can help you understand when to use it and how to configure it.

## General questions

### Can I move on-premises Configuration Manager servers to Azure?

Yes, this scenario is supported. For more information, see [Support for virtualization environments](../plan-design/configs/support-for-virtualization-environments#bkmk_Azure).

### Should all child primary sites be in Azure with the central administration site or on-premises? What about secondary sites?

[File-based and database replication](../plan-design/hierarchy/data-transfers-between-sites) for site-to-site communications benefit from the proximity of being hosted in Azure. However, all client-related traffic would be remote from site servers and site systems. If you use a fast and reliable network connection between Azure and your intranet with an unlimited data plan, hosting all your infrastructure in Azure is an option.

If you use a metered data plan and available bandwidth or cost is a concern, then consider placing specific sites and site systems on-premises. Then use the bandwidth controls built into Configuration Manager. Also consider this configuration when the network connection between Azure and your intranet isn't fast or can be unreliable.

### Is Configuration Manager in Azure considered software as a service (SaaS)?

No, it's infrastructure as a service (IaaS). You host your Configuration Manager infrastructure servers in Azure virtual machines.

### What factors are most important when considering to move Configuration Manager to Azure?

1. Networking
2. Availability
3. Performance
4. Cost
5. User Experience

For more information on these factors, see the other questions below.

### Can I use Configuration Manager with Azure Stack Hub?

Yes. [Azure Stack Hub](/en-us/azure-stack/operator) supports IaaS virtual machines the same as the Azure cloud. So Configuration Manager is supported on Azure Stack Hub in the same way as with Azure IaaS.

Configuration Manager cloud-attached features that rely on specific cloud services aren't supported with Azure Stack Hub. For example, you can't create a cloud management gateway (CMG) in Azure Stack Hub.

## Networking

### Should I use ExpressRoute or an Azure VPN Gateway?

Microsoft recommends using ExpressRoute. Network speeds and latency can affect functionality between the site server and remote site systems and between any client communication to the site systems.

There's no limitation in Configuration Manager for using Azure VPN Gateway. You should carefully review the following requirements from this infrastructure and then make your decision:

- Performance
- Patching
- Software distribution
- OS deployment

Consider the following aspects for each solution:

#### ExpressRoute (recommended)

- Natural extension to your datacenter and can link together multiple datacenters
- Private connections between Azure datacenters and your infrastructure
- Doesn't go over the public internet
- Offers reliability, fast speeds, lower latency, high security
- Offers up to 10 Gbps speeds and unlimited data plan options

#### VPN Gateway

- Site-to-site or point-to-site VPNs
- Traffic goes over the public internet
- Uses Internet Protocol Security (IPsec) and Internet Key Exchange (IKE)

For more information, see [ExpressRoute or Azure VPN](https://azure.microsoft.com/blog/expressroute-or-virtual-network-vpn-whats-right-for-me/).

### Which ExpressRoute options should I choose?

It depends. ExpressRoute has many different options like unlimited or metered, different speed options, and premium add-ons. The options you select depend on the Configuration Manager functionality you're using and how much data you plan to distribute. You can control the transfer of Configuration Manager data between site servers and distribution points, but you can't control site server-to-site server communication. When you use a metered data plan, if you place specific sites and site systems on-premises, and use [Configuration Manager's built-in bandwidth controls](../plan-design/hierarchy/fundamental-concepts-for-content-management), you can help control the cost of using Azure.

### Do I still need to join my site servers to an Active Directory domain?

Yes. When you move to Azure, the [supported configurations](../plan-design/configs/supported-configurations) remain the same, including Active Directory requirements for installing Configuration Manager.

### Can I use Microsoft Entra ID?

No. Microsoft Entra ID isn't currently supported. Your site servers still need to be members of a [Active Directory domain](../plan-design/configs/support-for-active-directory-domains).

## Availability

### Can I use high availability options like Azure VM availability sets with Configuration Manager?

Yes. You can use Azure VM availability sets for redundant site system roles like distribution points or management points.

You can also use them for the Configuration Manager site servers. For example, central administration sites and primary sites can all be in the same availability set. This configuration can help you make sure that they're not rebooted at the same time.

For more information, see [Availability options for Azure Virtual Machines](/en-us/azure/virtual-machines/availability) and [High availability options for Configuration Manager](../servers/deploy/configure/high-availability-options).

### Can I use an Azure SQL Server database?

No. You need to use SQL Server in a VM. Configuration Manager doesn't currently support Azure SQL Server.

For high availability of the site database server, use SQL Server Always On availability groups. For more information, see [Prepare to use a SQL Server Always On availability group with Configuration Manager](../servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

### Can I use Azure load balancers with site system roles like management points or software update points?

Configuration Manager isn't tested with [Azure load balancers](/en-us/azure/load-balancer/load-balancer-overview). If the functionality is transparent to the application, it shouldn't have any adverse effects on normal operations.

## Performance

### What factors affect performance in this scenario?

The following factors are the most important to Configuration Manager performance on Azure:

- [Azure VM size and type](/en-us/azure/virtual-machines/sizes)
- Azure VM disks: premium storage is recommended, especially for SQL Server
- Network latency and speed

### What size VMs should I use?

In general, your compute power (CPU and memory) need to meet the [recommended hardware for Configuration Manager](../plan-design/configs/recommended-hardware). But there are some differences between regular computer hardware and Azure VMs, especially when it comes to the disks these VMs use. The VM size you use depends on the size of your environment.

The following list includes some general recommendations for VM size:

- For production deployments of any significant size, use **S** class Azure VMs. These VMs can use premium storage disks. Non **S** class VMs use blob storage and in general won't meet the performance requirements necessary for an acceptable production experience.
- Use multiple premium storage disks for higher scale, and striped in the Windows Disk Management console for maximum IOPS.
- Use better or multiple premium disks during your initial site deployment. For example, **P30** instead of **P20**, and two **P30** disks in a striped volume, instead of a single **P30**. If your site later needs to increase VM size due to additional load, you can take advantage of the additional CPU and memory that a larger VM size provides. You'll also already have disks in place that can take advantage of the additional IOPS throughput that the larger VM size allows.

The following tables list the initial suggested disk counts to use at primary and central administration sites for various size installations:

#### Co-located site database

A primary or central administration site with the site database on the site server:

| Desktop clients | Recommended VM size | Recommended disks |
| --- | --- | --- |
| &lt; 25,000 | DS4\_V2 | 2xP30 (striped) |
| 25,000 to 50,000 | DS13\_V2 | 2xP30 (striped) |
| 50,000 to 100,000 | DS14\_V2 | 3xP30 (striped) |

#### Remote site database

A primary or central administration site with the site database on a remote server:

| Desktop clients | Recommended VM size | Recommended disks |
| --- | --- | --- |
| &lt; 25,000 | Site server: F4S Database server: DS12\_V2 | Site server: 1xP30 Database server: 2xP30 (striped) |
| 25,000 to 50,000 | Site server: F4S Database server: DS13\_V2 | Site server: 1xP30 Database server: 2xP30 (striped) |
| 50,000 to 100,000 | Site server: F8S Database server: DS14\_V2 | Site server: 2xP30 (striped) Database server: 3xP30 (striped) |

#### Example

This image shows an example disk configuration for the following VM:

- A DS14\_V2 size VM for a site that manages 50,000 to 100,000 clients
- Three P30 disks in a striped volume
- Separate logical volumes for the Configuration Manager install and database files

![Example disk management configuration for a site on an Azure VM](media/vm_disks.png)

## User experience

### Why is user experience a main area of importance?

The decisions you make for networking, availability, performance, and site server location can directly affect your users. Moving a site to Azure should be transparent to your users so that they don't experience a change in their day-to-day interactions with Configuration Manager.

### To keep costs low for a single primary site, should remote site systems be in Azure or on-premises?

Except for communication from the site server to a distribution point, these server-to-server communications in a site can occur at any time and don't use mechanisms to control the use of network bandwidth. Because you can't control the communication between site systems like management points and software update points, make sure to consider any costs associated with these communications.

Network speeds and latency are other factors to consider as well. Slow or unreliable networks could impact functionality between the site server and remote site systems, and client communication to the site systems. Factor in the number of managed clients that use a given site system and the features you actively use.

As a starting point, you can use the standard guidance for site systems across WAN links. Ideally, the network throughput that you select and receive between Azure and your intranet will be consistent with a WAN that is well-connected with a fast network.

### What about content distribution and content management?

The approach for content management is much the same as for site servers and site systems.

- If you use a fast and reliable network connection between Azure and your intranet with an unlimited data plan, hosting standard distribution points in Azure could be an option.
- If any of the following factors apply:

    - You use a metered data plan
    - Bandwidth cost is a concern
    - The network connection between Azure and your intranet isn't fast or can be unreliable

    Then you might consider the following other approaches:

    - Use standard or pull distribution points on-premises.
    - Enable Windows BranchCache on distribution points or other [peer caching technologies](../plan-design/hierarchy/fundamental-concepts-for-content-management#peer-caching-technologies).
    - Use a content-enabled [cloud management gateway](../clients/manage/cmg/overview) (CMG). Note that it doesn't support software update packages for Microsoft updates. You need to have an alternate location, or configure the software update deployment need to allow clients to get update content from the internet.

Note

If you require PXE or multicast support, you need an on-premises distribution point to respond to these boot requests.

### To support internet-based clients, what can I do instead of using an internet-facing management point?

Use a [cloud management gateway](../clients/manage/cmg/overview) (CMG). The CMG provides a simple way to manage Configuration Manager clients on the internet. You deploy the service to an Azure subscription, and it connects to your on-premises infrastructure through the cloud management gateway connector point. Clients can then access on-premises site system roles whether they're connected to the internal network or on the internet.

### Which peer caching technology should I use?

[Peer cache](../plan-design/hierarchy/client-peer-cache) is a 100% native Configuration Manager technology. [BranchCache](../plan-design/configs/support-for-windows-features-and-networks#bkmk_branchcache) and [Delivery Optimization](../plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization) are Windows features. They can all be useful depending upon your requirements. For more information, including a table to compare features, see [Content management fundamentals - Peer caching technologies](../plan-design/hierarchy/fundamental-concepts-for-content-management#peer-caching-technologies).

## Cost

### Will moving Configuration Manager to Azure be a cost-effective solution for my organization?

It's hard to say since every environment is different. To estimate the cost for your environment, use the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/).

## More information

### Where I can learn more about these Azure technologies?

#### Fundamentals

- [What is Azure](https://azure.microsoft.com/overview/what-is-azure/)

#### Azure VM machine types

- [Azure machine sizes](/en-us/azure/virtual-machines/sizes)
- [VM pricing](https://azure.microsoft.com/pricing/details/virtual-machines/windows/)
- [Storage pricing](https://azure.microsoft.com/pricing/details/storage/)

#### Disk performance considerations

- [Premium storage](/en-us/azure/virtual-machines/premium-storage-performance)
- [Select a disk type of IaaS VMs](/en-us/azure/virtual-machines/disks-types#premium-ssd)
- [Scalability and performance targets for standard storage accounts](/en-us/azure/storage/common/scalability-targets-standard-account)
- [Blog post on how premium storage works](https://azure.microsoft.com/blog/azure-premium-storage-now-generally-available-2/)

#### Availability

- [Azure service level agreement (SLA) for virtual machines](https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/)
- [Availability options for Azure Virtual Machines](/en-us/azure/virtual-machines/availability)

#### Connectivity

- [ExpressRoute or Azure VPN](https://azure.microsoft.com/blog/expressroute-or-virtual-network-vpn-whats-right-for-me/)
- [Azure ExpressRoute pricing](https://azure.microsoft.com/pricing/details/expressroute/)
- [What is Azure ExpressRoute?](/en-us/azure/expressroute/expressroute-introduction)