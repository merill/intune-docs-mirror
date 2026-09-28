---
layout: Conceptual
title: Discover device and user resources - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/run-discovery
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
description: Read an overview of the discovery process and discovery data records.
ms.date: 2017-02-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f3fc7fd4-b3de-1574-1546-e9722aa96bcb
document_version_independent_id: e982e9ac-94bd-852e-2013-eaadc9dbfbbc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/run-discovery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/run-discovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/run-discovery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: fff84128-8b8f-f1bd-ba5b-8bf9e53c510f
---

# Discover device and user resources - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You use one or more discovery methods in Configuration Manager to find device and user resources that you can manage. You can also use discovery to identify network infrastructure in your environment. There are several different methods you can use to discover different things, and each method has its own configurations and limitations.

## Overview of discovery

Discovery is the process by which Configuration Manager learns about the things you can manage. The following are the available discovery methods:

- Active Directory Forest Discovery
- Active Directory Group Discovery
- Active Directory System Discovery
- Active Directory User Discovery
- Microsoft Entra user Discovery
- Microsoft Entra user Group Discovery
- Heartbeat Discovery
- Network Discovery
- Server Discovery

Tip

You can learn about the individual discovery methods in [About discovery methods for Configuration Manager](about-discovery-methods).

For assistance in selecting which methods to use, and at which sites in your hierarchy, see [Select discovery methods to use for Configuration Manager](select-discovery-methods-to-use).

To use most discovery methods, you must enable the method at a site, and set it up to search specific network or Active Directory locations. When it runs, it queries the specified location for information about devices or users that Configuration Manager can manage. When a discovery method successfully finds information about a resource, it puts that information into a file called a discovery data record (DDR). That file is then processed by a primary or central administration site. Processing of a DDR creates a new record in the site database for newly discovered resources, or updates existing records with new information.

Some discovery methods can generate a large volume of network traffic, and the DDRs they produce can result in a significant use of CPU resources during processing. Therefore, plan to use only those discovery methods that you require to meet your goals. You might start by using only one or two discovery methods, and then later enable additional methods in a controlled manner to extend the level of discovery in your environment.

After discovery information is added to the site database, the information then replicates to each site in the hierarchy, regardless of where it was discovered or processed. Therefore, while you can set up different schedules and settings for discovery methods at different sites, you might run a specific discovery method at only a single site. This reduces the use of network bandwidth through duplicate discovery actions, and reduces the processing of redundant discovery data at multiple sites.

You can use discovery data to create custom collections and queries that logically group resources for management tasks. For example:

- Pushing client installations, or upgrading.
- Deploying content to users or devices.
- Deploying client settings and related configurations.

## About discovery data records

DDRs are files created by a discovery method. They contain information about a resource you can manage in Configuration Manager, such as computers, users, and in some cases, network infrastructure. They are processed at primary sites or at central administration sites. After the resource information in the DDR is entered into the database, the DDR is deleted, and the information replicates as global data to all sites in the hierarchy.

The site at which a DDR is processed depends on the information it contains:

- DDRs for newly discovered resources that are not in the database are processed at the top-level site of the hierarchy. The top-level site creates a new resource record in the database, and assigns it a unique identifier. DDRs transfer by file-based replication until they reach the top-level site.
- DDRs for previously discovered objects are processed at primary sites. Child primary sites do not transfer DDRs to the central administration site when the DDR contains information about a resource that is already in the database.
- Secondary sites do not process DDRs, and always transfer them by file-based replication to their parent primary site.

DDR files are identified by the .ddr extension, and have a typical size of about 1 KB.

## Get started with discovery:

Before using the Configuration Manager console to set up discovery, you should understand the differences among the methods, what they can do, and for some, their limitations.

The following topics can build a foundation that will help you use discovery methods successfully:

- [About discovery methods for Configuration Manager](about-discovery-methods)
- [Select discovery methods to use for Configuration Manager](select-discovery-methods-to-use)

Then, when you understand the methods you want to use, find guidance to set up each method in [Configure discovery methods for Configuration Manager](configure-discovery-methods).