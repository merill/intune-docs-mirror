---
layout: Conceptual
title: Update reset tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/update-reset-tool
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
description: Use the update reset tool for in-console updates for Configuration Manager.
ms.date: 2017-07-31T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ef8d818d-d2ed-1173-b3a3-97fdd0d01f58
document_version_independent_id: 91027917-4660-91cc-8544-ea08f8877c28
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/update-reset-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/update-reset-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/update-reset-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: d21c6f87-51fc-fe62-81b9-c52e85199000
---

# Update reset tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Beginning with version 1706, Configuration Manager primary sites, and central administration sites include the Configuration Manager Update Reset Tool, **CMUpdateReset.exe**. Use the tool to fix issues when in-console updates have problems downloading or replicating. The tool is found in the ***\cd.latest\SMSSETUP\TOOLS*** folder of the site server.

You can use this tool with any version of the current branch that remains in support.

Use this tool when an [in-console update](install-in-console-updates) has not yet installed and is in a failed state. A failed state means that the update download is in progress but stuck or taking an excessively long time. A long time is considered to be hours longer than your historical expectations for update packages of similar size. It can also be a failure to replicate the update to child primary sites.

When you run the tool, it runs against the update that you specify. By default, the tool does not delete successfully installed or downloaded updates.

### Prerequisites

The account you use to run the tool requires the following permissions:

- **Read** and **Write** permissions to the site database of the central administration site and to each primary site in your hierarchy. To set these permissions, you can add the user account as a member of the **db\_datawriter** and **db\_datareader**[fixed database roles](/en-us/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles) on the Configuration Manager database of each site. The tool does not interact with secondary sites.
- **Local Administrator** on the top-level site of your hierarchy.
- **Local Administrator** on the computer that hosts the service connection point.

You need the GUID of the update package that you want to reset. To get the GUID:

1. In the console, go to **Administration** &gt; **Updates and Servicing**.
2. In the display pane, right-click the heading of one of the columns (like **State**), then select **Package Guid** to add that column to the display.
3. The column now shows the update package GUID.

Tip

To copy the GUID, select the row for the update package you want to reset, and then use CTRL+C to copy that row. If you paste your copied selection into a text editor, you can then copy only the GUID for use as a command-line parameter when you run the tool.

### Run the tool

The tool must be run on the top-level site of the hierarchy.

When you run the tool, use command-line parameters to specify:

- The SQL Server at the top-tier site of the hierarchy.
- The site database name at the top-tier site.
- The GUID of the update package you want to reset.

Based on the status of the update, the tool identifies the additional servers it needs to access.

If the update package is in a *post download* state, the tool does not clean up the package. As an option, you can force the removal of a successfully downloaded update by using the force delete parameter (See command-line parameters later in this topic).

After the tool runs:

- If a package was deleted, restart the SMS\_Executive service at the top-tier site. Then, check for updates so you can download the package again.
- If a package was not deleted, you do not need to take any action. The update reinitializes and then restarts replication or installation.

**Command-line parameters:**

| Parameter | Description |
| --- | --- |
| **-S &lt;FQDN of the SQL Server of your top-tier site&gt;** | *Required* Specify the FQDN of the SQL Server that hosts the site database for the top-tier site of your hierarchy. |
| **-D &lt;Database name&gt;** | *Required* Specify the name of the database at the top-tier site. |
| **-P &lt;Package GUID&gt;** | *Required* Specify the GUID for the update package you want to reset. |
| **-I &lt;SQL Server instance name&gt;** | *Optional* Identify the instance of SQL Server that hosts the site database. |
| **-FDELETE** | *Optional* Force deletion of a successfully downloaded update package. |

**Examples:** In a typical scenario, you want to reset an update that has download problems. Your SQL Servers FQDN is *server1.fabrikam.com*, the site database is *CM\_XYZ*, and the package GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*. You run: ***CMUpdateReset.exe -S server1.fabrikam.com -D CM\_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

In a more extreme scenario, you want to force deletion of problematic update package. Your SQL Servers FQDN is *server1.fabrikam.com*, the site database is *CM\_XYZ*, and the package GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*. You run: ***CMUpdateReset.exe -FDELETE -S server1.fabrikam.com -D CM\_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***