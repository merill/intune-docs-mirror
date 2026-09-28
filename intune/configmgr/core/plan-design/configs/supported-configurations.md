---
layout: Conceptual
title: Supported configurations - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations
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
description: Identify key configurations and requirements so you can plan, deploy, and maintain a functional Configuration Manager deployment.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 60550039-fe2c-3d12-8981-6f9ddcf0970e
document_version_independent_id: 87850034-0d44-85e5-9990-66af3ffd0ffd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/supported-configurations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/supported-configurations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/supported-configurations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 1cde6944-8e67-6851-2cc7-9fc61526455d
---

# Supported configurations - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

As an on-premises solution, Configuration Manager makes use of your servers, clients, network configurations, and other products like Microsoft Intune, SQL Server, and Azure.

This information can help you identify key configurations, requirements, and limitations. Use it to plan, deploy, and maintain a functional Configuration Manager deployment. This information is specific to the infrastructure for Configuration Manager sites, hierarchies, and managed devices.

When a Configuration Manager feature or capability requires more specific configurations, see the feature-specific documentation. It's supplemental to the more general configuration details.

The products and technologies described in these articles are supported by Configuration Manager. However, their inclusion in this content doesn't imply an extension of support for any product beyond that product's individual support lifecycle. Products that are beyond their support lifecycle aren't supported for use with Configuration Manager. This statement includes any products that are covered under the [Extended Security Updates (ESU)](/en-us/lifecycle/faq/extended-security-updates) program. For more information about Extended Security Updates in Configuration Manager, see [Supported OS versions for clients and devices for Configuration Manager](supported-operating-systems-for-clients-and-devices#bkmk_ESU).

Note

For more general information, see the [Microsoft Support Lifecycle](/en-us/lifecycle).

Products and product versions that aren't listed in these articles aren't supported with Configuration Manager unless they're announced on the [Configuration Manager blog](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/bg-p/ConfigurationManagerBlog). The content on this blog may precede an update to this documentation.

- [Site and site system prerequisites](site-and-site-system-prerequisites): Learn about required configurations on a Windows Server to support different site types and site system roles.
- [Supported operating systems for site system servers](supported-operating-systems-for-site-system-servers): Learn about which operating systems you can use as a site server or site system server.
- [Supported operating systems for clients and devices](supported-operating-systems-for-clients-and-devices): Learn about which operating systems you can manage with Configuration Manager. These include Windows, Windows Embedded, macOS, and mobile devices.
- [Support for Windows 11](support-for-windows-11) and [Support for Windows 10](support-for-windows-10): Learn about the Windows 11 and Windows 10 versions that are supported as clients.
- [Support for the Windows ADK](support-for-windows-adk): Learn about the Windows Assessment and Deployment Kit (Windows ADK) version that are supported with Configuration Manager current branch for OS deployment.
- [Supported operating systems for the console](supported-operating-systems-consoles): Learn about which operating systems can host the Configuration Manager console.
- [Supported SQL Server versions](support-for-sql-server-versions): Learn which versions, editions, and compatibility levels of SQL Server can host the site database and reporting database.
- [Supported configurations for SQL Server](supported-configurations-for-sql-server): Learn about required and optional SQL Server and database configurations.
- [High-availability options](../../servers/deploy/configure/high-availability-options): Learn about the options you can implement when designing your environment to help maintain a high level of available service for Configuration Manager.
- [Support for Active Directory domains](support-for-active-directory-domains): Learn about the supported Active Directory domain configurations that Configuration Manager requires and supports.
- [Support for Windows features and networks](support-for-windows-features-and-networks): Learn about supported Windows technologies and limitations for use with Configuration Manager. For example, Windows BranchCache and data deduplication.
- [Support for virtualization environments](support-for-virtualization-environments): Learn more about how to use supported virtual machine technologies.
- [FAQ for Configuration Manager on Azure](../../understand/configuration-manager-on-azure): Answers to common questions about using Configuration Manager on an Azure environment.

Use the following articles to understand Configuration Manager size, scale, and performance:

- [Size and scale numbers](size-and-scale-numbers): Learn about how many sites, roles per site, and clients are supported in different hierarchy designs.
- [Recommended hardware](recommended-hardware): Learn about guidelines that can help you identify the right hardware and configurations to host your Configuration Manager sites and key services.
- [Site size and performance guidelines](site-size-performance-guidelines): Site size-related performance test results, methodology, and guidance.
- [Site size and performance FAQ](../../understand/site-size-performance-faq): Answers to common Configuration Manager questions about site sizing and performance.