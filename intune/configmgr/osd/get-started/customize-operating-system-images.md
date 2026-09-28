---
layout: Conceptual
title: Customize operating system images - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/customize-operating-system-images
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
description: Use capture-and-build task sequences, manual configuration, or a combination of both to customize an operating system image.
ms.date: 2025-07-31T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8f84aba9-b342-8008-3d05-d554a44d6091
document_version_independent_id: db8a0533-0ded-e26f-6c4d-f8d3f638dcd4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/get-started/customize-operating-system-images.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/get-started/customize-operating-system-images
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/get-started/customize-operating-system-images.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a19b04d9-4e16-d94b-7587-1b8479c9329a
---

# Customize operating system images - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Operating system images in Configuration Manager are WIM files. A WIM file represents a compressed collection of reference files and folders that are required to successfully install and configure an operating system on a computer. A custom operating system image is built and captured from a reference computer. The reference computer is configured with all the required operating system files, support files, software updates, tools, and other software apps. The extent to which you manually configure the reference computer is up to you. You can:

- Completely automate the configuration of the reference computer by using a build and capture task sequence.
- Manually configure certain aspects of the reference computer and then automate the rest by using task sequences.
- Manually configure the reference computer without using task sequences.

Use the following sections to customize an operating system.

## Prepare for the reference computer

There are several things to think about before you use capture an operating system image from a reference computer.

### Decide between an automated or manual configuration

The following outlines advantages and disadvantage for an automated and manual configuration of the reference computer.

#### Automated configuration

##### Advantages of automated configuration

- The configuration can be completely unattended, which eliminates the requirement for an administrator or user to be present.
- You can reuse the task sequence to repeat the configuration of additional reference computers with a high level of confidence.
- You can modify the task sequence to accommodate differences in reference computers without having to recreate the entire task sequence.

##### Disadvantages of automated configuration

- The initial action to build a task sequence can take a long time to create and test.
- If the reference computer requirements change significantly, it can take a long time to rebuild and retest the task sequence.

#### Manual configuration

##### Advantages of manual configuration

- You don't have to create a task sequence or take the time to test and troubleshoot the task sequence.
- You can install directly from CDs without putting all the software packages (including Windows itself) into a Configuration Manager package.

##### Disadvantages of manual configuration

- The accuracy of the reference computer configuration depends on the administrator or user who configures the computer.
- You must still verify and test that the reference computer is configured correctly.
- You can't reuse the configuration method.
- Requires a person to be actively involved throughout the process.

### Considerations for the reference computer

The following lists the basic items to consider when you configure a reference computer.

- **Operating system to deploy**

    The reference computer must be installed with the operating system that you intend to deploy to your destination computers. For more information about the operating systems that you can deploy, see [Infrastructure requirements for operating system deployment](../plan-design/infrastructure-requirements-for-operating-system-deployment).
- **Appropriate service pack**

    The reference computer must be installed with the operating system that you intend to deploy to your destination computers.
- **Appropriate software updates**

    Install all software applications that you want included in the operating system image that you capture from the reference computer. You can also install software applications when you deploy the captured operating system image to your destination computers.
- **Workgroup membership**

    The reference computer must be configured as a member of a workgroup.
- **Sysprep**

    The System Preparation (Sysprep) tool is a technology that you can use with other deployment tools to install Windows operating systems onto new hardware. Sysprep prepares a computer for disk imaging or delivery to a customer. Sysprep configures the computer to create a new computer security identifier (SID) when the computer is restarted. In addition, Sysprep cleans up user and computer-specific settings and data that must not be copied to a destination computer.

    You can manually Sysprep the reference computer by running the following command:

    `Sysprep /quiet /generalize /reboot`

    The /generalize option instructs Sysprep to remove system-specific data from the Windows installation. System-specific information includes event logs, unique security IDs (SIDs), and other unique information. After the unique system information is removed, the computer restarts.

    You can automate Sysprep by using the [Prepare Windows for Capture](../understand/task-sequence-steps#BKMK_PrepareWindowsforCapture) task sequence step or capture media.

    Important

    The [Prepare Windows for Capture](../understand/task-sequence-steps#BKMK_PrepareWindowsforCapture) task sequence step attempts to reset the local administrator password on the reference computer to a blank value before Sysprep runs. If the Local Security policy **Password must meet complexity requirements** is enabled, this task sequence step fails to reset the administrator password. In this scenario, disable this policy before you run the task sequence.

    For more information about Sysprep, see [Sysprep (System Preparation) overview](/en-us/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview).
- #### Appropriate tools and scripts required to mitigate installation scenarios

    Appropriate tools and scripts required to mitigate installation scenarios
- #### Appropriate desktop customization, such as wall paper, branding, and default user profile

    You can configure the reference computer with the desktop customization properties that you want to include when you capture the operating system image from the reference computer. Desktop properties include wallpaper, organizational branding, and a standard default user profile.

## Manually build a reference computer

Use the following procedure to manually build a reference computer.

Note

When you manually build the reference computer, you can capture the operating system image by using capture media. For more information, see [Create capture media](../deploy-use/create-capture-media).

### To manually build the reference computer

1. Identify the computer to use as the reference computer.
2. Configure the reference computer with the appropriate operating system and any other software that is required to create the operating system image that you want to deploy.

    Warning

    At a minimum, install the appropriate operating system and service pack, support drivers, and required software updates.
3. Configure the reference computer to be a member of a workgroup.
4. Reset the local Administrator password on the reference computer so that the password value is blank.
5. Run Sysprep by using the command: **sysprep /quiet /generalize /reboot**. The /generalize option instructs Sysprep to remove system-specific data from the Windows installation. System-specific information includes event logs, unique security IDs (SIDs), and other unique information. After the unique system information is removed, the computer restarts.

    After the reference computer is ready, use a task sequence to capture the operating system image from the reference computer. For detailed steps, see [Capture an operating system image from an existing reference computer](../deploy-use/create-a-task-sequence-to-capture-an-operating-system#BKMK_CaptureExistingRefComputer).

## Use a task sequence to build a reference computer

You can automate the process to create a reference computer by using a task sequence to deploy the operating system, drivers, applications, and so on. Use the following steps to build the reference computer and then to capture the operating system image from the reference computer.

- Use a task sequence to build and capture the operating system image from the reference computer. For detailed steps, see [Use a task sequence to build and capture a reference computer](../deploy-use/create-a-task-sequence-to-capture-an-operating-system#BKMK_BuildCaptureTS).