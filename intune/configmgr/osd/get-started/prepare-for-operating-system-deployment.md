---
layout: Conceptual
title: Prepare for OS deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/prepare-for-operating-system-deployment
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
description: Learn about how to prepare for operating system deployments in Configuration Manager
ms.date: 2019-02-22T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 35e994e1-2875-4dd4-b500-ed5d00c6c6a7
document_version_independent_id: 2862c42f-6027-fa80-cc45-e0040a1d2779
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/get-started/prepare-for-operating-system-deployment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/get-started/prepare-for-operating-system-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/get-started/prepare-for-operating-system-deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/0811fd70-54cc-4b30-9df4-d821a6be00ca
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e026b98e-678e-4406-bc80-b3daea608acc
platformId: d4ebbbfb-5162-8f2b-1eab-d144fbbd2ffb
---

# Prepare for OS deployment - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

There are several things you must do in Configuration Manager before you can deploy operating systems. Use the following articles to prepare for OS deployment:

- [Manage boot images](manage-boot-images)
- [Manage OS images](manage-operating-system-images)
- [Manage OS upgrade packages](manage-operating-system-upgrade-packages)
- [Manage drivers](manage-drivers)
- [Manage user state](manage-user-state)
- [Prepare for unknown computer deployments](prepare-for-unknown-computer-deployments)
- [Associate users with a destination computer](associate-users-with-a-destination-computer)

### OS image size

OS images are large in size. For example, the image size for Windows 7 is 3 GB or more. The size of the image and the number of computers to which you simultaneously deploy the OS affects the network performance and available bandwidth. Make sure to test the network performance. Testing the impact better gauges the effect the image deployment might have and the time it takes to complete the deployment. Configuration Manager activities that affect network performance include distributing the image to a distribution point, distributing the image from one site to another, and downloading the image to the client.

Also make sure that you plan for sufficient disk storage space on the distribution points that host the OS images.

For more information, see [Additional planning considerations for distribution points](prepare-site-system-roles-for-operating-system-deployments#additional-planning-considerations-for-distribution-points).

### Client cache size

When Configuration Manager clients download content, they automatically use Background Intelligent Transfer Service (BITS), if it's available. When you deploy a task sequence that installs an OS, you can set an option on the deployment so that Configuration Manager clients download the full image to a local cache before the task sequence runs.

When a Configuration Manager client must download an OS image, but there isn't enough space in the cache, the client can clear space in its cache. It checks the other packages in the cache to determine whether deleting any of the oldest packages will free enough disk space to accommodate the image. If deleting packages doesn't free enough space, the client doesn't download the image, and the deployment fails. This behavior might occur if the cache has a large package that you configure to persist in the cache. If deleting packages does free enough disk space in the cache, the client deletes them, and then downloads the image into the cache.

The default cache size on Configuration Manager clients might not be large enough for most OS image deployments. If you plan to download the full image to the client cache, adjust the client cache size on the destination computers to accommodate the size of the image that you're deploying.

For more information, see [Configure the client cache](../../core/clients/manage/configure-client-cache).