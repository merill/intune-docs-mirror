---
layout: Conceptual
title: Use cloud services - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/use-cloud-services
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
description: Provision cloud resources for Configuration Manager to supplement your on-premises infrastructure.
ms.date: 2021-07-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 97f045ff-807d-3cf5-18ef-7313e66f7f81
document_version_independent_id: 2ed4aa83-920a-ec00-4d10-d08c07a76383
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/use-cloud-services.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/use-cloud-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/use-cloud-services.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: e83feb4e-481f-d243-494f-baaf1e058fc2
---

# Use cloud services - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager supports several cloud-based options. These can supplement your on-premises infrastructure, and can help solve business problems like:

- How to manage clients that roam onto the internet.
- How to provide content resources to isolated clients or resources on the intranet, outside your firewall.
- How to scale out infrastructure when physical hardware isn't available, or isn't logically placed to support your needs.

Provisioning cloud resources isn't something you have to do before you deploy Configuration Manager. It can be beneficial to understand these options before progressing too far in a hierarchy design plan. The use of cloud resources might save you money and time, while solving business problems that on-premises infrastructure can't.

## Cloud-based resources

Each option has different requirements. Investigate each in greater depth to understand the unique prerequisites, limitations, and potential for additional costs based on use.

### Azure virtual machines for cloud-based infrastructure

Configuration Manager supports using computers that run in virtual machines in Azure. You can use Azure virtual machines in the following scenarios:

- Run Configuration Manager in a virtual machine and use it to manage clients installed in other cloud-based virtual machines.
- Run Configuration Manager in a virtual machine and use it to manage clients that aren't in Azure.
- Run different Configuration Manager site system roles in Azure virtual machines. Run other roles in your on-premises network. Configure appropriate network connectivity for communications.

The same requirements for networks, operating systems, and hardware requirements that apply to installing the Configuration Manager on your on-premises network also apply to the installation of Configuration Manager in Azure.

An Azure subscription is required to use Azure virtual machines. You incur charges based on the number of virtual machines you use, their configuration, and use of cloud-based resources.

Additionally, Configuration Manager sites and clients that run in Azure virtual machines are subject to the same license requirements as on-premises installations.

For more information, see [Configuration Manager on Azure FAQ](configuration-manager-on-azure).

### Azure services

You can connect the site to Azure for several scenarios:

- Microsoft Entra authentication and discovery. For more information, see [Configure Azure services](../servers/deploy/configure/azure-services-wizard).
- Cloud management gateway to manage internet-based clients. For more information, see [Cloud management gateway overview](../clients/manage/cmg/overview).
- Deploy apps from the Microsoft Store for Business and Education. For more information, see [Manage apps from the Microsoft Store for Business and Education](../../apps/deploy-use/manage-apps-from-the-windows-store-for-business).
- [Microsoft Intune tenant attach](../../tenant-attach/device-sync-actions)

These are different than using an Azure virtual machine, on which you deploy a site system role.

- Run as a service in Azure, not on a virtual machine.
- Automatically scale to meet increased content requests from clients.
- Support clients on the internet and the intranet.

An Azure subscription is required for these scenarios. You incur charges based on the amount of data that transfers to and from the service.

### Additional Configuration Manager capabilities

Some Configuration Manager capabilities can connect to cloud-based services, like:

- Windows Server Update Services (WSUS)
- Download updates for Configuration Manager

These additional capabilities don't require you to have an Azure subscription. You don't have to set up specific connections, certificates, or services in the cloud. Instead, they are automatically managed by Configuration Manager for you. All you need to do is ensure applicable site systems and devices can access the internet-based URLs.

## Security for cloud-based services

Configuration Manager uses certificates to provision and access your content in Azure, and to manage the services that you use. Configuration Manager encrypts the data that you store in Azure, but doesn't introduce additional security or data controls beyond those that Azure provides.

For more information, see the details for the different cloud-based resource scenarios. Also see an [Introduction to Azure security](/en-us/azure/security/fundamentals/overview).