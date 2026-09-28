---
layout: Conceptual
title: Reduce task sequence policy size - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/reduce-task-sequence-policy-size
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
description: When the size of the task sequence policy exceeds 32 MB, the client fails to process the large policy. The client then fails to run the task sequence deployment. Manage the size of task sequence policy to reduce deployment failures.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ac8f1af8-faf6-933a-298d-6a8b74ad86f3
document_version_independent_id: ac8f1af8-faf6-933a-298d-6a8b74ad86f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/reduce-task-sequence-policy-size.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/reduce-task-sequence-policy-size
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/reduce-task-sequence-policy-size.md
cmProducts: []
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: f3dacae3-fc19-f454-8134-e157e08eca91
---

# Reduce task sequence policy size - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When the size of the task sequence policy exceeds 32 MB, the client fails to process the large policy. The client then fails to run the task sequence deployment. The size of the task sequence as stored in the site database is smaller, but can still cause problems if too large. When the client processes the entire task sequence policy, the expanded size can cause problems over 32 MB.

To check for the 32-MB task sequence policy size on clients, use [management insights](../../core/servers/manage/management-insights#operating-system-deployment).

Configuration Manager restricts the following actions for a task sequence in the site database that's greater than 2 MB in size:

- Save changes in the task sequence editor
- Save changes with PowerShell cmdlets
- Import a new task sequence
- Any other change using supported SDK methods

For example, if you try to save changes to a large task sequence, the task sequence editor will display an error.

Tip

The behavior in version 2010 and later checks for the 2 MB size limit on the task sequence as stored in the site database. When the client processes the entire task sequence policy, the expanded size can cause problems over 32 MB. The management insights check for the 32 MB task sequence policy size.

When you view the list of task sequences in the Configuration Manager console, add the **Size (KB)** column. Use this column to identify large task sequences that can cause problems.

## Actions to reduce task sequence size

To help reduce the size of task sequences and task sequence deployment policies, take the following actions:

- Separate functional segments into child task sequences, and use the [Run Task Sequence](../understand/task-sequence-steps#child-task-sequence) step. Keep each task sequence less than 2 MB in the database. Each task sequence has a separate 32-MB limit on its policy size.

    Note

    Reducing the total number of steps and groups in a task sequence has minimal impact on the policy size. Each step is generally a couple of KB in policy. Moving groups of steps to a child task sequence is more impactful.
- Reduce the number of software updates in deployments to the same collection as the task sequence.
- Instead of entering a script in the [Run PowerShell Script](../understand/task-sequence-steps#BKMK_RunPowerShellScript) step, reference it via a package.
- There's an 8-KB limit on the size of the task sequence *environment* when it runs. Review the usage of custom task sequence variables, which can also contribute to the policy size.
- As a last resort, split a complex, dynamic task sequence into separate task sequences with distinct deployments to different collections.