---
layout: Conceptual
title: Network infrastructure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/configure-firewalls-ports-domains
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
description: Set up firewalls, ports, and domains to prepare for Configuration Manager communications.
ms.date: 2019-06-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 3790964d-94f2-a2d8-3e92-20cf278797e4
document_version_independent_id: f239c194-7ee5-a411-d788-2aca46d59fa4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/configure-firewalls-ports-domains.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/configure-firewalls-ports-domains
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/configure-firewalls-ports-domains.md
cmProducts: []
platformId: fa0bfc38-a6cf-8a59-6ac6-bf6c57fa2122
---

# Network infrastructure - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To prepare your network to support Configuration Manager, you may need to configure some infrastructure components. For example, open firewall ports to pass the communications used by Configuration Manager.

## Ports and protocols

Different Configuration Manager features use different network ports. Some ports are required, and some you can customize.

Most Configuration Manager communications use common ports like port 80 for HTTP or 443 for HTTPS. Some site system roles support the use of custom websites and custom ports. For more information, see [Websites for site system servers](websites-for-site-system-servers).

Before you deploy Configuration Manager, identify the ports that you plan to use, and set up firewalls as needed.

After you install Configuration Manager, if you need to change a port, don't forget to update firewalls on devices and the network. Also change the configuration of the port in Configuration Manager.

For more information, see the following articles:

- [How to configure client communication ports](../../clients/deploy/configure-client-communication-ports)
- [Ports used in Configuration Manager](../hierarchy/ports)

## Internet access requirements

Some Configuration Manager features rely on internet connectivity for full functionality. If your organization restricts network communication with the internet using a firewall or proxy device, make sure to allow the necessary endpoints.

For more information, see [Internet access requirements](internet-endpoints)

## Proxy servers

You can specify separate proxy servers for different site system servers and clients. You make these configurations when you install a site system role or client, or change them later as needed.

For more information, see [Proxy server support](proxy-server-support).