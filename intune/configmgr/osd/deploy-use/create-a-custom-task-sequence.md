---
layout: Conceptual
title: Create a custom task sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-custom-task-sequence
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
description: Edit a custom task sequence in Configuration Manager to add steps to the task sequence.
ms.date: 2020-04-01T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c2b76bbe-9f9b-896b-aeb9-d840e6360327
document_version_independent_id: 2e74654c-85cd-9ce0-8892-d30326e75d96
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-a-custom-task-sequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-a-custom-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-a-custom-task-sequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 20017e0c-589e-6a3f-4f6d-fe3f9e793141
---

# Create a custom task sequence - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you create a custom task sequence in Configuration Manager, it contains no task sequence steps. After you create the task sequence, edit it, and add the task sequence steps you need.

## Create a custom task sequence

Use the following procedure to create a custom task sequence:

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select the **Task Sequences** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Task Sequence**. This action starts the Create Task Sequence Wizard.
3. On the **Create a New Task Sequence** page, select **Create a new custom task sequence**.
4. On the **Task Sequence Information** page, specify:

    - A name for the task sequence
    - A description of the task sequence
    - An optional boot image for the task sequence to use

After you complete the Create Task Sequence Wizard, Configuration Manager adds the custom task sequence to the **Task Sequences** node. You can now edit this task sequence to add task sequence steps to it.