---
layout: Conceptual
title: Technical preview 1808 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1808
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1808.
ms.date: 2018-08-17T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 1832ab60-e3bc-b385-dee8-afce8610d55d
document_version_independent_id: c018c777-bb4e-1209-30f9-6d7af772df0a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1808.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1808
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1808.md
platformId: cb8f614b-1905-46bb-4a59-8ed76a9e0129
---

# Technical preview 1808 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1808. Install this version to update and add new features to your technical preview site.

Review the [technical preview](technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Phased deployment of software updates

Create phased deployments for software updates. Phased deployments allow you to orchestrate a coordinated, sequenced rollout of software based on customizable criteria and groups.

In the Configuration Manager console, go to the **Software Library**, expand **Software Updates**, and select **All Software Updates**. Select one update, and then click **Create Phased Deployment** in the ribbon. This action is also available from the **All Windows 10 Updates** and **Office 365 Updates** nodes.

The behavior of a software update phased deployment is the same as for task sequences and applications. For more information, see [Create phased deployments](../../osd/deploy-use/create-phased-deployment-for-task-sequence).

### Known issues

- The Create Phased Deployment wizard only provides the option to **Automatically create a default two phase deployment**.
- The setting to **Gradually make the software available over this period of time (in days)** doesn't work.

## Improvement to repair applications

A new button is now available in Software Center to **Repair** an application. When you configure an application with a repair program, users can start the command from Software Center.

For more information, see [Repair applications](capabilities-in-technical-preview-1807#bkmk_app-repair).