---
layout: Conceptual
title: Choose what to migrate - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/determine-whether-to-migrate-data
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
description: Learn which data you can migrate and which data you can't migrate to Configuration Manager current branch.
ms.date: 2016-12-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: 65aacb63-1db9-22e5-ed41-d24122aa3e15
document_version_independent_id: da3c6664-b42d-4fa8-2aae-c4b843dbae79
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/migration/determine-whether-to-migrate-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/migration/determine-whether-to-migrate-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/migration/determine-whether-to-migrate-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: f93715d4-7b11-9798-e396-d405d99c68c7
---

# Choose what to migrate - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In Configuration Manager current branch, migration provides a process for transferring data and configurations that you've created from supported versions of Configuration Manager to your new hierarchy. You can use this to:

- Combine multiple hierarchies into one.
- Move data and configurations from a lab deployment into your production deployment.
- Move data and configuration from a prior version of Configuration Manager, like Configuration Manager 2007, which has no upgrade path to Configuration Manager current branch, or from System Center 2012 Configuration Manager (which does support an upgrade path to Configuration Manager current branch).

With the exception of the distribution point site system role and the computers that host distribution points, no infrastructure (which includes sites, site system roles, or computers that host a site system role), migrates, transfers, or can be shared between hierarchies.

Although you cannot migrate server infrastructure, you can migrate Configuration Manager clients between hierarchies. Client migration involves migrating the data that clients use from the source hierarchy to the destination hierarchy, and then installing or reassigning the client software so that the client then reports to the new hierarchy.

After you install a client to the new hierarchy and the client submits its data, its unique Configuration Manager ID helps Configuration Manager associate the data that you previously migrated with each client computer.

The functionality that's provided by migration helps you maintain investments that you have made in configurations and deployments while letting you take full advantage of core changes in the product first (which was first introduced in System Center 2012 Configuration Manager and then continued in Configuration Manager). These changes include a simplified Configuration Manager hierarchy that uses fewer sites and resources, and the improved processing that comes from using native 64-bit code that runs on 64-bit hardware.

For information about the versions of Configuration Manager that migration supports, see [Prerequisites for migration](prerequisites-for-migration).

## Data that you can migrate to Configuration Manager current branch

Migration can migrate most objects between supported Configuration Manager hierarchies. The migrated instances of some objects from a supported version of Configuration Manager 2007 must be modified to conform to the System Center 2012 Configuration Manager schema and object format.

These modifications don't affect the data in the source site database. Objects that are migrated from a supported version of System Center 2012 Configuration Manager or Configuration Manager current branch don't require modification.

The following are objects that can migrate based on the version of Configuration Manager in the source hierarchy. Some objects, like queries, do not migrate. If you want to continue to use these objects that do not migrate you must recreate them in the new hierarchy. Other objects, including some client data, are automatically recreated in the new hierarchy when you manage clients in that hierarchy.

### Objects that you can migrate from System Center 2012 Configuration Manager or Configuration Manager current branch

- Applications for System Center 2012 Configuration Manager and later versions
- App-V Virtual Environment from System Center 2012 Configuration Manager and later versions
- Asset Intelligence customizations
- Boundaries
- Collections: To migrate collections from a supported version of System Center 2012 Configuration Manager or Configuration Manager current branch, you use an object migration job.
- Compliance settings:

    - Configuration baselines
    - Configuration items
- Deployments
- Operating system deployment:

    - Boot images
    - Driver packages
    - Drivers
    - Images
    - Packages
    - Task sequences
- Search results: Saved search criteria
- Software updates:

    - Deployments
    - Deployment packages
    - Templates
    - Software update lists
- Software distribution packages
- Software metering rules
- Virtual application packages

### Objects that you can migrate from Configuration Manager 2007 SP2

- Advertisements
- Applications for System Center 2012 Configuration Manager and later versions
- App-V Virtual Environment from System Center 2012 Configuration Manager and later versions
- Asset Intelligence customizations
- Boundaries
- Collections: You migrate collections from a supported version of Configuration Manager 2007 by using a collection migration job.
- Compliance settings (referred to as desired configuration management in Configuration Manager 2007):

    - Configuration baselines
    - Configuration items
- Operating system deployment:

    - Boot images
    - Driver packages
    - Drivers
    - Images
    - Packages
    - Task sequences
- Search results: Search folders
- Software updates:

    - Deployments
    - Deployment packages
    - Templates
    - Software update lists
- Software distribution packages
- Software metering rules
- Virtual application packages

## Data that you can't migrate to Configuration Manager current branch

You cannot migrate the following types of objects:

- AMT client provisioning information
- Files on clients, including:

    - Client inventory and history data
    - Files in the client cache
- Queries
- Configuration Manager 2007 security rights and instances for the site and objects
- Configuration Manager 2007 reports from SQL Server Reporting Services
- Configuration Manager 2007 web reports
- System Center 2012 Configuration Manager and Configuration Manager current branch reports
- System Center 2012 Configuration Manager and Configuration Manager current branch role-based administration:

    - Security roles
    - Security scopes