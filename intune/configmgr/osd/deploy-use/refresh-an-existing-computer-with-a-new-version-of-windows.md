---
layout: Conceptual
title: Refresh an existing computer's OS - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows
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
description: You can use several methods in Configuration Manager to partition and format an existing computer and install a new OS on the computer.
ms.date: 2019-08-27T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 05fc457b-054e-75ae-e8fd-2e0bed1f0b6d
document_version_independent_id: 49dc04cd-3a2e-c2b6-fd7c-8d3881d21f85
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e8d0b130-c305-60c6-248c-8069b99cd4f6
---

# Refresh an existing computer's OS - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use Configuration Manager to partition and format an existing computer and then install a new OS. This process is sometimes called *reimaging* or *wipe and load*. For this scenario, choose from many different deployment methods, such as PXE, bootable media, or Software Center. You can also use a state migration point to store settings, and then restore them to the new OS.

To choose the right OS deployment scenario, see [Scenarios to deploy enterprise operating systems](scenarios-to-deploy-enterprise-operating-systems).

## Plan

### Plan for and implement infrastructure requirements

There are several infrastructure requirements that must be in place before you can deploy an OS. Some of these requirements include the Windows ADK, the User State Migration Tool (USMT), and Windows Deployment Services (WDS). For more information, see [Infrastructure requirements for OS deployment](../plan-design/infrastructure-requirements-for-operating-system-deployment).

### Install a state migration point

If you want to capture settings from an existing computer, and then restore the settings to the new OS, consider using a state migration point. For more information, see [State migration point](../get-started/prepare-site-system-roles-for-operating-system-deployments#state-migration-point).

## Configure

### Prepare a boot image

Boot images start a computer in a Windows PE environment. Windows PE is a minimal OS with limited components and services. From Windows PE, Configuration Manager can then install a full Windows OS on the computer.

For more information, see the following articles:

- [Manage boot images](../get-started/manage-boot-images)
- [Customize boot images](../get-started/customize-boot-images)
- [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### Prepare an OS image

The OS image contains the files necessary to install the OS on the destination computer.

For more information, see the following articles:

- [Manage OS images](../get-started/manage-operating-system-images)
- [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### Create a task sequence to deploy an OS

Use a task sequence to automate the installation of the OS. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.

For more information, see the following articles:

- [Create a task sequence to install an OS](create-a-task-sequence-to-install-an-operating-system)
- [Manage user state](../get-started/manage-user-state)

## Deploy

- Use one of the following deployment methods to deploy the OS:

    - [Use PXE to deploy Windows over the network](use-pxe-to-deploy-windows-over-the-network)
    - [Use multicast to deploy Windows over the network](use-multicast-to-deploy-windows-over-the-network)
    - [Create an image for an OEM in factory or a local depot](create-an-image-for-an-oem-in-factory-or-a-local-depot)
    - [Use stand-alone media to deploy Windows without using the network](use-stand-alone-media-to-deploy-windows-without-using-the-network)
    - [Use bootable media to deploy Windows over the network](use-bootable-media-to-deploy-windows-over-the-network)
    - [Use Software Center to deploy Windows over the network](use-software-center-to-deploy-windows-over-the-network)

## Monitor

For more information, see [Monitor OS deployments](monitor-operating-system-deployments).

Note

When you reimage a UEFI device, Windows Boot Manager creates a new entry in the boot loader. This behavior is most noticeable when you repeatedly reimage a device, such as in a test environment or a student lab. It generally doesn't impact the performance or usage of the device. If the list gets too large, some specific hardware devices may encounter functional issues. For example, not booting to an external USB drive, or not able to select the current boot entry from the list. Use the Windows **bcdedit** command to clear unused boot entries. For more information, see [BCDEdit /deletevalue](/en-us/windows-hardware/drivers/devtest/bcdedit--deletevalue).