---
layout: Conceptual
title: Capture and restore user state - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-capture-and-restore-user-state
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
description: Use Configuration Manager task sequences to capture and restore the user state data in OS deployment scenarios.
ms.date: 2018-08-17T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 92bc7b99-ad4a-f342-3bc2-8d76ea9cbccc
document_version_independent_id: bd750b12-2373-c35e-70da-bf0cfc4fde2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-a-task-sequence-to-capture-and-restore-user-state
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6a079aed-b4ff-8908-2159-7c8f122bc5db
---

# Capture and restore user state - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use Configuration Manager task sequences to capture and restore the user state data in OS deployment scenarios. In these scenarios, you want to retain the user state of the current OS. Depending on the type of task sequence you create, the capture and restore steps might be automatically added as part of the task sequence. In other scenarios, you might need to manually add the capture and restore steps to the task sequence. This article provides the steps that you must add to an existing task sequence to capture and restore user state data.

## Task sequence steps

To capture and restore the user state, add the following steps to the task sequence:

- [Request State Store](../understand/task-sequence-steps#BKMK_RequestStateStore): If you store the user state on the state migration point, you need this step.
- [Capture User State](../understand/task-sequence-steps#BKMK_CaptureUserState): This step captures the user state data. It then stores the data on either the state migration point or the local disk using hardlinks.
- [Restore User State](../understand/task-sequence-steps#BKMK_RestoreUserState): This step restores the user state data on the destination computer. It can retrieve the data from a state migration point or if hardlinked on the local disk.
- [Release State Store](../understand/task-sequence-steps#BKMK_ReleaseStateStore): If you store the user state on the state migration point, you need this step. This step removes the data from the state migration point.

Use the following procedures to add the task sequence steps needed to capture and restore the user state. For more information about creating a task sequence, see [Manage task sequences to automate tasks](manage-task-sequences-to-automate-tasks).

## Capture the user state

To add task sequence steps to capture the user state, use the following steps:

1. In the **Task Sequence** list, select a task sequence, and then click **Edit**.
2. If you're using a state migration point to store the user state, add the **Request State Store** step to the task sequence. In the **Task Sequence Editor**, click **Add**. Point to **User State**, and then click **Request State Store**. Configure the properties and options for this step, and then click **Apply**. For more information about the available settings, see [Request State Store](../understand/task-sequence-steps#BKMK_RequestStateStore).
3. Add the **Capture User State** step to the task sequence. In the **Task Sequence Editor**, click **Add**. Point to **User State**, and then click **Capture User State**. Configure the properties and options for this step, and then click **Apply**. For more information about the available settings, see [Capture User State](../understand/task-sequence-steps#BKMK_CaptureUserState).

    Important

    When you add this step to your task sequence, also set the **OSDStateStorePath** task sequence variable to specify where to store the user state data. If you store the user state locally, don't specify a root folder as that can cause the task sequence to fail. When you store the user data locally always use a folder or subfolder. For more information about this variable, see [Task sequence variables](../understand/task-sequence-variables#OSDStateStorePath).
4. If you're using a state migration point, add the **Release State Store** step to the task sequence. In the **Task Sequence Editor**, click **Add**. Point to **User State**, and then click **Release State Store**. Configure the properties and options for this step, and then click **Apply**. For more information about the available settings, see [Release State Store](../understand/task-sequence-steps#BKMK_ReleaseStateStore).

    Important

    The task sequence action that runs before the **Release State Store** step must be successful before the **Release State Store** step starts.

Deploy this task sequence to capture the user state on a destination computer. For information about how to deploy task sequences, see [Deploy a task sequence](deploy-a-task-sequence).

## Restore the user state

To add task sequence steps to restore the user state, use the following steps:

1. In the **Task Sequence** list, select a task sequence, and then click **Edit**.
2. Add the **Restore User State** step to the task sequence. In the **Task Sequence Editor**, click **Add**. Point to **User State**, and then click **Restore User State**. This step establishes a connection to the state migration point if necessary. Configure the properties and options for this step, and then click **Apply**. For more information about the available settings, see [Restore User State](../understand/task-sequence-steps#BKMK_RestoreUserState).

    Important

    When you use the [Capture User State](../understand/task-sequence-steps#BKMK_CaptureUserState) step with the option to **Capture all user profiles with standard options**, you must select the **Restore local computer user profiles** setting in the **Restore User State** step. Otherwise the task sequence will fail.

    Note

    If you store the user state by using local hardlinks and the restore isn't successful, you can manually delete the hardlinks that were created to store the data. The task sequence can run the USMTUtils tool to automate this action with a [Run Command Line](../understand/task-sequence-steps#BKMK_RunCommandLine) step. If you use USMTUtils to delete the hardlink, add a [Restart Computer](../understand/task-sequence-steps#BKMK_RestartComputer) step after you run USMTUtils.
3. If you're using a state migration point to store the user state, add the **Release State Store** step to the task sequence. In the **Task Sequence Editor**, click **Add**. Point to **User State**, and then click **Release State Store**. Configure the properties and options for this step, and then click **Apply**. For more information about the available settings, see [Release State Store](../understand/task-sequence-steps#BKMK_ReleaseStateStore).

    Important

    The task sequence action that runs before the **Release State Store** step must be successful before the **Release State Store** step starts.

Deploy this task sequence to restore the user state on a destination computer. For information about deploying task sequences, see [Deploy a task sequence](deploy-a-task-sequence).