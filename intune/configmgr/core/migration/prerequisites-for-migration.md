---
layout: Conceptual
title: Migration prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/prerequisites-for-migration
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
description: Understand the supported versions of Configuration Manager, supported source-site languages, and required configurations for migration.
ms.date: 2018-05-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: c303f63f-456f-973e-c0b2-dcb50ba89f90
document_version_independent_id: 5e2ccaa0-6db4-5343-cb21-a90e3e2d0300
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/migration/prerequisites-for-migration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/migration/prerequisites-for-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/migration/prerequisites-for-migration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: f2344384-807a-fd22-15af-127fdc359e1a
---

# Migration prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To migrate from a supported source hierarchy, you must have access to each applicable Configuration Manager source site, and permissions within the Configuration Manager destination site to configure and run migration operations.

Use the information in the following sections to help you understand the versions of Configuration Manager that are supported for migration, and the required configurations.

- Versions of Configuration Manager that are supported for migration
- Source site languages that are supported for migration
- Required configurations for migration

## Versions of Configuration Manager that are supported for migration

You can migrate data from a source hierarchy that runs any of the following versions of Configuration Manager:

- Configuration Manager 2007 SP2 (For the purpose of migration, Configuration Manager 2007 R2 or R3 on the source site are not a consideration. So long as the source site runs SP2, sites with either the R2 or R3 add-on installed are supported for migration to Configuration Manager current branch).
- System Center 2012 Configuration Manager SP2 or System Center 2012 R2 Configuration Manager SP1.

    Tip

    In addition to migration, you can use an in-place upgrade of sites that run System Center 2012 Configuration Manager to Configuration Manager current branch.
- A Configuration Manager hierarchy of the same or lesser version of Configuration Manager.

    For example, if you have a destination hierarchy that runs Configuration Manager current branch 1606, you could use migration to copy data from a source hierarchy that runs version 1606 or 1602. However you could not migrate data from a source hierarchy that runs 1610.

## Source site languages that are supported for migration

When you migrate data between Configuration Manager hierarchies, the data is stored in the destination hierarchy in the language neutral format for Configuration Manager. Because Configuration Manager 2007 does not store data in a language neutral format, the migration process must convert objects to this format during migration from Configuration Manager 2007. Therefore, only Configuration Manager 2007 source sites that are installed with the following languages are supported for migration:

- English
- French
- German
- Japanese
- Korean
- Russian
- Simplified Chinese
- Traditional Chinese

When you migrate data from a System Center 2012 Configuration Manager or Configuration Manager current branch hierarchy, there are no source site language limitations. Objects in the source site database are already in a language neutral format.

## Required configurations for migration

The following are required configurations for using migration and migration operations:

- **To configure, run, and monitor migration in the Configuration Manager console:**

    In the destination site, your account must be assigned the role-based administration security role of **Infrastructure Administrator**. This security role grants permissions to manage all migration operations, which includes the creation of migration jobs, clean up, monitoring, and the action to share and upgrade distribution points.
- **Data Gathering:**

    To enable the destination site to gather data, you must configure the following two source site access accounts for use with each source site:

    - **Source Site Account:** This account is used to access the SMS Provider of the source site.

        - For a Configuration Manager 2007 SP2 source site, this account requires **Read** permission to all source site objects.
        - For a System Center 2012 Configuration Manager or Configuration Manager current branch source site, this account requires **Read** permission to all source site objects, You grant this permission to the account by using role-based administration. For information about how to use role-based administration, see [Fundamentals of role-based administration for Configuration Manager](../understand/fundamentals-of-role-based-administration).
    - **Source Site Database Account:** This account is used to access the SQL Server database of the source site and requires **Connect**, **Execute**, and **Select** permissions to the source site database.

    You can configure these accounts when you configure a new source hierarchy, data gathering for an additional source site, or when you reconfigure the credentials for a source site. These accounts can use a domain user account, or you can specify the computer account of the top-level site of the destination hierarchy.

    Important

    If you use the Configuration Manager computer account for either access account, ensure that this account is a member of the security group **Distributed COM Users** in the domain where the source site resides.

    When gathering data, the following network protocols and ports are used:

    - NetBIOS/SMB - 445 (TCP)
    - RPC (WMI) - 135 (TCP & UDP)
    - Dynamic RPC. Dynamic ports use a range of port numbers that are defined by the OS version. These ports are also known as ephemeral ports. For more information about the default port ranges, see [Service overview and network port requirements for Windows](https://support.microsoft.com/help/832017/service-overview-and-network-port-requirements-for-windows).
    - SQL Server - The TCP ports in use by both the source and destination site databases.
- **Migrate Software Updates:**

    Before you migrate software updates, you must configure the destination hierarchy with a software update point. For more information, see [Planning to migrate software updates](planning-for-the-migration-of-objects#Plan_migrate_Software_updates).
- **Share distribution points:**

    To successfully share any distribution points from a source site, at least one primary site or the central administration site in the destination hierarchy must use the same port numbers for client requests as the source site. For information about client request ports, see [How to configure client communication ports](../clients/deploy/configure-client-communication-ports)

    For each source site, only the distribution points that are installed on site system servers that are configured with a FQDN are shared.

    In addition, to share a distribution point from a System Center 2012 Configuration Manager or Configuration Manager current branch source site, the **Source Site Account** (which accesses the SMS Provider for the source site server), must have **Modify** permissions to the **Site** object on the source site. You grant this permission to the account by using role-based administration. For information about how to use role-based administration, see [Fundamentals of role-based administration for Configuration Manager](../understand/fundamentals-of-role-based-administration).
- **Upgrade or reassign distribution points:**

    The **Source Site Access Account** configured to gather data from the SMS Provider of the source site must have the following permissions:

    - To upgrade a Configuration Manager 2007 distribution point, the account requires **Read**, **Execute**, and **Delete** permissions to the **Site** class on the Configuration Manager2007 site server to successfully remove the distribution point from the Configuration Manager2007 source site
    - To reassign a System Center 2012 Configuration Manager or Configuration Manager current branch distribution point, the account must have **Modify** permission to the **Site** object on the source site. You grant this permission to the account by using role-based administration. For information about how to use role-based administration, see [Fundamentals of role-based administration for Configuration Manager](../understand/fundamentals-of-role-based-administration).

        To successfully upgrade or reassign a distribution point to a new hierarchy, the ports that are configured for client requests at the site that manages the distribution point in the source hierarchy must match the ports that are configured for client requests at the destination site that will manage the distribution point. For information about client request ports, see [How to configure client communication ports](../clients/deploy/configure-client-communication-ports).