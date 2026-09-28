---
layout: Conceptual
title: Prerequisites for sites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/prerequisites-for-installing-sites
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
description: Learn about prerequisites for installing the different types of Configuration Manager sites.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: cd6a33be-723c-b8e3-4bce-2d77840057d5
document_version_independent_id: 42d3dbab-cf6e-467c-215a-d97e8e7b3eb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/prerequisites-for-installing-sites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/prerequisites-for-installing-sites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/prerequisites-for-installing-sites.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 7a8cbad9-c617-69fd-75db-16493adb43b8
---

# Prerequisites for sites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you begin a site installation, learn about the prerequisites for installing the different types of Configuration Manager sites.

## Primary sites and the central administration site

The following prerequisites apply to installing one of the following types:

- A central administration site (CAS) as the first site of a hierarchy
- A stand-alone primary site
- A child primary site

If you're installing a CAS as part of a hierarchy expansion, see the section for Expanding a stand-alone primary site.

### Prerequisites for installing a primary site or a CAS

- The necessary Windows Server roles, features, and Windows components must be installed. For more information, see [Site system prerequisites](../../../plan-design/configs/site-and-site-system-prerequisites#central-administration-site-and-primary-site-servers)
- The user account that installs the site must have the following permissions:

    - **Administrator** on the following servers:

        - The site server
        - Each SQL Server that hosts the **site database**
        - Each instance of the **SMS Provider** for the site
    - **Sysadmin** on the instance of SQL Server that hosts the site database

        Important

        When Configuration Manager setup finishes, the site server computer account still needs **sysadmin** permissions to SQL Server. Don't remove the SQL Server sysadmin permissions from this account.

        For more information on the need for these permissions after setup is complete, see [Accounts: Elevated permissions](../../../plan-design/hierarchy/accounts#elevated-permissions).
- If you're installing a primary site, you may also need **Administrator** permissions on additional servers. For example, where you install the initial management point and distribution point, if not on the site server.
- If you're installing a new child primary site below a CAS, you need the following additional permissions:

    - **Administrator** on the site server that hosts the CAS
    - **Administrator** on the SQL Server that hosts the CAS site database
    - Role-based administration permissions within Configuration Manager that are equivalent to the security role of **Infrastructure Administrator** or **Full Administrator**
- Use the correct installation source files, and run setup from that location. For information about the correct source files to use to install different types of sites, see [Prepare to install site: Options for installing different types of sites](prepare-to-install-sites#bkmk_options).
- The site server needs access to the latest setup files from Microsoft. Use one of the following methods:

    - Before you start the install, download and store a copy of these files on your local network. For more information, see [Setup Downloader](setup-downloader).
    - If a local copy of these files isn't available, the site server needs access to the internet. It downloads these files from Microsoft during the installation. For more information, see [Internet access requirements](../../../plan-design/network/internet-endpoints).
- The site server and site database server must meet all prerequisite configurations. Before starting Configuration Manager setup, [manually run Prerequisite Checker](prerequisite-checker) to identify and fix problems.

### Prerequisites to expand a stand-alone primary site

A stand-alone primary site must meet the following prerequisites before you can expand it into a hierarchy with a CAS:

#### Source file version matches site version

Install the new CAS using media from a CD.Latest folder that matches the version of the stand-alone primary site. To make sure the versions match, use the source files found in the [CD.Latest folder](../../manage/the-cd.latest-folder) on the stand-alone primary site.

For more information about the correct source files to use to install different sites, see [Prepare to install sites: Options for installing different types of sites](prepare-to-install-sites#bkmk_options).

#### Stop active migration from another hierarchy

You can't configure the stand-alone primary site to migrate data from another Configuration Manager hierarchy. Stop active migration to the stand-alone primary site from other Configuration Manager hierarchies and remove all configurations for migration. These configurations include:

- Migration jobs that haven't completed
- Data gathering
- The configuration of the active source hierarchy

This configuration is necessary because Configuration Manager migrates data from the top-level site of the hierarchy. When you expand a stand-alone primary site, the configurations for migration don't transfer to the CAS.

After you expand the stand-alone primary site, if you reconfigure migration at the primary site, the CAS runs the migration jobs.

For more information about how to configure migration, see [Configure source hierarchies and source sites for migration](../../../migration/configuring-source-hierarchies-and-source-sites-for-migration).

#### Computer account as Administrator

Add the computer account of the server that hosts the new CAS to the **Administrators** group on the stand-alone primary site server.

To successfully expand the stand-alone primary site, the computer account of the new CAS needs **Administrator** permissions on the stand-alone primary site. This account requires these permissions only during site expansion. When site expansion finishes, you can remove the account from the user group on the primary site.

#### Installation account permissions

The user account that runs Configuration Manager setup to install the new CAS needs role-based administration permissions at the stand-alone primary site.

For the user account that installs a CAS as part of a site expansion, add them to the proper role at the stand-alone primary site. Use the built-in **Full Administrator** or **Infrastructure Administrator** roles.

For more information including the complete list of required permissions, see [Site installation account](../../../plan-design/hierarchy/accounts#site-installation-account).

#### Top-level site roles

Before you expand the site, uninstall the following site system roles from the stand-alone primary site:

- Asset Intelligence sync point
- Endpoint protection point
- Service connection point

Configuration Manager only supports these roles at the top-level site of the hierarchy. Uninstall these site system roles before you expand the stand-alone primary site. After you expand the site, reinstall these site system roles at the CAS.

All other site system roles can remain installed at the primary site.

Configuration Manager setup also includes a [prerequisite check](list-of-prerequisite-checks#cloud-management-gateway-on-the-expanded-primary-site) that the standalone primary site doesn't include the [cloud management gateway](../../../clients/manage/cmg/overview) (CMG) service. Before you expand the site to a hierarchy, remove the CMG. Then redeploy it from the new CAS.

#### Open the SQL Server Service Broker port

The network port must be open for the SQL Server Service Broker (SSB) between the stand-alone primary site and the server for the CAS.

To successfully replicate data between a CAS and a primary site, Configuration Manager requires an open port between the two sites for SSB to use. When you install a CAS and expand a stand-alone primary site, the prerequisite check doesn't verify that the port you specify for the SSB is open on the primary site.

#### Known issues with Azure services

After you expand the site, you need to reconfigure the following Azure services with Configuration Manager:

- [Log Analytics](/en-us/azure/azure-monitor/platform/collect-sccm?context=/mem/configmgr/core/context/core-context)
- [Microsoft Store for Business](../../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business)
- [Tenant attach](../../../../tenant-attach/device-sync-actions)

The easiest method is to renew the Microsoft Entra tenant secret key. For more information, see [Renew secret key](../configure/azure-services-wizard#bkmk_renew).

Instead of renewing the secret key, remove and then recreate the connection to that service.

## Secondary sites

The following prerequisites are for installing secondary sites:

- The necessary Windows Server roles, features, and Windows components must be installed. For more information, see [Site system prerequisites](../../../plan-design/configs/site-and-site-system-prerequisites#secondary-site-server).
- The administrator who configures the installation of the secondary site in the Configuration Manager console needs role-based administration permissions that are equivalent to the security role of **Infrastructure Administrator** or **Full Administrator**.
- Add the computer account of the parent primary site to the **Administrators** group on the secondary site server.
- When the secondary site uses a previously installed instance of SQL Server to host the secondary site database:

    - The computer account of the parent primary site needs **sysadmin** permissions on the instance of SQL Server on the secondary site server.
    - The **Local System** account of the secondary site server computer needs **sysadmin** permissions on the instance of SQL Server on the secondary site server.

        Important

        When Configuration Manager setup finishes, both accounts still need **sysadmin** permissions to SQL Server. Don't remove the sysadmin permissions from these accounts.
- The secondary site server must meet all prerequisite configurations. These configurations include SQL Server and the default site system roles of the management point and distribution point.