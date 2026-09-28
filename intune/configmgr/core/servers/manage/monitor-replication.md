---
layout: Conceptual
title: Monitor database replication - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/monitor-replication
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
description: Learn how to monitor SQL Server replication in your Configuration Manager hierarchy.
ms.date: 2022-04-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: fb2ac69f-ffde-8ad1-3483-1f3d5ccd5581
document_version_independent_id: 10a8fbf1-ac62-8cb7-d524-65f720740fc1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/monitor-replication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/monitor-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/monitor-replication.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d91f49d9-0325-3a35-e684-31301d413d6c
---

# Monitor database replication - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Monitor details for database replication with the **Database Replication** node in the **Monitoring** workspace of the Configuration Manager console. You can monitor the status of replication links between sites. It also shows initialization and replication of replication groups for the site to which you connect.

Tip

Although a **Database Replication** node also appears under the **Hierarchy Configuration** node in the **Administration** workspace, you can't view the replication status for database replication links from that location.

## Replication link status

Database replication between sites involves the replication of several sets of information, called *replication groups*. Each replication group sends and receives data with different priorities. By default, you can't modify the data contained in a replication group and the frequency of replication.

When a replication link is active, and its status isn't failed or degraded, all groups replicate quickly. If one or more groups fail to complete replication in the expected period of time, the link displays as *degraded*. Degraded links can still function, but you should monitor them to make sure they return to active status. Investigate them to make sure additional degradation or replication failures don't occur.

For each replication link, specify the number of times that an unsuccessfully replicated group retries. After this number of retries, the site sets the status of the link to degraded or failed. Even if all but one group replicates successfully, the site sets the status of the link to degraded or failed. It sets this status because the one replication group fails to complete replication in the specified number of attempts. For more information, see the [Database replication thresholds](../../plan-design/hierarchy/database-replication#database-replication-thresholds).

Use the following information to understand the status of replication links that might require further investigation:

### Link is active

No problems have been detected, and communication across the link is current.

While a parent site is updating to a new version, and you view the link status from the child site, the link status displays as active. After the update, until the child site is at the same version as the parent site, the link status displays as active when viewed from the parent site. When viewed from the child site, it displays as being configured.

### Link is degraded

Replication is functional, but at least one replication object or group is delayed. Monitor links that are in this state. Review information from both sites on the link for indications that the link might fail.

A link can also display a status of degraded when the site that receives replicated data is unable to quickly commit the data to the database. This behavior happens when large volumes of data replicate. For example, you deploy a software update to a large number of computers. The parent site on the link might take some time to process this volume of replicated data. A processing lag at the parent site results in it setting the link status to degraded until it can successfully process the backlog of data.

### Link has failed

Replication isn't functional. It's possible that a replication link might recover without further action. To investigate and help remediate replication on this link, use the Replication Link Analyzer (RLA).

This status can also indicate a problem with the physical network between the parent and child site on the replication link.

## Monitor replication status

Use the **Database Replication** node in the **Monitoring** workspace to view the status for a replication link. View details about the database at each site on the replication link. You can also view details about replication groups. To view these details, select a replication link, and then select the appropriate tab for the replication status you want to view.

The following sections give details about the different tabs for replication status:

### Summary

View high-level information about the replication of site data and global data between the two sites on a link.

Select **View reports for historical traffic data** to view a report that shows details about the network bandwidth used by replication across the link.

### Parent Site

For the parent site on a replication link, view details about the database, which include:

- Firewall ports for the SQL Server
- Free disk space
- Database file locations
- Certificates

### Child Site

For the child site on a replication link, view details about the database, which include:

- Firewall ports for the SQL Server
- Free disk space
- Database file locations
- Certificates

### Initialization Detail

View the initialization status for groups that replicate across the link. This information can help you identify when initialization of replication data is in progress or has failed.

Use this information to identify when a site might be in *interoperability mode*. Interoperability mode is when the child site doesn't run the same version of Configuration Manager as the parent site.

### Replication Detail

View the replication status for each group that replicates across the link. Use this information to help identify problems or delays for the replication of specific data. It can help determine the appropriate database replication thresholds for this link. For more information, see [Database replication thresholds](../../plan-design/hierarchy/database-replication#database-replication-thresholds).

Tip

Replication groups for site data are sent only from the child site to the parent site. Replication groups for global data replicate in both directions.

## Replication Link Analyzer

Configuration Manager includes the **Replication Link Analyzer** (RLA), which you use to analyze and repair replication issues. Use RLA to remediate link failures when replication fails. It's also useful when replication stops working but the site hasn't yet reported it as failed.

Use RLA to remediate replication issues between the following computers in the hierarchy:

- Between a site server and the site database server
- Between a site's database server and another site's database server, otherwise known as intersite replication

Note

The direction of the replication failure doesn't matter.

Run RLA in either the Configuration Manager console or at a command prompt:

- To run in the Configuration Manager console: Go to the **Monitoring** workspace, and select the **Database Replication** node. Select the replication link that you want to analyze, and then in ribbon, select **Replication Link Analyzer**.
- To run at a command prompt, type the following command: `%ProgramFiles(x86)%\Microsoft Endpoint Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe <source site server FQDN> <destination site server FQDN>`

    Important

    Starting in version 1910, this path changed to use the `Microsoft Endpoint Manager` folder. Make sure you don't use an older version of the file that might exist in another folder.

When you run RLA, it detects problems by using a series of diagnostic rules and checks. You view the problems that the tool identifies. When it has instructions to resolve an issue, it displays them. If RLA can automatically remediate a problem, it presents you with that option.

When RLA finishes, it saves the results in the following XML-based report and a log file on the desktop of the user who runs the tool:

- ReplicationAnalysis.xml
- ReplicationLinkAnalysis.log

RLA stops the following services while it remediates some problems. It restarts these services when remediation is complete:

- SMS\_SITE\_COMPONENT\_MANAGER
- SMS\_EXECUTIVE

If RLA fails to complete remediation, restart these services on the site server if necessary.

RLA logs all investigation and remediation actions to provide additional details that it doesn't display in the wizard.

### RLA prerequisites

The account that you use to run RLA must have the following permissions:

- Local administrator rights on each computer that's involved in the replication link.
- Sysadmin rights on each SQL Server database that's involved in the replication link.

Note

The account doesn't require a specific Configuration Manager role-based administration security role. An administrative user with access to the **Database Replication** node can run the tool in the Configuration Manager console. A system administrator with sufficient rights to each computer can run the tool at a command prompt.

### RLA known issue

RLA generates SQL Server Service Broker (SSB) certificate errors for primary sites that upgraded from System Center 2012 Configuration Manager. This issue is because of changes in the names of the certificates in Configuration Manager current branch. You can safely ignore these errors.

## Monitoring database replication

### Monitor high-level site-to-site database replication status

1. In the Configuration Manager console, go to the **Monitoring** workspace.
2. Select the **Site Hierarchy** node to open the **Hierarchy Diagram** view.
3. Hover the mouse pointer on the line between the two sites. View the status of global and site data replication for these sites.

### Monitor the status of a replication link

1. In the Configuration Manager console, go to the **Monitoring** workspace.
2. Select the **Database Replication** node, and then select the replication link that you want to monitor. Then select the appropriate tab to view different details about the replication status for that link.