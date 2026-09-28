---
layout: Conceptual
title: OS Deployment Image Management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-image-management
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
description: There are several package types that Configuration Manager uses to manage reference computer operating system images.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 7229b8ce-fc8a-48e1-7184-99b108f4c7cb
document_version_independent_id: 4b15c428-a3ea-4bd2-8266-f9e6ba8d8e60
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-operating-system-deployment-image-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-operating-system-deployment-image-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-operating-system-deployment-image-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b6038dd0-1822-ce4e-9728-e8706aebdf8a
---

# OS Deployment Image Management - Configuration Manager | Microsoft Learn

There are several package types that Configuration Manager uses to manage reference computer operating system images.

For more information about operating system deployment image management, see [Manage operating system images with Configuration Manager](../../osd/get-started/manage-operating-system-images).

## Reference Computer

### Operating System Installation

The operating system installation package contains all the files necessary to install the desired Windows operating system on a reference computer. in Configuration Manager, they're managed by [SMS_OperatingSystemInstallPackage](../reference/osd/sms_operatingsysteminstallpackage-server-wmi-class). This package doesn't require a program. The task sequence references the source files as needed.

### Boot Image

An operating system deployment boot image is a Windows Pre-Installation Environment (PE) 2.0 image that is used during the operating system deployment process. In Configuration Manager, boot images are managed by [SMS_BootImagePackage](../reference/osd/sms_bootimagepackage-server-wmi-class). For more information, see [How to Add a Boot Image from a WIM File in Configuration Manager](how-to-add-a-boot-image-from-a-wim-file).

### Driver Packages

Driver packages contain Windows device drivers that aren't included with the operating system. In Configuration Manager they're managed by [SMS_DriverPackage](../reference/osd/sms_driverpackage-server-wmi-class) objects. For more information, see [How to Create a Driver Package for a Windows Driver in Configuration Manager](how-to-create-a-driver-package-for-a-windows-driver).

### Sysprep Package

Sysprep is a Windows system presentation tool that facilitates image creation and preparation of an image for deployment to multiple computers. Sysprep is supplied with Windows Vista, but if you're deploying Windows XP or an earlier operating system, you must create an [SMS_Package](../reference/core/servers/configure/sms_package-server-wmi-class) object package to contain Sysprep and its support files. For more information about creating `SMS_Package` objects, see [How to Create a Package](../core/servers/configure/how-to-create-a-package).

## Target Computer

### Operating System Image

Operating system image packages contain operating system images. In Configuration Manager, they're managed by [SMS_ImagePackage](../reference/osd/sms_imagepackage-server-wmi-class) objects. For more information, see [How to Add an Operating System Image Package in Configuration Manager](how-to-add-an-operating-system-image-package-in-configuration-manager).

### Configuration Manager 2007 Client Installation

Because every operating system deployment installs the Configuration Manager client, you need to create a package (`SMS_Package`) to install the Configuration Manager client. You can use the package definition file that is included with Configuration Manager for the Configuration Manager client upgrade. For more information about creating a package with a package definition file, see [How to Create a Package by Using a Package Definition File Template](../core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template).

### User State Migration Tool

If you're migrating user state from one desktop to another, then you should use the User State Migration Tool (USMT) as your migration tool.

In Configuration Manager, you create a package (`SMS_Package`) object to run the USMT on the computer. A package program isn't required.

### Other Packages

You'll need to create other packages (`SMS_Package`) for the applications you want installed on the target computer.

## Package Distribution

You copy the various package types to distribution points by using the same method that you would use for copying `SMS_Package` package object. For more information, see [How to Assign a Package to a Distribution Point](../core/servers/configure/how-to-assign-a-package-to-a-distribution-point).