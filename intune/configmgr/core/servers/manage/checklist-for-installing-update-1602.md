---
layout: Conceptual
title: Checklist for 1602 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-1602
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
description: Learn about actions to take before updating from Configuration Manager version 1511 to version 1602.
ms.date: 2017-02-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: checklist
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 705a7918-dea6-758c-4289-6a491a8c38fc
document_version_independent_id: 9f293f33-f755-34dd-8a15-2528b88dc908
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/checklist-for-installing-update-1602.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/checklist-for-installing-update-1602
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/checklist-for-installing-update-1602.md
platformId: 307be817-242b-076f-ca5e-b55615ea4e5c
---

# Checklist for 1602 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before updating from Configuration Manager version 1511 to version 1602, review the following information and checklist for actions to take before starting the update.

**About installing update 1602:**

Update 1602 can only be installed at the top-level site of your hierarchy. This means you initiate the installation from your central administration site if you have one, or from your stand-alone primary site.

- Child primary sites install the update automatically after the central administration site finishes installing the update. You can use maintenance windows to control when a site installs updates. Beginning with the release of the 1602 update, maintenance windows have been renamed *service windows*. For more information, see [Service windows for site servers](service-windows).
- You must manually update secondary sites from within the Configuration Manager console after the primary parent site finishes installing the update. Automatic updates of secondary site servers are not supported.

When the site server installs the update, site system roles that are installed on the site server and those that are installed on remote computers automatically get updated. Therefore, before installing the update, make sure each site system server meets any new prerequisites for operations with the new update version.

The first time you use a Configuration Manager console after the update has finished, you will be prompted to update that console. To do so, you must run Configuration Manager setup on the computer that hosts the console, and choose the option to update the console. We recommend that you do not delay installing the update to the console.

**Checklist:**

**Ensure that all sites run a supported version of Configuration Manager:** Each site server in the hierarchy must run Configuration Manager version 1511 before you can start the installation of update 1602.

**Review installed Microsoft .NET versions on site system servers:** When a site installs update 1602, Configuration Manager automatically installs .NET Framework 4.5.2 on each computer that hosts one of the following site system roles (if .NET Framework 4.5 or later is not already installed):

- Enrollment proxy point
- Enrollment point
- Management point
- Service connection point

This installation can put the site system server into a reboot pending state, and report errors to the Configuration Manager component status viewer. Additionally, .NET applications on the server might experience random failures until the server is rebooted.

For more information, see [Site and site system prerequisites](../../plan-design/configs/site-and-site-system-prerequisites).

**Review the site and hierarchy status and verify that there are no unresolved issues:** Before you update a site, resolve all operational issues for the site server, the site database server, and site system roles that are installed on remote computers. A site update can fail due to existing operational problems.

For more information, see [Use the status system](use-status-system).

**Review file and data replication between sites:** Ensure that file and database replication between sites is operational and current. Delays or backlogs in either can prevent a smooth, successful update.

For database replication, you can use the Replication Link Analyzer to help resolve issues prior to starting the update.

For more information, see [About the Replication Link Analyzer](monitor-replication#BKMK_RLA).

**Install all applicable critical updates for operating systems on computers that host the site, the site database server, and remote site system roles:** Before you install an update for Configuration Manager, install any critical updates for each applicable site system. If an update that you install requires a restart, restart the applicable computers before you start the upgrade.

**Disable database replicas for management points at primary sites:** Configuration Manager cannot successfully update a primary site that has a database replica for management points enabled. Disable database replication before you:

- Create a backup of the site database to test the database upgrade.
- Install an update for Configuration Manager.

For more information, see [Database replicas for management points for Configuration Manager](../deploy/configure/database-replicas-for-management-points).

**Reconfigure software update points that use NLBs:** Configuration Manager cannot update a site that uses a Network Load Balancing (NLB) cluster to host software update points. If you use NLB clusters for software update points, use Windows PowerShell to remove the NLB cluster.

For more information, see [Plan for software updates](../../../sum/plan-design/plan-for-software-updates).

**Disable all site maintenance tasks at each site for the duration of the update installation on that site:** Before you install updates, disable any site maintenance task that might run during the time the update process is active. These tasks include (but are not limited) to the following:

- Backup Site Server
- Delete Aged Client Operations
- Delete Aged Discovery Data

When a site database maintenance task runs during the update installation, the update installation can fail. Before you disable a task, record the schedule of the task so you can restore its configuration after the update has installed.

For more information, see [Maintenance tasks for Configuration Manager](maintenance-tasks) and [Reference for maintenance tasks for Configuration Manager](reference-for-maintenance-tasks).

**Temporarily stop any antivirus software on the Configuration Manager servers:** Before you update a site, ensure that you have stopped antivirus software on the Configuration Manager servers. 

**Create a backup of the site database at the central administration site and primary sites:** Before you update a site, backup the site database to ensure that you have a successful backup to use for disaster recovery.

For more information, see [Backup and recovery for Configuration Manager](backup-and-recovery).

**Backup a customized Configuration.mof file:** If you use a customized Configuration.mof file to define data classes that you use with hardware inventory, create a backup of this file before updating the site. After the update, restore this file to your version 1602 site. When you update a site, the current file is overwritten with the original (default) version of the file. For more information about using this file, see [How to extend hardware inventory](../../clients/manage/inventory/extend-hardware-inventory).

**Test the database upgrade on a copy of the most recent site database backup:** Before you update a Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.

- You should test the site database upgrade process because when you upgrade a site, the site database might be modified.
- Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.
- A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.
- Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.
- If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database. Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable.

**Plan for client piloting:** When you install an update that updates the client, you can test that new client update in pre-production before it deploys and upgrades all your active clients.

To take advantage of this option, you must configure your site to support automatic upgrades for pre-production before beginning installation of the update. For more information, see [Upgrade clients](../../clients/manage/upgrade/upgrade-clients) and [How to test client upgrades in a pre-production collection](../../clients/manage/upgrade/test-client-upgrades).

**Plan to use Maintenance windows to control when site servers install updates:** You can use the maintenance windows to define a period of time during which updates to the site server can be installed. This can help you control when sites in your hierarchy install the update.

Beginning with the release of the 1602 update, maintenance windows have been renamed *service windows*. For more information, see [Service windows for site servers](service-windows).

**Run setup prerequisite checker:** Before you install update 1602, you can run the prerequisite checker independently from the update installation. When you install the update on the site, prerequisite checker runs again.

For more information, see **Step 3: Run the prerequisite checker before installing an update** in the [Updates for Configuration Manager](updates) topic.

Important

When the prerequisite checker runs independently or as part of an update installation, the process updates some product source files that are used for site maintenance tasks. Therefore, after running the prerequisite checker but before installing the 1602 update, if you need to perform a site maintenance task, run **Setupwfe.exe** (Configuration Manager Setup) from the CD.Latest folder on the site server.

**Update sites:** You are now ready to start the update installation for your hierarchy. We recommend that you plan to install the update outside of normal business hours for each site, when the process of installing the update and its actions to reinstall site components and site system roles will have the least effect on your business operations.

For more information, see [Updates for Configuration Manager](updates).