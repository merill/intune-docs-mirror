---
layout: Conceptual
title: Create Software Distribution Packages for Mobile Devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/mdm/how-to-create-software-distribution-packages-for-mobile-devices
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
description: How to Create Software Distribution Packages, Programs, and Advertisements for Mobile Devices
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 12053ede-95bc-9e8c-f997-febd63cc650c
document_version_independent_id: 3d0ff183-93ac-9ff8-c4ee-85d6adce2d4f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/mdm/how-to-create-software-distribution-packages-for-mobile-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/mdm/how-to-create-software-distribution-packages-for-mobile-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/mdm/how-to-create-software-distribution-packages-for-mobile-devices.md
cmProducts: []
platformId: 48bd68a9-dab3-1cc9-68ec-bb90eb878542
---

# Create Software Distribution Packages for Mobile Devices - Configuration Manager | Microsoft Learn

Configuration Manager device management enables mobile device software distribution to mobile devices. Packages, programs, and advertisements for mobile devices are much the same as those for computer clients. For detailed information about creating packages, programs and advertisements, see the following topics:

- [How to Create a Package](../core/servers/configure/how-to-create-a-package)
- [How to Create a Program](../core/servers/configure/how-to-create-a-program)
- [How to Create an Advertisement](../core/servers/configure/how-to-create-an-advertisement)

Important

This article only applies to the mobile device legacy client.

## Packages

Packages for mobile devices in Configuration Manager generally represent a software application to be installed on a mobile device, but they might also contain individual files, updates, or even an individual command.

### Configuration Packages

Configuration packages are packages specifically for mobile devices. These packages contain one or more configuration items. Configuration items are collections of settings for one or more mobile device platforms.

## Programs

Programs for mobile devices in Configuration Manager are commands that are distributed with a Configuration Manager package that tell a mobile device client what should occur when the package is received.

## Advertisements

Advertisements for mobile devices in Configuration Manager allow mobile devices to download and install available packages. Advertisements for mobile devices are much the same as advertisements for computer clients. Mobile device advertisement programs will not run on desktop computers and computer advertisement programs will not run on mobile devices. Advertisements can be created in two ways, one for each type of package that can be advertised to mobile devices. The following advertisements can be sent to mobile devices:

- Advertisements for configuration packages for mobile devices
- Advertisements for software distribution packages for mobile devices

### Advertisements for Configuration Packages

Configuration packages are packages specifically for mobile devices. These packages contain one or more configuration items. Configuration items are collections of settings for one or more mobile device platforms.

### Advertisements for Software Distribution Packages

Advertisements for mobile devices are identical to software distribution packages for computer clients except that they target mobile devices and contain content that is appropriate for mobile devices.