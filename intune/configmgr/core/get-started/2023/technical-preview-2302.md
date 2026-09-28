---
layout: Conceptual
title: Technical preview 2302 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2302
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2302.
ms.date: 2023-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: d33086fc-fa7a-f3e2-8224-bb90667d0f34
document_version_independent_id: d33086fc-fa7a-f3e2-8224-bb90667d0f34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2302.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2302
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2302.md
platformId: a7bd2790-6845-5e0d-22ad-18598b5195de
---

# Technical preview 2302 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2302. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Dark theme extended to delete secondary site wizard

The Configuration Manager console now extends the dark theme for the delete secondary site wizard. This wizard will also have a new look for the normal theme. This is part of the ongoing effort to make dark theme and overall admin console experience better.

![Screenshot of dark theme for the delete secondary site wizard.](media/15942599-console-dark-theme.png)

To use the theme, select the arrow from the top left of the ribbon, then choose **Switch console theme**. Select **Switch console theme** again to return to the light theme.

### Known issue

Console restart is required on doing the theme switch, as the node navigation pane might not properly render when you move to a new workspace.

## Enable Windows features introduced via Windows servicing that are off by default

To learn more about the settings: “Enable Windows features introduced via Windows servicing that are off by default”, please read this [blog](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/commercial-control-for-continuous-innovation/ba-p/3737575). The post describes the Commercial control for continuous innovation in Windows. The setting for this policy is now integrated with the Configuration Manager 2302 Technical Preview. More information on the Commercial control timeline and versions of Windows 11 supported by the setting can be found in the blog.

The Windows features that the policy will control will be released in later part of 2023. This ConfigMgr Technical Preview feature is for awareness and not for testing in February 2023.

[![Screenshot of setting properties. It displays the behavior of software updates enable windows features settings.](media/16834520-wincom-servicing.png)](media/16834520-wincom-servicing.png#lightbox)