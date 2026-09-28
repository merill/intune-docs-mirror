---
layout: Conceptual
title: Content Library Transfer tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/content-library-transfer
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
description: Use the Content Library Transfer tool to transfer content from one disk drive to another on a Configuration Manager distribution point.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c0aa1294-38fc-8525-90ec-8c45d519677d
document_version_independent_id: 42905d19-58ff-a20f-cf99-32167fdc4036
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/content-library-transfer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/content-library-transfer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/content-library-transfer.md
cmProducts: []
platformId: 4b9fe88f-4881-62eb-fab1-e02f7ef64956
---

# Content Library Transfer tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Content Library Transfer tool is one of the [Configuration Manager tools](tools). It transfers content from one disk drive to another. The tool is designed to run on distribution point site systems. It supports distribution points colocated with a site or remote site systems.

The tool is useful for the scenario when the disk drive hosting the content library becomes full. First add or identify another hard disk with sufficient space to host the content library. Then use **ContentLibraryTransfer.exe** to transfer content from the old filled hard disk to the new, empty drive.

Once the transfer is complete, content is accessible to client computers from the new location.

## Usage

Run **ContentLibraryTransfer.exe** as a user with administrative permissions on the distribution point.

#### Syntax

`ContentLibraryTransfer.exe –SourceDrive <drive letter of source drive> –TargetDrive <drive letter of destination drive>`

#### Example

`ContentLibraryTransfer –SourceDrive E –TargetDrive G`

## Limitations

- Run the tool locally on the distribution point. You can't run it from a remote computer.
- Only use it when clients aren't actively accessing the distribution point. If you run the tool while clients are accessing content, the content library on the destination drive may have incomplete data. The data transfer might fail altogether leading to an unusable content library.
- Don't distribute content to the distribution point when you run the tool. If you run the tool while content is being written to the distribution point, the content library on the destination drive may have incomplete data. The data transfer might fail altogether leading to an unusable content library.