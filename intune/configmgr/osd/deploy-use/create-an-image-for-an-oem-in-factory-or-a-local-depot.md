---
layout: Conceptual
title: Create an image for an OEM in factory or a local depot - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot
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
description: Use prestaged media deployments to reduce network traffic while you deploy an OS to a computer that isn't fully provisioned.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: dfbdb806-9297-ed5f-cccd-21287eb253de
document_version_independent_id: 51ecf20d-b83d-b24d-f46b-bb9cc5c8ac2f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b218d11f-920f-3bd8-bb53-70566661b4d0
---

# Create an image for an OEM in factory or a local depot - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Prestaged media deployments in Configuration Manager let you deploy an OS to a computer that isn't fully provisioned. The prestaged media is a Windows image (WIM) file. The manufacturer (OEM) can install it on a bare-metal computer, or you can use it in a staging center that's separate from your production environment.

This method of deployment can reduce network traffic because the boot image and OS image are already on the destination computer. You can specify applications, packages, and driver packages to also include in the prestaged media. After it installs the OS on the computer, the task sequence first checks the prestaged cache for applications, packages, or driver packages. If it can't find the necessary content, or there is a newer revision available online, the task sequence downloads the content from a distribution point.

Use prestaged media in the following OS deployment scenarios:

- [Install a new version of Windows on a new computer (bare metal)](install-new-windows-version-new-computer-bare-metal)
- [Replace an existing computer and transfer settings](replace-an-existing-computer-and-transfer-settings)

Complete the steps in one of these OS deployment scenarios. Then use the following sections to prepare for and create the prestaged media.

## Configure deployment settings

On the **Deployment Settings** page of the deployment, for the **Make available to the following** setting, select one of the following options:

- Configuration Manager clients, media, and PXE
- Only media and PXE
- Only media and PXE (hidden)

## Create the prestaged media

Create the prestaged media file to send to the OEM or your local depot. For more information, see [Create prestaged media with Configuration Manager](create-prestaged-media).

## Send the prestaged media file

Send the media to the OEM or your local depot to prestage on the computers. They apply the image file to a formatted hard disk on the computer.

## Deliver the computer

When you deliver the computer to a user, and turn it on for the first time:

1. The computer starts with the prestaged boot image.
2. It checks a hash on the prestaged media to make sure it's valid.
3. The computer connects to the management point for available task sequences to complete the process.