---
layout: Conceptual
title: Use multicast to deploy Windows over the network - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network
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
description: Use multicast in your Configuration Manager environment so that multiple computers can simultaneously download the OS image.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bcc1ea3f-0d16-b4a0-d6c5-2f10eef8cf2b
document_version_independent_id: 4cfdd952-86b0-86a2-f26a-ad3a104999bb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c48a1338-3389-756c-c900-5f28cc1490ad
---

# Use multicast to deploy Windows over the network - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Multicast is a network optimization method that you can use when multiple clients are likely to download the same OS image at the same time. When you use multicast, multiple computers simultaneously download the OS image as it's multicast by the distribution point. This behavior is instead of each client downloading a copy of the image over a separate connection from the distribution point.

Deploy operating systems over the network by using multicast in the following OS deployment scenarios:

- [Refresh an existing computer with a new version of Windows](refresh-an-existing-computer-with-a-new-version-of-windows)
- [Install a new version of Windows on a new computer (bare metal)](install-new-windows-version-new-computer-bare-metal)

Complete the steps in one of these OS deployment scenarios. Then use the following sections to support multicast.

## Configure distribution points for multicast

To use multicast, configure at least one distribution point to support multicast. For more information, see [Install and configure distribution points](../../core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-multicast).

For a list of ports required to support multicast, see [Ports](../../core/plan-design/hierarchy/ports#BKMK_PortsClient-DP2).

## Prepare an OS image for multicast

You need to configure the OS image to support multicast. For more information, see [Prepare the OS image for multicast deployments](../get-started/manage-operating-system-images#BKMK_OSImageMulticast).

## Deploy the task sequence

Deploy the OS to a target collection. For more information, see [Deploy a task sequence](deploy-a-task-sequence).