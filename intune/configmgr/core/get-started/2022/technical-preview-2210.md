---
layout: Conceptual
title: Technical preview 2210 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2210
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2210.
ms.date: 2022-10-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
locale: en-us
document_id: 6f9c2746-5964-afb1-6236-3e35c02ae4a0
document_version_independent_id: 6f9c2746-5964-afb1-6236-3e35c02ae4a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2210.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2210
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2210.md
cmProducts: []
platformId: cb002f68-3ed5-112e-68fb-822820112762
---

# Technical preview 2210 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2210. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Featured Apps in Software Center

We're now adding a **Featured** tab in Software Center where we'll display featured apps. With the new tab, IT admin can mark apps as "featured" and encourage end users to use these apps. Currently, this feature is available only for "User Available" apps. Also, admins can make the **Featured** tab of Software Center as default the tab from Client Settings.

If an app is marked as **Featured** and it's deployed to a User Collection as an Available app, it will show under the **Featured** pivot in Software Center.

[![Screenshot of wizard for app properties. It displays the checkbox, which needs to be selected to make apps as featured in software center.](media/3601183-featured-apps-software-center.png)](media/3601183-featured-apps-software-center.png#lightbox)

For more information, see [Software Center in Configuration Manager](../../understand/software-center).