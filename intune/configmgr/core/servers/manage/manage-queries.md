---
layout: Conceptual
title: Manage queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/manage-queries
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
description: Learn how to manage your queries. Includes a table for detailed reference.
ms.date: 2019-04-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7b6f086c-da23-7c6c-504c-46114d1588a3
document_version_independent_id: 5bd2a52c-efe8-dcda-e980-e650ac9d74b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/manage-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/manage-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/manage-queries.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1d792537-2ade-30dd-ce80-3b938e0860b8
---

# Manage queries - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article can help you manage queries in Configuration Manager.

For information about how to create queries, see [How to create queries](create-queries).

## Manage queries

In the **Monitoring** workspace, select **Queries**, select the query to manage, and then select a management task.

The following table provides information about the management tasks.

| Management task | Details |
| --- | --- |
| **Run** | Runs the selected query and displays the results in the Configuration Manager console. |
| **Install Client** | Opens the **Install Client Wizard**, which lets you install the Configuration Manager client on computers returned by the selected query. This option isn't available for queries that return mobile devices, users, or user groups.  For more information about how to install Configuration Manager clients by using client push, see [Deploy clients to Windows computers](../../clients/deploy/deploy-clients-to-windows-computers). |
| **Export** | Opens the **Export Objects Wizard**. This wizard lets you export the query to a Managed Object Format (MOF) file that you can then import at another site. |
| **Move** | Opens the **Move Selected Items** dialog box. This dialog box lets you move the selected query to a folder that you previously created under the **Queries** node. |