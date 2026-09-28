---
layout: Conceptual
title: Import and export applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/import-export-applications
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
description: Learn how to import and export applications in Configuration Manager to share between separate hierarchies.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d0b78a10-f252-a74f-8114-b72e7f92d54d
document_version_independent_id: b26e2357-a7ba-fe4c-4f58-d0d45b7f5bcb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/import-export-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/import-export-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/import-export-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: bf6c73f8-ab85-28e5-3576-2f6fb6a78bbc
---

# Import and export applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use Configuration Manager to import and export applications between two hierarchies. For example, copy an application from a test environment to a production environment.

## Export

1. In the Configuration Manager console, select the **Applications** node. In the Create group of the ribbon, choose **Export Application**.
2. On the **General** screen, enter a path to a new ZIP file to export into. Optionally, specify whether to export *dependencies, supersedence relationships, conditions, and virtual environments*, and *content for the selected applications and dependencies*. Enter any necessary administrator comments, and select **Next**.
3. Verify the application and any dependencies are listed on the **Related Objects** page and select **Next**.
4. On the Summary page, select **Next**.
5. Once the process completes, it creates the ZIP file, and you can close the wizard.

Important

If you're going to copy this application to another environment, take both the ZIP file and the folder that accompanies it. The ZIP file must exist in the same directory as the created folder.

## Import

Note

You can only import applications from UNC paths, you can't directly import from your local disk.

1. In the Configuration Manager console, select the **Applications** node. In the Create group of the ribbon, choose **Import Application**.
2. Choose the ZIP file that you'd like to import and select **Next**.
3. The File Content window shows what happens when you import the application. Select **Next**.
4. Review the summary screen and select **Next**.
5. Close the wizard. The application is now available in the site.

Tip

Starting in version 2010, when you import an object in the Configuration Manager console, it now imports to the current folder. Previously, Configuration Manager always put imported objects in the root node.

## Automation

If you want to automate the import and export of applications, use the following PowerShell cmdlets:

- [Import-CMApplication](/en-us/powershell/module/configurationmanager/import-cmapplication)
- [Export-CMApplication](/en-us/powershell/module/configurationmanager/export-cmapplication)