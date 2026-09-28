---
layout: Conceptual
title: Education Windows device enrollment with provisioning packages - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-package
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn about how to enroll Windows devices with provisioning packages using SUSPCs and Windows Configuration Designer.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: b51f91b4-096e-7974-59bd-762a18998bf1
document_version_independent_id: b51f91b4-096e-7974-59bd-762a18998bf1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/enroll-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/enroll-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/enroll-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f45bfbe3-da7c-af24-7b8f-37515b1be285
---

# Education Windows device enrollment with provisioning packages - Microsoft Intune | Microsoft Learn

Enrolling devices with provisioning packages is an efficient way to deploy a large number of Windows devices. Some of the benefits of provisioning packages are:

- There are no particular hardware dependencies on the devices to complete the enrollment process.
- Devices don't need to be registered in advance.
- Enrollment is a simple task: just open a provisioning package and the process is automated.

You can create provisioning packages using either **Windows Configuration Designer** or **Set Up School PCs** applications, which are described in the following sections.

Important

To create a bulk enrollment token, which is used to join Entra, you must have a supported Microsoft Entra role assignment. For more information, see [Requirements](../../../device-enrollment/windows/create-bulk-package#requirements).

## Windows Configuration Designer

Windows Configuration Designer is especially useful in scenarios where a school needs to provision packages for both bring-you-own devices and school-owned devices. Windows Configuration Designer allows granular customizations, including the possibility to embed scripts in the package.

![Set up device page in Windows Configuration Designer](media/enroll-package/wcd.png)

For more information, see [Install Windows Configuration Designer](/en-us/windows/configuration/provisioning-packages/provisioning-install-icd), which provides details about the app, its provisioning process, and considerations for its use.

## Set up School PCs

With Set up School PCs, you can create a package containing the most common device configurations that students need, and enroll devices in Intune. The package is saved on a USB stick, which can then be plugged into devices during OOBE. Applications and settings are automatically applied to the devices, including the Microsoft Entra join and Intune enrollment process.

### Create a provisioning package

The Set Up School PCs app guides you through configuration choices for school-owned devices.

![Configure device settings in Set Up School PCs app](media/enroll-package/supcs-win11se.png)

Caution

If you are creating a provisioning package for **Windows 11 SE** devices, ensure to select the correct *OS version* in the *Configure device settings* page.

Set Up School PCs configures many settings, allowing you to optimize devices for shared use and other scenarios.

For more information on prerequisites, configuration, and recommendations, see [Use the Set Up School PCs app](/en-us/education/windows/use-set-up-school-pcs-app).

## Enroll devices with the provisioning package

To provision Windows devices with provisioning packages, insert the USB stick containing the package during the out-of-box experience. The devices read the content of the package, join Microsoft Entra ID and automatically enroll in Intune.

All settings defined in the package and in Intune are applied to the device, and the device is ready to use.

Note

After the device arrives at the logon screen Intune will continue to apply poicies and install applications in the background.

![Windows 11 OOBE - enrollment with provisioning package animation.](media/enroll-package/win11-oobe-ppkg.gif)