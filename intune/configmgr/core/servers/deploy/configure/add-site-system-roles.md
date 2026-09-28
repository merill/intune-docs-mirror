---
layout: Conceptual
title: Add site system roles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/add-site-system-roles
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
description: Understand Configuration Manager site system roles and how to add them to extend the functionality and capacity of your site.
ms.date: 2021-07-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: c98e2394-edaa-4e05-c975-f5043c941b31
document_version_independent_id: 7759cab0-dfc0-f9bb-50e6-f502efbcc387
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/add-site-system-roles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/add-site-system-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/add-site-system-roles.md
cmProducts: []
platformId: aa35c807-1e16-4274-17f4-36e3d1393450
---

# Add site system roles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Each Configuration Manager site supports multiple site system roles. Each role extends the functionality and capacity of your site to provide services to the site and to manage devices and users. Each site system role on a site system server must be from the same site.

Configuration Manager doesn't support site system roles for multiple sites on a single site system server.

Tip

If you're not familiar with the basics for site system roles or the difference between the site server, site system servers, and site system roles, see [Fundamentals of Configuration Manager](../../../understand/fundamentals).

The following articles detail procedures and related details for installing site system roles:

- [Install site system roles](install-site-system-roles): Basic guidance about how to use the two in-console wizards to install new site system roles.
- [Set up checklist for CMG](../../../clients/manage/cmg/set-up-checklist): Set up a cloud management gateway (CMG) to manage clients on the internet.
- [Install site system roles for on-premises mobile device management (MDM)](/en-us/previous-versions/troubleshoot/configmgr/install-site-system-roles-for-on-premises-mdm): Set up your site system roles to support managing modern devices by using Configuration Manager on-premises MDM.
- [Configuration options for site system roles](configuration-options-for-site-system-roles): Some site system roles support configurations that require more details than the user interface can explain.
- [Remove a site system role](../install/uninstall-sites-and-hierarchies#bkmk_role): Guidance and procedures to remove roles from site system servers.