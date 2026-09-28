---
layout: Conceptual
title: Associate users with a computer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/associate-users-with-a-destination-computer
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
description: Configure Configuration Manager to associate users with destination computers when deploying operating systems.
ms.date: 2025-07-17T00:00:00.0000000Z
ms.subservice: osd
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ca1e2253-6d9c-6b24-2303-f6ac319f74a9
document_version_independent_id: c4958fd1-025f-b839-82d5-730fe142d523
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/get-started/associate-users-with-a-destination-computer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/get-started/associate-users-with-a-destination-computer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/get-started/associate-users-with-a-destination-computer.md
cmProducts: []
platformId: 6ef53c23-c809-fd48-a130-314c87ac2b72
---

# Associate users with a computer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you use Configuration Manager to deploy operating systems, you can associate users with the destination computer. This option works whether a single user or multiple users are the primary users of the destination computer.

User device affinity supports user-centric management for when you deploy applications. When you associate a user with the destination computer on which to install an OS, you can later deploy applications to that user, and the applications automatically install on the destination computer. While you can configure support for user device affinity during OS deployment, you can't use user device affinity to deploy the OS.

For more information about user device affinity, see [Link users and devices with user device affinity](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity).

There are several methods by which you can integrate user device affinity into your OS deployments. You can integrate user device affinity into PXE deployments, bootable media deployments, and pre-staged media deployments.

Note

When integrating user device affinity in OS deployments, the value of the **SMSTSAssignUsersMode** variable needs to match the value configured in the boot method (PXE, bootable media, pre-staged media).

If the values don't match, then device affinity isn't set.

### Create a task sequence that includes the **SMSTSAssignUsersMode** variable

Add the **SMSTSAssignUsersMode** variable to the beginning of your task sequence by using the [Set Task Sequence Variable](../understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) step. This variable specifies how the task sequence handles the user information.

For more information, see [Task sequence variables](../understand/task-sequence-variables#SMSTSAssignUsersMode).

### Create a prestart command that gathers the user information

The prestart command can be a VBScript with an input box. It can also be an HTML application (HTA) that validates the user data that they enter.

This prestart command must set the **SMSTSUDAUsers** variable that's used when the task sequence runs. This variable can be set on a computer, a collection, or a task sequence variable.

For more information, see [Task sequence variables](../understand/task-sequence-variables#SMSTSUDAUsers).

### Configure how distribution points and media associate the user with the destination computer

The distribution point or media supports associating users with the destination computer where the OS is deployed. Use one of the following methods:

- [Configure a distribution point to accept PXE boot requests](prepare-site-system-roles-for-operating-system-deployments#configuring-distribution-points-to-accept-pxe-requests)
- [Create bootable media](../deploy-use/create-bootable-media)
- [Create pre-staged media](../deploy-use/create-prestaged-media)

Configuring user device affinity support doesn't have a built-in method to validate the user identity. This behavior is important when a technician is provisioning the computer and enters the information on behalf of the user. In addition to setting how task sequence handles the user information, configuring these options on the distribution point and media provides the ability to restrict the deployments that are started from a PXE boot or from a specific type of media.