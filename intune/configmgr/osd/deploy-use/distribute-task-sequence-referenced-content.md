---
layout: Conceptual
title: Distribute referenced content - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/distribute-task-sequence-referenced-content
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
description: Before clients run a task sequence that references content, distribute that content to distribution points.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e20810fb-0bc9-eb35-7962-3279b7f118c8
document_version_independent_id: e20810fb-0bc9-eb35-7962-3279b7f118c8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/distribute-task-sequence-referenced-content.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/distribute-task-sequence-referenced-content
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/distribute-task-sequence-referenced-content.md
cmProducts: []
platformId: 4e85fa4b-cee5-b859-0a7e-431701d25f6e
---

# Distribute referenced content - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before clients run a task sequence that references content, distribute that content to distribution points. At any time, you can select the task sequence and distribute its content to build a new list of reference packages for distribution. If you make changes to the task sequence with updated content, redistribute the content before it's available to clients.

## Distribute content

Use the following procedure to distribute the content that is referenced by a task sequence:

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select the **Task Sequences** node.
2. In the **Task Sequence** list, select the task sequence that you want to distribute.
3. On the **Home** tab of the ribbon, in the **Deployment** group, select **Distribute Content**. This action starts the Distribute Content Wizard.
4. On the **General** page, verify that the correct task sequence is selected for distribution.
5. On the **Content** page, verify the content to distribute, such as the boot image referenced by the task sequence.
6. On the **Content Destination** page, specify the collections, distribution point, or distribution point group where you want to distribute the task sequence contents.

    Important

    If the task sequence that you selected references content that's already distributed to a specific distribution point, the wizard doesn't list that distribution point.
7. Complete the wizard.

## Prestage content

You can also prestage the content referenced in the task sequence. Configuration Manager creates a compressed, prestaged content file that contains the files, associated dependencies, and associated metadata for the content that you select. Then you manually import the content at a site server, secondary site, or distribution point. For more information about how to prestage content files, see [Prestage content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage).