---
layout: Conceptual
title: Migration source hierarchies - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/configuring-source-hierarchies-and-source-sites-for-migration
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
description: Configure a source hierarchy and source sites so you can migrate data to your Configuration Manager current branch environment.
ms.date: 2016-12-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: e7834922-fea6-b372-d3ba-ca2b9da49583
document_version_independent_id: d21fd405-e83b-84d7-26ba-04c233965cd5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/migration/configuring-source-hierarchies-and-source-sites-for-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: e408ee73-df0c-e531-266c-83993c99fc89
---

# Migration source hierarchies - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To enable migration of data to your Configuration Manager current branch environment, you must configure a supported Configuration Manager source hierarchy and one or more source sites in that hierarchy that contain data that you want to migrate.

Note

Operations for migration are run at the top-level site in the destination hierarchy. If you configure migration when you use a Configuration Manager console that is connected to a primary child site, you must allow time for the configuration to replicate to the central administration site, start, and then replicate status back to the primary site to which you are connected.

Use the information and procedures in the following sections to specify the source hierarchy and add additional source sites. After you finish these procedures, you can create migration jobs and start to migrate data from the source hierarchy to the destination hierarchy.

- Specify a source hierarchy for migration
- Identify additional source sites of the source hierarchy

## Specify a source hierarchy for migration

To migrate data to your destination hierarchy, you must specify a supported source hierarchy that has the data that you want to migrate. By default, the top-level site of that hierarchy becomes a source site of the source hierarchy. If you migrate from a Configuration Manager 2007 hierarchy, you can then set up additional source sites for migration after data is gathered from the initial source site. If you migrate from a System Center 2012 Configuration Manager or Configuration Manager current branch hierarchy, you do not have to set up additional source sites to migrate data from the source hierarchy. This is because these versions of Configuration Manager use a shared database that is available at the top-level site of the source hierarchy. The shared database has all the information that you can migrate.

Use the following procedures to specify a source hierarchy for migration and to identify additional source sites in a Configuration Manager 2007 hierarchy.

Run this procedure with a Configuration Manager console that is connected to the destination hierarchy:

### To configure a source hierarchy

1. In the Configuration Manager console, click **Administration**.
2. In the **Administration** workspace, expand **Migration**, and then click **Source Hierarchy**.
3. On the **Home** tab, in the **Migration** group, click **Specify Source Hierarchy**.
4. In the **Specify Source Hierarchy** dialog box, for **Source Hierarchy**, select **New source hierarchy**.
5. For **Top-level Configuration Manager site server**, enter the name or IP address of the top-level site of a supported source hierarchy.
6. Specify source site access accounts that have the following permissions:

    - Source Site Account: **Read** permission to the SMS Provider for the specified top-level site in the source hierarchy. Distribution point sharing and upgrades require **Modify** and **Delete** permissions to the site in the source hierarchy.
    - Source Site Database Account: **Read** and **Execute** permission to the SQL Server database for the specified top-level site in the source hierarchy.

        If you specify the use of the computer account, Configuration Manager uses the computer account of the top-level site of the destination hierarchy. For this option, ensure that this account is a member of the security group **Distributed COM Users** in the domain where the top-level site of the source hierarchy resides.
7. To share distribution points between the source and destination hierarchies, select the **Enable distribution point sharing for the source site server** check box. If you do not enable distribution point sharing at this time, you can do so by editing the credentials of the source site after data gathering has finished.
8. Click **OK** to save the configuration. This opens the **Data Gathering Status** dialog box, and data gathering starts automatically.
9. When data gathering finishes, click **Close** to close the **Data Gathering Status** dialog box and complete the configuration.

## Identify additional source sites of the source hierarchy

When you configure a supported source hierarchy, the top-level site of that hierarchy is automatically configured as a source site, and data is automatically gathered from that site. The next action that you take depends on the version of Configuration Manager that is run by the source hierarchy:

- For a Configuration Manager 2007 source hierarchy, you can begin migration from that initial source site or set up additional source sites from the source hierarchy after the data gathering finishes for the initial source site. To migrate data that is only available from a child site, set up additional source sites for a Configuration Manager 2007 hierarchy. For example, you might configure additional source sites to gather data about content that you want to migrate when it's created at a child site in the source hierarchy and is not available at the top site of the source hierarchy.
- For a System Center 2012 Configuration Manager or Configuration Manager current branch source hierarchy, you do not need to configure additional source sites. This is because these versions of Configuration Manager use a shared database that is available at the top-level site of the source hierarchy. The shared database has all the information that you can migrate from all of the sites in that source hierarchy. This makes the data that you can migrate available from the top-level site of the source hierarchy.

When you configure additional source sites for a Configuration Manager 2007 source hierarchy, you must configure the additional source sites from the top of the source hierarchy to the bottom. You must configure a parent site as a source site before you configure any of its child sites as source sites.

Use the following procedure to configure additional source sites for Configuration Manager 2007 source hierarchies:

### To identify additional source sites in the source hierarchy

1. In the Configuration Manager console, click **Administration**.
2. In the **Administration** workspace, expand **Migration**, and then click **Source Hierarchy**.
3. Choose the site that you want to configure as a source site.
4. On the **Home** tab, in the **Source Site** group, click **Configure**.
5. In the **Source Site Credentials** dialog box, for the source site access accounts, specify accounts that have the following permissions:

    - Source Site Account: **Read** permission to the SMS Provider for the specified top-level site in the source hierarchy. Distribution point sharing and upgrades require **Modify** and **Delete** permissions to the site in the source hierarchy.
    - Source Site Database Account: **Read** and **Execute** permission to the SQL Server database for the specified top-level site in the source hierarchy.

    If you specify the use of the computer account, Configuration Manager uses the computer account of the top-level site of the destination hierarchy. For this option, ensure that this account is a member of the security group **Distributed COM Users** in the domain where the top-level site of the source hierarchy resides.
6. To share distribution points between the source and destination hierarchies, select the **Enable distribution point sharing for the source site server** check box. If you do not enable distribution point sharing at this time, you can do so by editing the credentials for the source site after data gathering has finished.
7. Click **OK** to save the configuration. This opens the **Data Gathering Status** dialog box, and data gathering starts automatically.
8. When data gathering finishes, click **Close** to complete the configuration.