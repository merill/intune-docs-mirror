---
layout: Conceptual
title: Create task sequence media - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-task-sequence-media
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
description: Create task sequence media to deploy an OS to a destination computer in your Configuration Manager environment.
ms.date: 2023-12-14T00:00:00.0000000Z
ms.subservice: osd
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 58434540-48c9-7117-ffd7-d04f6aaa4817
document_version_independent_id: 4c338292-31cd-cbbb-b46b-f6dc3430de51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/create-task-sequence-media.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/create-task-sequence-media
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/create-task-sequence-media.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5d20d44a-dde4-058a-6c85-71838cfda06d
---

# Create task sequence media - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use media to capture an OS image from a reference computer or to deploy an OS to a destination computer in your Configuration Manager environment. The media that you create can be a CD, DVD set, or a USB flash drive.

Media is used mostly to deploy an OS on computers that don't have a network connection or that have a low-bandwidth connection to the site. However, you can also use media to start an OS deployment outside of an existing Windows OS. This method is useful when there's no OS, the OS isn't working, or you want to repartition the disk.

Deployment media includes bootable media, standalone media, and prestaged media. The content of the media varies, depending on what type of media that you use. For example, standalone media contains the task sequence that deploys the OS. Other types of media retrieve task sequences from the management point.

Important

As a security best practice, always assign a password to help protect the task sequence media. Assigning a password to the media not only prevents someone without the password from running a task sequence when using the media, but it also properly encrypts the task sequence environment on the media. The task sequence environment includes the task sequence steps and their variables.

Using a password doesn't encrypt the remaining content of the task sequence media such as packages. Don't include any sensitive information in task sequence packages such as scripts. Store and implement all sensitive information by using task sequence variables.

Important

To create task sequence media, you must be an administrator on the computer where you run the Configuration Manager console. If you're not an administrator, you're prompted for administrator credentials when you start the Create Task Sequence Media wizard.

## Capture media

Capture media allows you to capture an OS image from a reference computer. Capture media contains the boot image that starts the reference computer and the task sequence that captures the OS image.

## Bootable media

Bootable media contains the following components:

- The boot image
- Optional [prestart commands](../understand/prestart-commands-for-task-sequence-media) and their required files
- Configuration Manager binaries

When the destination computer starts, it connects to the network and retrieves the task sequence, the OS image, and any other required content from the network. Because the task sequence isn't on the media, you can change the task sequence or content without having to recreate the media.

Starting in version 2006, bootable media can download cloud-based content. The device still needs an intranet connection to the management point. It can get content from a content-enabled cloud management gateway (CMG). For more information, see [Bootable media support for cloud-based content](deploy-task-sequence-over-internet#bootable-media-support-for-cloud-based-content).

## Prestaged media

Prestaged media allows you to apply bootable media and an OS image to a hard disk before the provisioning process. The prestaged media is a Windows Image (WIM) file. The manufacturer can install it to the bare-metal computer during their build process. Or you can use it in a staging center that's not connected to the production Configuration Manager environment.

Prestaged media contains the boot image used to start the destination computer and the OS image that's applied to the destination computer. You can also specify applications, packages, and driver packages to include as part of the prestaged media. The task sequence that deploys the OS isn't included in the media. When you deploy a task sequence that uses prestaged media, the client checks the local task sequence cache for valid content first. If the content can't be found or has been revised, the client downloads the content from a distribution point or peer.

You apply prestaged media to the hard drive of a new computer before you send the computer to the user. When the computer starts for the first time after you've applied the prestaged media, the computer starts in Windows PE. It connects to a management point to locate the task sequence that completes the OS deployment process.

## Standalone media

Standalone media contains everything that's required to deploy the OS. This content includes the task sequence and any other required content. Because everything is on the media, the required disk space is larger than for other types of media.

## Considerations when using HTTPS

When you configure your management points and distribution points to use HTTPS, create boot media and prestaged media at a primary site, not the central administration site. Also, consider the following point to help you determine whether to configure the media as dynamic or site-based:

- To configure the media as dynamic media, all primary sites must have the root certificate authority (CA) of the site from which you created the media. You can import the root CA to all primary sites in your hierarchy.
- When primary sites in your Configuration Manager hierarchy use different root CAs, you must use site-based media at each site.