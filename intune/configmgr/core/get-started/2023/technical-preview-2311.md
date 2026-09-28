---
layout: Conceptual
title: Technical preview 2311 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2311
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2311.
ms.date: 2023-11-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: c925ac8f-1247-fe2b-ce65-c9e5be05f774
document_version_independent_id: c925ac8f-1247-fe2b-ce65-c9e5be05f774
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2311.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2311
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2311.md
platformId: 3d0f2c3a-c359-091d-3164-f877e484f53d
---

# Technical preview 2311 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2311. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Folder support for Scripts node in Software Library

You can now organize scripts by using folders. This change allows for better categorization and management of scripts. Full Administrator and Operations Administrator roles can manage the folders.

![Screenshot of scripts folder structure in console.](media/24475159-folder-scripts.png)

## New parameter SoftwareUpdateO365Language is added to Save-CMSoftwareUpdate cmdlet

A new parameter **SoftwareUpdateO365Language** is now added to PowerShell Save-CMSoftwareUpdate cmdlet. Customers now don't have to check a specific language in the SUP Properties (causing a metadata download for that language for all updates).

PowerShell Commandlet: `Save-CMSoftwareUpdate – SoftwareUpdateO365Language <language name> (<region name>)"`

Note

Languages need to be in O365 format to be consistent with Admin Console UI. E.g. "Hungarian (Hungary)".

## Support for ARM64 Operating System Deployment

Configuration Manager operating system deployment support is now added on Windows 11 ARM64 devices. Currently Importing and customizing Arm64 boot images, Wipe and load Task Sequence, Media creation Task sequence and WDS PXE for Arm64 is supported.

## Resource access profiles and deployments will block Configuration manager upgrade

Any configured Resource access profiles and associated deployments will block the Configuration manager upgrade. Please consider deleting them and moving the co-management workload for Resource Access (if co-managed) to Intune.

## WildCard Support added in Defender Exploit Guard policy for Controlled Folders

Defender Exploit Guards policy for Controlled Folder now accepts Regex in the file path for apps.

E.g. [C:\Folder\Subfolder\app?.exe] [C:\Folder1\Sub\*Name]