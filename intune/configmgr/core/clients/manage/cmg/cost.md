---
layout: Conceptual
title: Cost of CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/cost
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
description: Understand the costs of operating the cloud management gateway (CMG) service in Microsoft Azure.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 3917efa9-0cba-0c73-8339-27848967c58f
document_version_independent_id: ea0b61a7-cf1c-8543-c31c-49bf35063238
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/cost.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/cost
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/cost.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: b2300eca-e1da-6725-5a57-3967541dd11a
---

# Cost of CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The cloud management gateway (CMG) in Configuration Manager uses several components in Microsoft Azure. These components incur charges to the Azure subscription account. Some costs are fixed, but some vary depending upon usage.

Important

The following cost information is for estimating purposes only. Your environment may have other variables that affect the overall cost of using CMG.

To help determine potential costs, use the following Azure resources:

- [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)

    Note

    Virtual machine costs vary by region.
- [Azure bandwidth pricing details](https://azure.microsoft.com/pricing/details/bandwidth/)

    Note

    Pricing for data transfer is tiered. The more you use, the less you pay per gigabyte.

## Compute costs

CMG uses Azure platform as a service (PaaS), which uses virtual machines (VMs). These VMs incur compute costs. The specific type to use when estimating costs depends upon which deployment method you use.

Note

Although CMG is built on Azure PaaS, CMG is a software as a serice (SaaS) solution provided and maintained by Microsoft. CMG resources are added to customer Azure subscriptions so that consumption costs can be directly monitored and accounted for by the customer.

### Virtual machine scale set

When you deploy the CMG as a [virtual machine scale set](plan-cloud-management-gateway#virtual-machine-scale-sets), the following factors affect the cost of the service:

- In version 2107 and later, you can configure the VM size:

    - Lab ([B2s](/en-us/azure/virtual-machines/sizes-b-series-burstable))
    - Standard ([A2_v2](/en-us/azure/virtual-machines/av2-series))
    - Large ([A4_v2](/en-us/azure/virtual-machines/av2-series))

    Important

    The **Lab (B2s)** size VM is only intended for lab testing and small proof-of-concept environments. It isn't intended for production use with the CMG. The B2s VMs are low cost and low performing.

    You can change the VM size after you deploy the CMG. This action updates the Azure service to use a new VM.
- In version 2103 and earlier, the CMG uses a Standard [A2_v2](/en-us/azure/virtual-machines/av2-series) VM. The VM size isn't configurable. To change the VM size, you need to [Redeploy the service](modify-cloud-management-gateway#redeploy-the-service).
- You select how many VM instances support the CMG. One is the default, and 16 is the maximum. This number is set when you create the CMG, but you can change it afterwards to scale the service as needed.
- For more information on how many VMs you need to support your clients, see [CMG performance and scale](perf-scale).

### Virtual machine

Important

Starting in version 2203, the option to deploy a CMG as a **cloud service (classic)** is removed. All CMG deployments should use a [virtual machine scale set](plan-cloud-management-gateway#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

If you deployed the CMG as a classic cloud service, when estimating cost, this deployment method replaces the virtual machine scale set. The specific details are otherwise the same. With this deployment method, it uses a Standard A2\_v2 VM. The VM size isn't configurable. The cost difference between a virtual machine and a virtual machine scale set should be negligible, but may vary by Azure region.

## Outbound data transfer

- Charges are based on data flowing out of Azure, otherwise referred to as egress or download.
- CMG data flows out of Azure include policy to the client, client notifications, and client responses that the CMG forwards to the site. These responses include inventory reports, status messages, and compliance status.
- Even without any clients communicating with a CMG, some background communication causes network traffic between the CMG and the on-premises site.
- View the **Outbound data transfer (GB)** in the Configuration Manager console. For more information, see [Monitor clients on CMG](monitor-clients-cloud-management-gateway).
- *For estimating purposes only*, expect approximately 100-300 MB per client per month for internet-based clients. The lower estimate is for a default client configuration. The upper estimate is for a more aggressive client configuration. Your actual usage may vary depending upon how you configure client settings.

    Note

    Other administrative actions can increase the amount of outbound data transfer from Azure. For example, deployments for software updates or applications.
- Internet-based clients get Microsoft software update content from Windows Update at no charge. Don't distribute update packages with Microsoft update content to a content-enabled CMG. If you do distribute software update packages to your cloud content sources, you may incur storage and data egress costs.
- Misconfiguration of the CMG option to **Verify client certificate revocation** can cause more traffic from clients to the CMG. This other traffic can increase the Azure egress data, which can increase your Azure costs. For more information, see [Publish the certificate revocation list](security-and-privacy-for-cloud-management-gateway#publish-the-certificate-revocation-list).

Tip

Any data flows into Azure are free. These flows are otherwise referred to as ingress or upload. When you distribute content from the site to the content-enabled CMG, you're uploading the content to Azure.

## Content storage

- Internet-based clients get Microsoft software update content from Windows Update at no charge. Don't distribute update packages with Microsoft update content to a content-enabled CMG. If you do distribute software update packages to your cloud content sources, you may incur storage and data egress costs.

Note

The cloud-based distribution point (CDP) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable the CMG to distribute content.

- CMG uses Azure locally redundant storage (LRS). For more information, see [Locally redundant storage](/en-us/azure/storage/common/storage-redundancy-lrs).
- For any other necessary content, distribute it to a content-enabled CMG. This other content includes applications or third-party software updates.

    Note

    If you enable the client setting to [Download delta content when available](../../deploy/about-client-settings#allow-clients-to-download-delta-content-when-available), the content for third-party updates won't download to clients.

## Other costs

Each distinct CMG has one **Basic (ARM)** dynamic IP address. If you add other VMs to a CMG, it doesn't increase the number of these IP addresses. For more information, see [IP addresses pricing](https://azure.microsoft.com/pricing/details/ip-addresses/).

If you deploy the CMG as a virtual machine scale set, it uses **Azure Key Vault**. The CMG usage of Key Vault is low, significantly less than 10,000 operations per month. For more information, see [Key Vault pricing](https://azure.microsoft.com/pricing/details/key-vault/).

If you get a CMG server authentication certificate from a public provider, there's generally a cost associated with this certificate. For more information, see [CMG server authentication certificate](server-auth-cert).

## Control and monitor

Configuration Manager includes the following options to help control costs and monitor data access:

- Control and monitor the amount of content that you store in a cloud service.
- Configure Configuration Manager to alert you when thresholds for client downloads meet or exceed monthly limits.

For more information, see [Monitor CMG](monitor-clients-cloud-management-gateway).

To help reduce the number of data transfers from cloud-based sources by clients, use one of the following peer caching technologies:

- Configuration Manager peer cache
- Windows Delivery Optimization
- Windows BranchCache

    Note

    To enable a content-enabled CMG to use Windows BranchCache, install the BranchCache feature on the site server. For more information, see [Set up CMG: BranchCache](setup-cloud-management-gateway#branchcache)

For more information, see [Fundamental concepts for content management](../../../plan-design/hierarchy/fundamental-concepts-for-content-management).