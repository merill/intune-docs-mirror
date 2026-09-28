---
layout: Conceptual
title: Cloud management gateway overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview
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
description: Learn about managing internet-based clients with Configuration Manager by using the cloud management gateway (CMG) service in Azure.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 7cea480c-4b93-beb2-f455-da6dcb26e370
document_version_independent_id: f439c2f6-812a-1508-b1fb-fd99d93df2d8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: ef9fdcb8-0517-d613-66b2-62fbf1bbd18f
---

# Cloud management gateway overview - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The cloud management gateway (CMG) provides a simple way to manage Configuration Manager clients over the internet. You deploy CMG as a cloud service in Microsoft Azure. Then without more on-premises infrastructure, you can manage clients that roam on the internet or are in branch offices across the WAN. You also don't need to expose your on-premises infrastructure to the internet.

![Diagram of cloud management gateway (CMG) basic architecture.](media/cmg-basic-architecture.svg)

After establishing the prerequisites, creating the CMG consists of the following three steps in the Configuration Manager console:

1. Deploy the CMG cloud service to Azure.
2. Add the CMG connection point role.
3. Configure the site and site roles for the service.

Once deployed and configured, clients seamlessly access on-premises site roles whether they're on the intranet or internet.

This article provides the foundational knowledge to learn about the CMG and the scenarios where you can use it.

## Scenarios

There are several scenarios for which a CMG is beneficial. The following scenarios are some of the more common:

- Manage traditional Windows clients with Active Directory domain-joined identity. These clients include any supported version of Windows. It uses PKI certificates to secure the communication channel. Management activities include:

    - Software updates and endpoint protection
    - Inventory and client status
    - Compliance settings
    - Software distribution to the device
    - Windows in-place upgrade task sequence
- Manage traditional Windows 10 or later clients with modern identity, either hybrid or pure cloud domain-joined with Microsoft Entra ID. Clients use Microsoft Entra ID to authenticate rather than PKI certificates. Using Microsoft Entra ID is simpler to set up, configure and maintain than more complex PKI systems. Management activities are the same as the first scenario plus:

    - Software distribution to the user
- Install the Configuration Manager client on Windows 10 or later devices over the internet. Using Microsoft Entra ID allows the device to authenticate to the CMG for client registration and assignment. You can install the client manually, or using another software distribution method, such as Microsoft Intune.
- New device provisioning with co-management. When auto-enrolling existing clients, CMG isn't required for co-management. It's required for new devices involving Windows Autopilot, Microsoft Entra ID, Microsoft Intune, and Configuration Manager. For more information, see [Paths to co-management](../../../../comanage/quickstart-paths).

## Specific use cases

Across these scenarios, the following specific device use cases may apply:

- Roaming devices such as laptops
- Remote/branch office devices that are less expensive and more efficient to manage over the internet than across a WAN or through a VPN.
- Mergers and acquisitions, where it may be easiest to join devices to Microsoft Entra ID and manage through a CMG.
- Workgroup clients. These devices may require other configurations, such as certificates.

    To help with management of remote workgroup clients, use Configuration Manager token-based authentication. For more information, see [Token-based authentication for CMG](../../deploy/deploy-clients-cmg-token).

Important

By default all clients receive policy for a CMG, and start using it when they become internet-based. Depending upon the scenario and use case that applies to your organization, you may need to scope usage of the CMG. For more information, see the [Enable clients to use a cloud management gateway](../../deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway) client setting.