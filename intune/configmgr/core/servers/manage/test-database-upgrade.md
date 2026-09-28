---
layout: Conceptual
title: Test database update - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/test-database-upgrade
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
description: Test upgrade the site database when installing updates for Configuration Manager.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: cdfbb8bf-e68c-201a-2973-b3f85c329845
document_version_independent_id: df82b414-e376-7c0b-4d6c-fdbe69f48194
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/test-database-upgrade.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/test-database-upgrade
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/test-database-upgrade.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bba62c59-6b53-4be4-8b9d-6624f9184c22
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/f3a81ffb-ee36-4ec7-b54a-01b6681aff65
platformId: 021d8323-62de-a836-fe7e-59176332bd39
---

# Test database update - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If necessary, you can run a test database upgrade before you install an in-console update for the current branch of Configuration Manager.

Important

The test upgrade is no longer a required or recommend step for most sites.

If your database is suspect, or is modified by customizations not explicitly supported by Configuration Manager, continue to use this process.

## Do I need to run a test upgrade?

The deprecation of this upgrade test is made possible because of changes that are introduced with Configuration Manager current branch. These changes simplify the process and speed by which setup can update a production environment to a newer version. This redesign was done to help you stay current with less risk, and less operational overhead when installing each new update.

The changes are to how updates install, including logic that automatically rolls back a failed update without the need to run a site recovery. These changes enable the use of the console to manage update installations, and include an option to [retry installation of a failed update](post-in-console-updates#retry-installation-of-a-failed-update).

Tip

When you upgrade to Configuration Manager current branch from an older product, like System Center 2012 Configuration Manager, [test database upgrades remain a recommended step](../deploy/install/upgrade-to-configuration-manager#test-the-site-database-upgrade).

If you still plan to test the upgrade of a site database when you install an in-console update, the following information supplements the [guidance on installing an in-console update](install-in-console-updates).

## Prepare to run a test database upgrade

To run the upgrade test, use the Configuration Manager Setup from the [CD.Latest folder](the-cd.latest-folder). Use the same version of the source files as the version of Configuration Manager to which you're updating.

For example, to test the database update for version YYMM:

- You need at least one site on version YYMM from which you can get that CD.Latest folder.
- If you don't have a site that runs the required version, consider installing a site in a lab environment. Then update that site to the new version. This process creates the CD.Latest folder with the correct version of source files.

The upgrade test runs against a backup of your site database that you restore to a separate instance of SQL Server. After the test upgrade completes, discard the upgraded database. It can't be used by a Configuration Manager site.

## Run the test upgrade

1. Use Configuration Manager Setup and the source files from the **CD.Latest** folder of a site that runs the version that you plan to update to.
2. Copy the **CD.Latest** folder to a location on the SQL Server instance that you'll use to run the test database upgrade.
3. Create a backup of the site database that you want to test upgrade. Then restore a copy of that database to an instance of SQL Server that doesn't host a Configuration Manager site. The SQL Server instance needs to be the same edition of SQL Server as your site database. For more information, see [Quickstart: Backup and restore a SQL Server database on-premises](/en-us/sql/relational-databases/backup-restore/quickstart-backup-restore-database).
4. After you restore the database copy, run **Setup** from the CD.Latest folder. When you run Setup, use the `/TESTDBUPGRADE` command-line option. If the SQL Server instance that hosts the database copy isn't the default instance, provide the [command-line options](../deploy/install/command-line-options-for-setup#testdbupgrade) to identify the instance that hosts the site database copy.

    For example, you have a site database with the database name `CM_ABC`. You restore a copy of this site database to a supported instance of SQL Server with the instance name `DBTest`. To test an upgrade of this copy of the site database, use the following command line: `setup.exe /TESTDBUPGRADE DBtest\CM_ABC`

    You can find Setup.exe in the following location on the source media for Configuration Manager: `SMSSETUP\BIN\X64`
5. On the instance of SQL Server where you run the upgrade test, monitor the **ConfigMgrSetup.log** in the root of the system drive for progress and success.

    If the test upgrade fails, fix any issues related to the site database upgrade failure. Then, create a new backup of the site database and retest the upgrade of the new copy of the database.