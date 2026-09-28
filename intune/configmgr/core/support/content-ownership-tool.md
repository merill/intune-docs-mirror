---
layout: Conceptual
title: Content Ownership Tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/content-ownership-tool
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
description: Use the Content Ownership Tool to change ownership of orphaned packages in Configuration Manager.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c6d02e07-a254-893d-1a70-d784be1a9d7b
document_version_independent_id: 21de4033-2604-e048-5199-69fa5b128ec0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/content-ownership-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/content-ownership-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/content-ownership-tool.md
cmProducts: []
platformId: 84f33ac9-d243-1621-529c-65bebc0a8241
---

# Content Ownership Tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Content Ownership Tool is one of the [Configuration Manager tools](tools). It changes ownership of orphaned packages in Configuration Manager. Orphaned packages don't have an owning site server. Packages can become orphaned by removing the site server while they're still owned by this site server.

Run the Content Ownership Tool on any site server in the Configuration Manager hierarchy. Sign in as an administrative user with sufficient package permissions.

Tip

Use **ContentLibraryCleanup.exe** in `CD.Latest\SMSSETUP\TOOLS\ContentLibraryCleanup` to *remove* orphaned content from a distribution point. For more information, see [Content library cleanup tool](../plan-design/hierarchy/content-library-cleanup-tool).

## Features

- Display all orphaned packages
- Display all packages, even if they're not orphaned
- View the status of the connection to a site
- Filter packages by name, site code, or package type
- Sort by any displayed column
- Change assignment of one or more packages with a single action
- View progress of the ownership transfer activity

## Usage

Run **ContentOwnershipTool.exe** to start the tool. Local administrator permissions on the computer aren't required to run the tool.

There are no command-line parameters.

Important

This tool changes the ownership of an orphaned package. The package itself doesn't move from the distribution point that it's stored on. This ownership change doesn't cause the package to update on distribution points. It also doesn't cause clients to reevaluate policy for deployment of the package. After the ownership changes, make sure that the new site server can access the source files. It should have at least **Read** permissions to the source files of each package.