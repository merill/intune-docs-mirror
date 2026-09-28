---
layout: Conceptual
title: Prepare for unknown computer deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/prepare-for-unknown-computer-deployments
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
description: Learn how to deploy operating systems to computers that aren't managed by Configuration Manager in your Configuration Manager environment.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 3316b076-6d99-598f-999f-b9cf373b228f
document_version_independent_id: 10cc560e-40fa-9d44-5e31-11a058f7f8f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/get-started/prepare-for-unknown-computer-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/get-started/prepare-for-unknown-computer-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/get-started/prepare-for-unknown-computer-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2f8a9b7b-27ce-bb1d-3cb1-aca511e713e7
---

# Prepare for unknown computer deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information in this topic to deploy operating systems to unknown computers in your Configuration Manager environment. An unknown computer is a computer that isn't managed by Configuration Manager. This means that there's no record of these computers in the Configuration Manager database. Unknown computers include the following:

- A computer where the Configuration Manager client isn't installed
- A computer that isn't imported into Configuration Manager
- A computer that isn't been discovered by Configuration Manager

    You can deploy operating systems to unknown computers with the following deployment methods:
- [Use PXE to deploy Windows over the network](../deploy-use/use-pxe-to-deploy-windows-over-the-network)
- [Use bootable media to deploy an operating system](../deploy-use/create-bootable-media)
- [Use prestaged media to deploy an operating system](../deploy-use/create-prestaged-media)

## Unknown computer deployment workflow

The following is the basic workflow to deploy an operating system to an unknown computer:

- Select an unknown computer object to use in the deployment. You can deploy the operating system to one of the unknown computer objects in the **All Unknown Computers** collection or you can add the objects in the **All Unknown Computer** collection to another collection. Configuration Manager provides two unknown computer objects in the **All Unknown Computers** collection. One object is for x86 computers and the other object is for x64 computers.

    Note

    The **x86 Unknown Computer** object is for computers that are only x86 capable. The **x64 Unknown Computer** object is for computers that are x86 and x64 capable. In other words, these objects describe the architecture of the destination computer. They do not describe the operating system that you want to deploy to the destination computer.
- Configure a PXE-enabled distribution point or create media to support unknown computer deployments.
- Deploy the task sequence to install the operating system.

## Unknown Computer Installation Process

When a computer is first started from PXE or from media, Configuration Manager checks to see if a record for that computer exists in the Configuration Manager database. If there's a record, Configuration Manager then checks to see if there are any task sequences deployed to the record. If there isn't a record, Configuration Manager checks to see if there are any task sequences deployed to an unknown computer object. In either case, Configuration Manager then performs one of the following actions:

- If there's an available task sequence, Configuration Manager prompts the user to run the task sequence.
- If there's a required task sequence, Configuration Manager automatically runs the task sequence.
- If a task sequence isn't deployed for the record, Configuration Manager generates an error that there's no deployed task sequence for the destination computer.

    When an unknown computer is started, Configuration Manager recognizes the computer as an unprovisioned computer rather than an unknown computer. This means that the computer can now receive the task sequences that were deployed to the unknown computer object. The deployed task sequence then installs an operating system image that must include the Configuration Manager client.

    After the Configuration Manager client is installed, a record for the computer is created and the computer is listed in the appropriate Configuration Manager collection. If the computer fails to install the operating system image or the Configuration Manager client, an "Unknown" record for the computer is created and the computer appears in the **All Systems** collection.

Note

During the installation of the operating system image, the task sequence can retrieve collection variables but not computer variables from this computer.

## Enabling Unknown Computer Support

Use the following to enable unknown computer support when you deploy an operating system by using PXE, bootable media, and prestaged media.

- **PXE**

    Select the **Enable unknown computer support** check box on the **PXE** tab for a distribution point that is enabled for PXE. For more information, see [Configuring distribution points to accept PXE requests](prepare-site-system-roles-for-operating-system-deployments#configuring-distribution-points-to-accept-pxe-requests).
- **Bootable media**

    Select the **Enable unknown computer support** check box on the **Security** page of the Create Task Sequence Media Wizard. For more information, see [Configuring distribution points to accept PXE requests](prepare-site-system-roles-for-operating-system-deployments#configuring-distribution-points-to-accept-pxe-requests) and [Use PXE to deploy Windows over the network with Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network).
- **Prestaged media**

    Select the **Enable unknown computer support** check box on the **Security** page of the Create Task Sequence Media Wizard. For more information, see [Create prestaged media with Configuration Manager](../deploy-use/create-prestaged-media).