---
layout: Conceptual
title: Monitor migration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-to-monitor-migration-activity
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
description: Learn how to use the Configuration Manager console to monitor the progress and success of migration jobs.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: upgrade-and-migration-article
ms.collection: tier3
locale: en-us
document_id: d2573b53-0c23-c267-4784-ca966bad8d3b
document_version_independent_id: aeb0d15e-5512-8121-c7a7-1146953a7a3d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/migration/planning-to-monitor-migration-activity.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/migration/planning-to-monitor-migration-activity
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/migration/planning-to-monitor-migration-activity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 48e22a7f-26b0-d816-8a7f-361c41283767
---

# Monitor migration - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With Configuration Manager, you can monitor migration in the Configuration Manager console that connects to the destination hierarchy. In the Configuration Manager console in the **Administration** workspace, you can use the **Migration** node to monitor the progress and success of migration jobs. You can view summary information for each migration job that identifies objects that have migrated, those objects that have not yet migrated, and the number of objects that are excluded from a migration job. You will also see details about any migration problems.

## View Migration Progress

To view the progress of a migration job, use any of the following actions:

- In the **Administration** workspace of the Configuration Manager console, expand the **Migration Jobs** node, select a migration job, and then select the **Objects in Job** tab.
- Use the Configuration Manager log files to review the migration progress or to identify any problems. Migration Manager is the Configuration Manager process that tracks migration actions and records these in the migmctrl.log file in the **&lt;InstallationPath&gt;\LOGS** folder on the site server.

    Note

    If a migration job fails, review the details in the migmctrl.log file as soon as possible. The migration log entries are continually added to the file and overwrite old details. If the entries are overwritten, you might not be able to identify whether any problems that you might encounter with the migrated objects relate to migration issues. Migration activity is logged at the top-level site of the hierarchy regardless of the site your Configuration Manager console connects to when you configure migration.
- Use Configuration Manager reporting. Configuration Manager provides several built-in reports for migration, or you can edit those reports to fit your requirements. For more information about Configuration Manager reports, see [Introduction to reporting](../servers/manage/introduction-to-reporting).