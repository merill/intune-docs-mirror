---
layout: Conceptual
title: Introduction to operating system deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/introduction-to-operating-system-deployment
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
description: Understand the concepts before you deploy operating systems in your Configuration Manager environment.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 9e87d002-401a-b632-51ee-dd067a5c6f05
document_version_independent_id: cb438dbd-7bfb-5e9a-222f-108481b080ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/understand/introduction-to-operating-system-deployment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/understand/introduction-to-operating-system-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/understand/introduction-to-operating-system-deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2010fbb9-6c8c-4149-924f-3ad9d014e389
---

# Introduction to operating system deployment - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use Configuration Manager to deploy operating systems in many ways. Use the information in this section to understand how to deploy operating systems and automate tasks.

## The operating system deployment process

Configuration Manager provides several methods that you can use to deploy an operating system. There are several actions that you must take regardless of the deployment method that you use:

- Identify Windows device drivers that are required to start the boot image or install the operating system image that you have to deploy.
- Identify the boot image that you want to use to start the destination computer.
- Use a task sequence to capture an image of the operating system that you'll deploy. Alternatively, you can use a default operating system image.
- Distribute the boot image, operating system image, and any related content to a distribution point.
- Create a task sequence with the steps to deploy the boot image and the operating system image.
- Deploy the task sequence to a collection of computers.
- Monitor the deployment.

## Operating system deployment scenarios

There are many operating system deployment scenarios in Configuration Manager that you can choose from depending on your environment and the purpose for the operating system installation. For example, you can partition and format an existing computer with a new version of Windows or upgrade Windows to the latest version. To help you determine the deployment method that meets your needs, review [Scenarios to deploy enterprise operating systems](../deploy-use/scenarios-to-deploy-enterprise-operating-systems). You can choose from the following operating system deployment scenarios:

- [Upgrade Windows to the latest version](../deploy-use/upgrade-windows-to-the-latest-version)
- [Refresh an existing computer with a new version of Windows](../deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)
- [Install a new version of Windows on a new computer (bare metal)](../deploy-use/install-new-windows-version-new-computer-bare-metal)
- [Replace an existing computer and transfer settings](../deploy-use/replace-an-existing-computer-and-transfer-settings)

## Methods to deploy operating systems

There are several methods that you can use to deploy operating systems to Configuration Manager client computers.

- **PXE initiated deployments**: PXE-initiated deployments let client computers request a deployment over the network. In this method of deployment, the operating system image and a Windows PE boot image are sent to a distribution point that is configured to accept PXE boot requests. For more information, see [Use PXE to deploy Windows over the network with Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network).
- **Make operating systems available in Software Center**: You can deploy an operating system and make it available in the Software Center. Configuration Manager clients can initiate the operating system installation from Software Center. For more information, see [Replace an existing computer and transfer settings](../deploy-use/replace-an-existing-computer-and-transfer-settings).
- **Multicast deployments**: Multicast deployments conserve network bandwidth by concurrently sending data to multiple clients instead of sending a copy of the data to each client over a separate connection. In this method of deployment, the operating system image is sent to a distribution point. This in turn deploys the image when client computers request the deployment. For more information, see [Use multicast to deploy Windows over the network](../deploy-use/use-multicast-to-deploy-windows-over-the-network).
- **Bootable media deployments**: Bootable media deployments let you deploy the operating system when the destination computer starts. When the destination computer starts, it retrieves the task sequence, the operating system image, and any other required content from the network. Because that content isn't included on the media, you can update the content without having to re-create the media. For more information, see [Create bootable media](../deploy-use/create-bootable-media).
- **Stand-alone media deployments**: Stand-alone media deployments let you deploy operating systems in the following conditions:

    - In environments where it isn't practical to copy an operating system image or other large packages over the network.
    - In environments without network connectivity or low bandwidth network connectivity.

        For more information, see [Create stand-alone media](../deploy-use/create-stand-alone-media).
- **Pre-staged media deployments**: Pre-staged media deployments let you deploy an operating system to a computer that isn't fully provisioned. The pre-staged media is a Windows Imaging Format (WIM) file that can be installed on a bare-metal computer by the manufacturer or at an enterprise staging center that isn't connected to the Configuration Manager environment.

    Later in the Configuration Manager environment, the computer starts by using the boot image provided by the media, and then connects to the site management point for available task sequences that complete the download process. This method of deployment can reduce network traffic because the boot image and operating system image are already on the destination computer. You can specify applications, packages, and driver packages to include in the pre-staged media. For more information, see [Create prestaged media](../deploy-use/create-prestaged-media).

## Boot images

