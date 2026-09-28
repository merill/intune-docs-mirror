---
layout: Conceptual
title: Export and import task sequences - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/export-import-task-sequences
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
description: Export and import task sequences with or without their related objects.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0f3d5222-0318-fa6d-8036-2c12981f88e4
document_version_independent_id: 0f3d5222-0318-fa6d-8036-2c12981f88e4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/export-import-task-sequences.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/export-import-task-sequences
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/export-import-task-sequences.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 8ec03b77-2893-44e1-fee6-11da8f501c0c
---

# Export and import task sequences - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Export and import task sequences with or without their related objects. Use this process to move task sequences between hierarchies. For example, you create a task sequence in a development lab and export it. You then import that task sequence into the production environment to deploy.

This referenced content includes the following objects:

- OS images
- Boot images
- Packages like the client install package
- Driver packages
- Applications with dependencies
- Other task sequences referenced with the **Run task sequence** step

Consider the following points when you export and import task sequences:

- Configuration Manager doesn't export passwords in the task sequence. If you export and import a task sequence that contains passwords, edit the imported task sequence to reenter any passwords. Review the following steps that may include a password:

    - [Join Domain or Workgroup](../understand/task-sequence-steps#BKMK_JoinDomainorWorkgroup)
    - [Connect To Network Folder](../understand/task-sequence-steps#BKMK_ConnectToNetworkFolder)
    - [Run Command Line](../understand/task-sequence-steps#BKMK_RunCommandLine)
- When you export a task sequence with the **Set Dynamic Variables** step, Configuration Manager doesn't export values for variables that you configure with the **Secret value** setting. Reenter the values for these variables after you import the task sequence.
- When you have multiple primary sites, import task sequences at the central administration site.

## Export

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select the **Task Sequences** node.
2. In the **Task Sequence** list, select the task sequences that you want to export. If you select more than one task sequence, they're all stored in one export file.
3. On the **Home** tab of the ribbon, in the **Task Sequence** group, select **Export**. This action starts the Export Task Sequence Wizard.
4. On the **General** page, specify the following settings:

    - **File**: Specify the location and name of the export file. If you enter the file name directly, be sure to include the .zip extension to the file name. If you browse for the export file, the wizard automatically adds this file name extension.
    - If you don't want to export task sequence dependencies, deselect the option to **Export all task sequence dependencies**. By default, the wizard scans for all the related objects and exports them with the task sequence. These dependencies include any for applications and child task sequences.
    - If you don't want to copy the content from the package source to the export location, deselect the option to **Export all content for the selected task sequences and dependencies**. If you select this option, the Import Task Sequence Wizard uses the import path as the new package source location.
    - **Administrator comments**: Add a description of the task sequences to export.
5. Complete the wizard.

The wizard creates the following output files:

- If you don't export content: a .zip file.
- If you export content: a .zip file and a folder named *export*\_files, where *export* is the name of the .zip file that contains the exported content.

If you include content when you export a task sequence, make sure that you copy the .zip file and the *export*\_files folder, or the import fails.

Note

If you have a multi-site hierarchy, the export of task sequences should be done from the central administration site because the primary site may not have the required permissions to all the artifacts.

## Import

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select the **Task Sequences** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Import Task Sequence**. This action starts the Import Task Sequence Wizard.
3. On the **General** page of the ribbon, specify the exported .zip file.
4. On the **File Content** page, select the action that you require for each object that you import. This page shows all the objects that Configuration Manager found to import.

    - If the object has never been imported, select **Create New**.
    - If the object has been previously imported, select one of the following actions:

        - **Ignore Duplicate** (default): This action doesn't import the object. Instead, the wizard links the existing object to the task sequence.
        - **Overwrite**: This action overwrites the existing object with the imported object. For applications, you can add a revision to update the existing application or create a new application.
5. Complete the wizard.

After you import the task sequence, edit the task sequence to specify any passwords that were in the original task sequence. For security reasons, passwords aren't exported.

Tip

When you import an object in the Configuration Manager console, it imports to the current folder. In earlier versions of Configuration Manager, it always put imported objects in the root node.