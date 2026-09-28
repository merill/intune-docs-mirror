---
layout: Conceptual
title: Technical preview 2209 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2209
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2209.
ms.date: 2022-09-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 941e8ece-567b-8a34-cdb0-6d45abe8c440
document_version_independent_id: 941e8ece-567b-8a34-cdb0-6d45abe8c440
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2209.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2209
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2209.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 0fa53080-f2d5-cc20-d19e-1b5acc197cd3
---

# Technical preview 2209 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2209. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Improvements to the console

When performing a search on any node in the console, the hint text in the search bar will now indicate the scope of the search.

- By default, all subfolders are searched when you perform a search in any node that contains subfolders. You can narrow down the search by selecting the “Current Node” option from the search toolbar.
- If you want to expand the search to include all nodes, then select the “All Objects” button in the ribbon.

For more information, see [Console changes and tips](../../servers/manage/admin-console-tips).

## Improvements to the dark theme

Pop-ups in the Health attestation dashboard now adhere to the dark theme.

Enable this prerelease feature to experience the dark theme. For more information, see [Dark theme for the console.](../../servers/manage/admin-console#bkmk_dark)

## Other updates

The software center logo dimension details are now added as a hint in the software center customization wizard.

- The image file can't be larger than 2 MB size. The maximum dimension of the image should be 400 Pixels wide and 100 pixels tall.

For more information, see [Software Center settings](../../clients/deploy/about-client-settings#software-center-settings).