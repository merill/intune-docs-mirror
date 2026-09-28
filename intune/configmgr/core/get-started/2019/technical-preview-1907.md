---
layout: Conceptual
title: Technical preview 1907 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1907
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1907.
ms.date: 2019-07-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: d0b5ebe6-4270-61a3-cbfa-0479b717bbe6
document_version_independent_id: 8b8989ca-bfea-9700-41dc-ce0bb2468962
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1907.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1907
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1907.md
platformId: 3ae66543-5a1c-2464-0ec9-3f178590234d
---

# Technical preview 1907 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1907. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Search the task sequence editor

If you have a large task sequence with many groups and steps, it can be difficult to find specific steps. Based on your feedback, you can now search in the task sequence editor. This action lets you more quickly locate steps in the task sequence.

![Searching in the task sequence editor](media/4621085-task-sequence-search.png)

Search using the following criteria:

- Step name
- Step type
- Step description
- Group name
- Variable name
- Conditions
- Other content, for example, strings like variable values or command lines

You can also filter for all steps with the following attributes:

- Continue on error
- Has conditions

When you search, the editor window highlights in yellow the steps that match your search criteria.

You can quickly access these search fields and navigate the search results with the following keyboard shortcuts:

- **CTRL** + **F**: enter a search string
- **CTRL** + **O**: select the search options to scope the results
- **F3** or **Enter**: step forward through the results
- **SHIFT** + **F3**: step backwards through the results

## Improvements to Office 365 ProPlus upgrade readiness dashboard

We've made improvements to the **Office 365 ProPlus upgrade readiness** dashboard that released in [Technical Preview version 1904](technical-preview-1904#bkmk_o365). The following new tiles on this dashboard help you evaluate readiness:

- Deployment
- Macro advisories
- Top add-ins by count of version

In the Configuration Manager console, go to the **Software Library** workspace, expand **Office 365 Client Management**, and select the **Office 365 ProPlus Upgrade Readiness** node.

![Office 365 ProPlus upgrade readiness dashboard](media/4021125-office-365-upgrade-readiness-dashboard.png)

![Office 365 ProPlus upgrade readiness dashboard - add-ins](media/4021125-office-365-to-add-ins.png)

![Office 365 ProPlus upgrade readiness dashboard - macro advisories](media/4021125-office-365-macro-advisories.png)

For more information on prerequisites and using this data, see [Integration for Microsoft 365 Apps readiness](/en-us/sccm/sum/deploy-use/office-365-dashboard#bkmk_o365_readiness).