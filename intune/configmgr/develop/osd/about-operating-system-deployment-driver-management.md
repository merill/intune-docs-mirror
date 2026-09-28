---
layout: Conceptual
title: OS Deployment Driver Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management
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
description: In Configuration Manager, the driver catalog helps manage the cost and complexity of deploying an operating system in an environment that contains different types of computers and devices.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: bec78ca1-db8b-b480-d0a8-45eacfc50239
document_version_independent_id: 7167681c-275b-8eb0-7c53-c2e95de2ea47
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-operating-system-deployment-driver-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-operating-system-deployment-driver-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13fa216e-5ce7-17da-b647-b358e17addf8
---

# OS Deployment Driver Management - Configuration Manager | Microsoft Learn

In Configuration Manager, the driver catalog helps manage the cost and complexity of deploying an operating system in an environment that contains different types of computers and devices. By storing device drivers in the driver catalog and not with each individual operating system image, the number of operating system images that is needed is greatly reduced. For more information about the driver catalog, see [Manage drivers](../../osd/get-started/manage-drivers).

Note

Before a driver can be used, it must be added to a driver package. For more information, see [How to Create a Driver Package for a Windows Driver in Configuration Manager](how-to-create-a-driver-package-for-a-windows-driver).

## Driver Catalog Management

With the Configuration Manager Operating System Deployment server Windows Management Instrumentation (WMI) classes you can manage the following:

- Driver import
- Driver packages
- Boot images
- Supported platforms

### Driver Import

Using the [SMS_Driver](../reference/osd/sms_driver-server-wmi-class) import methods, you can import the Windows drivers described by .inf and Txtsetup.oem files into the driver catalog. For more information, see [How to Import a Windows Driver Described by an INF File into Configuration Manager](how-to-import-a-windows-driver-described-by-an-inf-file) and [How to Import a Windows Driver Described by an OEM File into Configuration Manager](how-to-import-a-windows-driver-described-by-a-txtsetup-oem-file).

Before a driver can be used, it must be enabled. For more information, see [How to Enable or Disable a Windows Driver in Configuration Manager](how-to-enable-or-disable-a-windows-driver).

### Driver Packages

Driver packages contain one or more Windows drivers. A driver package is an `SMS_DriverPackage` object and is distributed in the same way as an `SMS_Package` package. They both derive from [SMS_PackageBaseClass](../reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

For more information about creating a driver package, see [How to Create a Driver Package for a Windows Driver in Configuration Manager](how-to-create-a-driver-package-for-a-windows-driver).

### Boot Images

Windows device drivers that have been imported into the driver catalog can be added to one or more boot images. Boot images are stored in [SMS_BootImagePackage](../reference/osd/sms_bootimagepackage-server-wmi-class) objects. In an `SMS_BootImagePackage` object, Windows drivers are kept in an array of referenced drivers. For more information, see [How to add a Windows Driver to a Configuration Manager Boot Image Package](how-to-add-a-windows-driver-to-a-configuration-manager-boot-image-package)

### Supported Platforms

Windows drivers can be configured to support specific platforms. The supported platforms are stored in the driver package XML. For more information, see [How to Specify The Supported Platforms for a Driver](how-to-specify-the-supported-platforms-for-a-driver).

### Driver Categories

You can associate categories with Windows device drivers. For more information, see [How to Add a Category to a Windows Driver](how-to-add-a-category-to-a-windows-driver)