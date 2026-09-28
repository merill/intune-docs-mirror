---
layout: Conceptual
title: Manage clients over the internet - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/manage-clients-internet
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
description: Learn about managing clients with cloud management gateway and internet-based client management in Configuration Manager.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: fa504ed3-3112-bfd3-888f-b8e600862c2f
document_version_independent_id: 5a41e213-7a81-ae8c-02dc-6d493585a76b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/manage-clients-internet.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/manage-clients-internet
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/manage-clients-internet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: cfa700b4-1d17-edc7-a1c0-401c78465895
---

# Manage clients over the internet - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Typically in Configuration Manager, most of the managed computers and servers are physically on the same internal network as the site system servers that perform management functions. However, you can manage clients outside your internal network when they are connected to the internet. This ability doesn't require the clients to connect via VPN to reach the site system servers.

Configuration Manager provides two ways to manage internet-connected clients:

- Cloud management gateway
- Internet-based client management

Note

You can have a combination of both services for a single site. If a device gets policy from the site for both IBCM and CMG, then it randomizes between them for communication. The only mechanism available to control communication is client authentication. For example, if a Microsoft Entra joined client doesn't trust the server authentication certificate of the internet-based management point, it can only use the CMG. If a domain-joined client doesn't trust the server authentication certificate of the CMG, it can only use the internet-based management point.

## Cloud management gateway

The cloud management gateway provides management of internet-based clients. It uses a combination of a Microsoft Azure cloud service, and an on-premises site system role that communicates with that service. Internet-based clients use the cloud service to communicate with the on-premises Configuration Manager.

### CMG advantages

- No additional on-premises infrastructure investment required.
- Does not expose on-premises infrastructure to the internet.
- Cloud virtual machines that run the service are fully managed by Azure and require no maintenance.
- Easily set up and configured in the Configuration Manager console.

### CMG disadvantages

- Cloud subscription cost.
- Management data sent through cloud service.

## Internet-based client management

This method relies on internet-facing site system servers to which clients directly communicate for management purposes. It requires clients and site system servers to be configured for internet-based client management (IBCM).

### IBCM advantages

- No cloud service dependency.
- No additional cost associated with a cloud subscription.
- Full control of servers and roles providing the service.

### IBCM disadvantages

- Require additional infrastructure investment.
- Overhead and operational cost of additional infrastructure.
- Infrastructure must be exposed to the internet.