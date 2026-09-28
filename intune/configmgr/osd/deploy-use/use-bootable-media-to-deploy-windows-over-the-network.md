---
layout: Conceptual
title: Use bootable media to deploy Windows over the network - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network
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
description: Use bootable media deployments in Configuration Manager to deploy the OS when the destination computer starts.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 59e10b01-4aca-a2a8-fe75-7e1d235d217f
document_version_independent_id: 9d7de35a-cc07-2a88-e77e-e26b10d63073
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2ff08e75-4758-8522-325e-a3335b8b19b8
---

# Use bootable media to deploy Windows over the network - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Bootable media only includes the boot image and a pointer to the task sequence. It downloads the OS image and other referenced content from the network. Since the bootable media doesn't contain much content, you can update the task sequence and most content without having to replace the media.

Deploy operating systems over the network with boot media in the following scenarios:

- [Refresh an existing computer with a new version of Windows](refresh-an-existing-computer-with-a-new-version-of-windows)
- [Install a new version of Windows on a new computer (bare metal)](install-new-windows-version-new-computer-bare-metal)
- [Replace an existing computer and transfer settings](replace-an-existing-computer-and-transfer-settings)

Complete the steps in one of the OS deployment scenarios and then use the following sections to use bootable media to deploy the OS.

## Configure deployment settings

When you use bootable media to start the OS deployment process, configure the task sequence deployment to make the OS available to the media. Set this option on the **Deployment Settings** page of the deployment. For the **Make available to the following** setting, select one of the following options:

- Configuration Manager clients, media, and PXE
- Only media and PXE
- Only media and PXE (hidden)

For more information, see [Deploy a task sequence](deploy-a-task-sequence).

## Create the bootable media

When you create bootable media, specify whether it's a USB flash drive or CD/DVD set. The computer that starts the media must support the option that you choose as a bootable drive. For more information, see [Create bootable media](create-bootable-media).

## Install the OS from bootable media

To install the OS, insert the bootable media, and then power on the computer.

## Support for cloud-based content

Starting in version 2006, bootable media can download cloud-based content. For example, you send a USB key to a user at a remote office to reimage their device. Or an office that has a local PXE server, but you want devices to prioritize cloud services as much as possible. Instead of further taxing the WAN to download large OS deployment content, boot media and PXE deployments can now get content from cloud-based sources.

For more information, see [Bootable media support for cloud-based content](deploy-task-sequence-over-internet#bootable-media-support-for-cloud-based-content).