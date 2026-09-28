---
layout: Conceptual
title: Configure sites and hierarchies - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-sites-and-hierarchies
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
description: Consult this checklist to ensure you consider the most common configurations that affect both sites and hierarchies.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 2a60c0b1-23f6-485e-0588-08feaa11e07e
document_version_independent_id: 808fc2e9-bd01-b6ca-17c7-92dc43a6e18d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/configure-sites-and-hierarchies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/configure-sites-and-hierarchies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/configure-sites-and-hierarchies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b049ef96-9ec7-6433-e48e-930edb2bafdc
---

# Configure sites and hierarchies - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you install your first Configuration Manager site or add additional sites to your hierarchy, use this checklist to ensure that you consider the most common configurations that affect both sites and hierarchies.

The following configuration notes apply to most deployments:

- Some options build upon each other, such as Active Directory Forest Discovery, boundaries, and boundary groups.
- Several configurations have default values to use without configuration changes, at least to start.
- Other configurations, like boundary groups and distribution point groups, require you to configure them before using.

| Action | Details |
| --- | --- |
| Configure role-based administration | Segregate administrative assignments to control which administrative users can view and manage different objects and data in your Configuration Manager environment. Configurations for role-based administration are shared with all sites in a hierarchy. For more information, see [Configure role-based administration](configure-role-based-administration). |
| Publish site data to Active Directory Domain Services | Make it easy for clients to find services and efficiently use site resources. First [extend the Active Directory schema](../../../plan-design/network/extend-the-active-directory-schema). Then individually configure each site to [publish site data](publish-site-data) |
| Configure a service connection point | Plan to install and configure the service connection point at the top-level site of your hierarchy. For more information, see [About the service connection point](about-the-service-connection-point). |
| Add site system roles | Install one or more additional site system roles for individual sites. For more information, see [Add site system roles](add-site-system-roles). |
| Configure site boundaries and boundary groups | Specify boundaries that define network locations on your intranet that can contain devices that you want to manage. Then configure boundary groups so that clients at those network locations can find Configuration Manager resources. For more information, see [Define site boundaries and boundary groups](define-site-boundaries-and-boundary-groups). |
| Configure distribution point groups | Configure logical groups of distribution points to make managing deployments easier. For more information, see [Manage distribution point groups](install-and-configure-distribution-points#bkmk_manage). |
| Run discovery | Run discovery to find resources on your network, including network infrastructure, devices, and users. For more information, see [Run discovery](run-discovery). |
| Add redundancy and capacity for administrators | Install additional SMS Providers and Configuration Manager consoles to expand capacity for administrators to manage your infrastructure:**Install additional SMS providers** to provide redundancy for console and API connections to the site. For more information, see [Manage the SMS Provider](../../manage/modify-your-infrastructure#BKMK_ManageSMSprovider).**Install additional Configuration Manager consoles** to provide access to additional administrative users. For more information, see [Install Configuration Manager consoles](../install/install-consoles). |
| Configure site components | Configure site components at each site to modify the behavior of site system roles and site status reporting. For more information, see [Site components](site-components). |
| Create custom collections | Using information that the site discovers about devices and users, create custom collections of objects to simplify future management tasks. For more information, see [How to create collections](../../../clients/manage/collections/create-collections). |
| Configure settings to manage high-risk deployments | Configure settings at a site to warn administrators when they create a high-risk deployment. For more information, see [Settings to manage high-risk deployments](../../manage/settings-to-manage-high-risk-deployments). |
| Configure database replicas for management points | Configure a database replica to reduce the processor load that's placed on the site database server by management points as they service requests from clients. For more information, see [Database replicas for management points](database-replicas-for-management-points). |
| Configure a SQL Server Always On availability group | Configure availability groups as high-availability and disaster-recovery solutions for hosting the site database at primary sites and the central administration site. For more information, see [Prepare to use a SQL Server Always On availability group with Configuration Manager](sql-server-alwayson-for-a-highly-available-site-database). |
| Modify replication between sites | See [Data transfers between sites](../../../plan-design/hierarchy/data-transfers-between-sites) to learn about the following subjects: Configure [file-based replication](../../../plan-design/hierarchy/file-based-replication) between secondary sites Configure [database replication links](../../../plan-design/hierarchy/database-replication) Configure [distributed views](../../../plan-design/hierarchy/database-replication#distributed-views) |
| Configure site servers in passive mode | Starting in version 1806, configure a site server in passive mode for each primary site and the central administration site. This feature provides a highly available site server. For more information, see [Site server high availability](site-server-high-availability). |