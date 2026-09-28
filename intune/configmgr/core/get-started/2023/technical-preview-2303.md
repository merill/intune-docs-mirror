---
layout: Conceptual
title: Technical preview 2303 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2303
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2303.
ms.date: 2023-03-17T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: cea55c5d-1640-4f2b-8135-2d61ad0a7669
document_version_independent_id: cea55c5d-1640-4f2b-8135-2d61ad0a7669
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2303.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2303
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2303.md
platformId: 43a79a76-e17e-4f5a-a13a-0378ccf79696
---

# Technical preview 2303 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2303. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## SQL Server 2022 version support added for Configuration Manager

Starting with technical preview 2303, support is added for SQL server 2022 RTM version.

You can use this version of SQL Server for the following sites:

- A central administration site
- A primary site
- A secondary site

The following table identifies the recommended compatibility levels for Configuration Manager site databases:

| SQL Server version | Supported compatibility levels | Recommended level |
| --- | --- | --- |
| SQL Server 2022 | 150, 140, 130, 120, 110 | 150 |

## Dark theme extended to one customer voice (OCV) wizard

The Configuration Manager console now extends the dark theme for the one customer voice (OCV) wizards. All 'Send a smile' and 'Send a frown' wizards will adhere to dark theme starting in Technical Preview 2303. This is part of the ongoing effort to make dark theme and overall admin console experience better.

![Screenshot of dark theme for the one customer voice wizard.](media/17433655-console-dark-theme.png)

To use the theme, select the arrow from the top left of the ribbon, then choose **Switch console theme**. Select **Switch console theme** again to return to the light theme.

### Known issue

Console restart is required on doing the theme switch, as the node navigation pane might not properly render when you move to a new workspace.

## Prerequisites for the site server roles now include ODBC driver for SQL Server

Starting with technical preview 2303, Configuration Manager requires the installation of the ODBC driver for SQL server as a prerequisite. This prerequisite is required when you create a new site or update an existing one.

Configuration Manager doesn't manage the updates for the ODBC driver. Ensure that this component is up to date.