---
layout: Conceptual
title: Replace an existing computer and transfer settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/replace-an-existing-computer-and-transfer-settings
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
description: In Configuration Manager, choose from deployment methods, such as bootable media, multicast, or Software Center, to replace an existing computer with a new computer.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e0f2f3d1-5137-294b-e176-c2fbe5008201
document_version_independent_id: 6f84d216-40d0-911f-353f-1d16c5e1a196
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/replace-an-existing-computer-and-transfer-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/replace-an-existing-computer-and-transfer-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/replace-an-existing-computer-and-transfer-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6d117f3-f930-5f67-a7f2-e1d2b93ca3af
---

# Replace an existing computer and transfer settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic provides the general steps in Configuration Manager to replace an existing computer with a new computer. For this scenario, you can choose from many different deployment methods, such as bootable media, multicast, or Software Center. You can also choose to install a state migration point to store settings and then restore them to the new operating system after it is installed. If you are unsure that this is the right operating system deployment scenario for you, see [Scenarios to deploy enterprise operating systems](scenarios-to-deploy-enterprise-operating-systems).

Use the following sections to refresh an existing computer with a new version of Windows.

## Plan

- **Plan for and implement infrastructure requirements**

    There are several infrastructure requirements that must be in place before you can deploy operating systems, such as Windows ADK, User State Migration Tool (USMT), Windows Deployment Services (WDS), supported hard disk configurations, etc. For more information, see [Infrastructure requirements for operating system deployment](../plan-design/infrastructure-requirements-for-operating-system-deployment)
- **Install a state migration point (required only if you transfer settings)**

    When you are going to capture settings from the existing computer, and then restore the settings to the new operating system, you must install a state migration point. For more information, see [State migration point](../get-started/prepare-site-system-roles-for-operating-system-deployments#state-migration-point).

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
3. **Create a task sequence to deploy operating systems over the network**

    Use a task sequence to automate the installation of the operating system over the network. Use the steps in [Create a task sequence to install an operating system](create-a-task-sequence-to-install-an-operating-system) to create the task sequence to deploy the operating system. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.

    Note

    In this scenario, if you capture and restore user settings and files, you can choose to use a state migration point or save the files locally. For more information, see [Manage user state](../get-started/manage-user-state).

## Deploy

- Use one of the following deployment methods to deploy the operating system:

    - [Use Software Center to deploy Windows over the network](use-software-center-to-deploy-windows-over-the-network)
    - [Use bootable media to deploy Windows over the network](use-bootable-media-to-deploy-windows-over-the-network)
    - [Use multicast to deploy Windows over the network](use-multicast-to-deploy-windows-over-the-network)
    - [Create an image for an OEM in factory or a local depot](create-an-image-for-an-oem-in-factory-or-a-local-depot)

## Monitor

- **Monitor the task sequence deployment**

    To monitor the task sequence deployment to install the operating system, see [Monitor operating system deployments](monitor-operating-system-deployments).