A boot image in Configuration Manager is a Windows PE (WinPE) image that is used during an operating system deployment. Boot images are used to start a computer in WinPE, which is a minimal operating system with limited components and services that prepare the destination computer for Windows installation. Configuration Manager provides two boot images: One to support x86 platforms and one to support x64 platforms. These are considered default boot images. Boot images that you create and add to Configuration Manager are considered custom images. Default boot images can be automatically replaced when you update Configuration Manager. For more information about boot images, see [Manage boot images](../get-started/manage-boot-images).

## Operating system images

Operating system images in Configuration Manager are stored in the Windows Imaging (WIM) file format and represent a compressed collection of reference files and folders that are required to successfully install and configure an operating system on a computer. For all operating system deployment scenarios, you must select an operating system image. You can use the default operating system image or build the operating system image from a reference computer that you configure. For more information, see [Manage operating system images](../get-started/manage-operating-system-images).

## Operating system upgrade packages

Operating system upgrade packages are used to upgrade an operating system and are setup-initiated operating system deployments. You import operating system upgrade packages to Configuration Manager from a DVD or mounted ISO file. For more information, see [Manage operating system upgrade packages](../get-started/manage-operating-system-upgrade-packages).

## Media to deploy operating systems

You can create several kinds of media that can be used to deploy operating systems. This includes capture media that is used to capture operating system images and stand-alone, pre-staged, and bootable media that is used to deploy an operating system. By using media, you can deploy operating systems on computers that do not have a network connection or that have a low bandwidth connection to your Configuration Manager site. For more information about how to use media, see [Create task sequence media](../deploy-use/create-task-sequence-media).

## Device drivers

You can install device drivers on destination computers without including them in the operating system image that is being deployed. Configuration Manager provides a driver catalog that contains references to all the device drivers that you import into Configuration Manager. The driver catalog is located in the **Software Library** workspace and consists of two nodes: **Drivers** and **Driver Packages**. The **Drivers** node lists all the drivers that you have imported into the driver catalog. You can use this node to discover the details about each imported driver, to change what driver package or boot image a driver belongs to, to enable or disable a driver, and more. For more information, see [Manage drivers](../get-started/manage-drivers).

## Save and restore user state

When you deploy operating systems, you can save the user state from the destination computer, deploy the operating system, and then restore the user state after the operating systems is deployed. This process is typically used when you install the operating system on a Configuration Manager client computer.

The user state information is captured and restored by using task sequences. When the user state information is captured, the information can be stored in one of the following ways:

- You can store the user state data remotely by configuring a state migration point. The Capture task sequence sends the data to the state migration point. Then, after the operating system is deployed, the Restore task sequence retrieves the data and restores the user state on the destination computer.
- You can store the user state data locally to a specific location. In this scenario, the Capture task sequence copies the user data to a specific location on the destination computer. Then, after the operating system is deployed, the Restore task sequence retrieves the user data from that location.
- You can specify hard links that can be used to restore the user data to its original location. In this scenario, the user state data remains on the drive when the old operating system is removed. Then, after the operating system is deployed, the Restore task sequence uses the hard links to restore the user state data to its original location.

    For more information [Manage user state](../get-started/manage-user-state).

## Deploy to unknown computers

You can deploy an operating system to computers that aren't managed by Configuration Manager. There's no record of these computers in the Configuration Manager database. These computers are referred to as unknown computers. Unknown computers include the following:

- A computer where the Configuration Manager client isn't installed
- A computer that isn't imported into Configuration Manager
- A computer that isn't discovered by Configuration Manager

    For more information, see [Prepare for unknown computer deployments](../get-started/prepare-for-unknown-computer-deployments).

## Associate users with a computer

When you deploy an operating system, you can associate users with the destination computer to support user device affinity actions. When you associate a user with the destination computer, the administrative user can later perform actions on whichever computer is associated with that user, such as deploying an application to the computer of a specific user. However, when you deploy an operating system, you can't deploy the operating system to the computer of a specific user. For more information, see [Associate users with a destination computer](../get-started/associate-users-with-a-destination-computer).

## Use task sequences to automate steps

You can create task sequences to perform various tasks within your Configuration Manager environment. The actions of the task sequence are defined in the individual steps of the sequence. When the task sequence is run, the actions of each step are performed at the command-line level without requiring user intervention. You can use task sequences for the following:

- [Create a task sequence to install an operating system](../deploy-use/create-a-task-sequence-to-install-an-operating-system)
- [Create a task sequence for non-operating system deployments](../deploy-use/create-a-task-sequence-for-non-operating-system-deployments)
- [Create a task sequence to capture an operating system](../deploy-use/create-a-task-sequence-to-capture-an-operating-system)
- [Create a task sequence to capture and restore user state](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state)
- [Create a custom task sequence](../deploy-use/create-a-custom-task-sequence)