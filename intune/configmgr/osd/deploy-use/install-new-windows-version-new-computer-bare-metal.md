---
layout: Conceptual
title: Install Windows on a new computer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal
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
description: Use Configuration Manager to install an operating system on a new computer (bare metal) by using PXE, OEM, or stand-alone media.
ms.date: 2017-01-23T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 22e9101d-5f64-c1fd-cfa3-aa8e5b63c98f
document_version_independent_id: 4a9ceff5-a7eb-c46c-7433-59ac51bfca60
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4a3100e2-5765-afe7-9564-97e8ff76122f
---

# Install Windows on a new computer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic provides the general steps in Configuration Manager to install an operating system on a new computer. For this scenario, you can choose from many different deployment methods, such as PXE, OEM, or stand-alone media. If you are unsure that this is the right operating system deployment scenario for you, see [Scenarios to deploy enterprise operating systems](scenarios-to-deploy-enterprise-operating-systems).

Use the following sections to refresh an existing computer with a new version of Windows.

## Plan

- **Plan for and implement infrastructure requirements**

    There are several infrastructure requirements that must be in place before you can deploy operating systems, such as Windows ADK, Windows Deployment Services (WDS), supported hard disk configurations, etc. For more information, see [Infrastructure requirements for operating system deployment](../plan-design/infrastructure-requirements-for-operating-system-deployment).

## Configure

1. **Prepare a boot image**

    Boot images start a computer in a Windows PE environment (a minimal operating system with limited components and services) that can then install a full Windows operating system on the computer. When you deploy operating systems, you must select a boot image to use and distribute the image to a distribution point. Use the following to prepare the boot image:

    - To learn more about boot images, see [Manage boot images](../get-started/manage-boot-images).
    - For more information about how to customize a boot image, see [Customize boot images](../get-started/customize-boot-images).
    - Distribute the boot image to distribution points. For more information, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).
2. **Prepare an operating system image**

    The operating system image contains the files necessary to install the operating system on the destination computer. Use the following to prepare the operating system image:

    - To learn more about how to create an operating system image, see [Manage operating system images](../get-started/manage-operating-system-images).
    - Distribute the operating system image to distribution points. For more information, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

    Note

    New installations of Windows can also be performed from installation source files via OS upgrade packages, but use OS images such as **install.wim** instead.

    Deploying new installations of Windows via OS upgrade packages is still supported, but is dependent on drivers being compatible with this method. When installing Windows from an OS upgrade package, drivers are installed while still in Windows PE versus simply being injected while in Windows PE. Some drivers are not compatible with being installed while in Windows PE. If drivers are not compatible with being installed while in Windows PE, then use an OS image instead.
3. **Create a task sequence to deploy operating systems over the network**

    Use a task sequence to automate the installation of the operating system over the network. Use the steps in [Create a task sequence to install an operating system](create-a-task-sequence-to-install-an-operating-system) to create the task sequence to deploy the operating system. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.

## Deploy

- Use one of the following deployment methods to deploy the operating system:

    - [Use PXE to deploy Windows over the network](use-pxe-to-deploy-windows-over-the-network)
    - [Use multicast to deploy Windows over the network](use-multicast-to-deploy-windows-over-the-network)
    - [Create an image for an OEM in factory or a local depot](create-an-image-for-an-oem-in-factory-or-a-local-depot)
    - [Use stand-alone media to deploy Windows without using the network](use-stand-alone-media-to-deploy-windows-without-using-the-network)
    - [Use bootable media to deploy Windows over the network](use-bootable-media-to-deploy-windows-over-the-network)

## Monitor

- **Monitor the task sequence deployment**

    To monitor the task sequence deployment to install the operating system, see [Monitor operating system deployments](monitor-operating-system-deployments).