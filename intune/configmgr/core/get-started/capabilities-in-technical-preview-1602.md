---
layout: Conceptual
title: Capabilities in Technical Preview 1602 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1602
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
description: Learn about features available in the Technical Preview for Configuration Manager, version 1602.
ms.date: 2017-01-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 6ffacd8f-7a7e-9956-ac8e-4fed72ebada0
document_version_independent_id: 2ef9c190-9b2f-9893-54f5-0740da5e973e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1602.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1602
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1602.md
platformId: 356e9039-4dcd-fe17-b441-63f9c0841a6c
---

# Capabilities in Technical Preview 1602 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the Technical Preview for Configuration Manager, version 1602. You can install this version to update and add new capabilities to your Configuration Manager technical preview site. Before installing this version of the technical preview, review the introductory topic, [Technical Preview for Configuration Manager](technical-preview), to become familiar with general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback about the features in a technical preview.

The following are new features you can try out with this version.

## Improvements to mobile device management

### iOS Activation Lock

Configuration Manager can help you manage iOS Activation Lock, a feature of the Find My iPhone app for iOS 7.1 and later devices. Activation Lock is enabled automatically when the Find My iPhone app is used on a device. After it is enabled, the user's Apple ID and password must be entered before anyone can:

- Turn off Find My iPhone
- Erase the device
- Reactivate the device

    Configuration Manager can request the Activation Lock status of both supervised and unsupervised devices that run iOS 7.1 and later. For supervised devices, Intune can retrieve the Activation Lock bypass code and directly issue it to the device.

## Improvements to Software Center in version 1602

### Refresh PC machine and user policy from Software Center

A new option, **Sync Policy** has been added to the **Options** &gt; **Computer Maintenance** page of Software Center that causes the PC to refresh it's Configuration Manager machine and user policy.

## Improvements to Windows 10 Servicing

In the 1602 Technical Preview we have added the following improvements for Windows 10 Servicing:

- New filter options for Servicing Plans. You can now filter for **Language**, **Required**, and **Title**. Only upgrades that meet the specified criteria will be added to the associated deployment.
- When you select the **Upgrades** classification for software updates synchronization, a warning dialog is displayed to let you know that WSUS [hotfix 3095113](https://support.microsoft.com/kb/3095113) is required to successfully synchronize software updates and for the Windows 10 Servicing to work properly. From the dialog, you can go to the knowledge base article for the hotfix.
- Available Windows 10 upgrades now only display in the **Windows 10 Servicing** \ **All Windows 10 Updates** node of the Configuration Manager console. These updates no longer display in the **Software Updates** \ **All Software Updates** node.
- End-users that start a Windows 10 Upgrade package will be prompted with a dialog that lets them know they will be upgrading their operating system.