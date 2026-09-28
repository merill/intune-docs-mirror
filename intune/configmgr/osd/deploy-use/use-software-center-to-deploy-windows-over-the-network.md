---
layout: Conceptual
title: Use Software Center to deploy Windows over the network - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network
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
description: Deploy an OS from Software Center to refresh an existing computer with a new version of Windows or to upgrade Windows to the latest version.
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ae68bde9-0300-2042-4512-50d36bf8c71e
document_version_independent_id: 235dc233-3795-21eb-91de-364ece7db873
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0b6ec0ec-2ece-d3c1-c750-291c72cb2b27
---

# Use Software Center to deploy Windows over the network - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can make a task sequence that installs an OS available in Software Center. A user can run a task sequence from Software Center for the following OS deployment scenarios:

- [Refresh an existing computer with a new version of Windows](refresh-an-existing-computer-with-a-new-version-of-windows)
- [Upgrade Windows to the latest version](upgrade-windows-to-the-latest-version)
- [Create a task sequence for non-OS deployments](create-a-task-sequence-for-non-operating-system-deployments)

Complete the steps in one of those OS deployment scenarios. Then use the following sections to prepare for deployments that are available in Software Center.

## Deploy the task sequence

Deploy the task sequence to a target collection. For more information, see [Deploy a task sequence](deploy-a-task-sequence).

On the **Deployment Settings** page of the deployment, for the **Make available to the following** setting, select one of the following options:

- Only Configuration Manager Clients
- Configuration Manager clients, media and PXE

Also configure whether the deployment is required or available:

- Required deployment: Required deployments make the task sequence available in Software Center. It automatically starts at the configured deadline.
- Available deployment: The task sequence is available in Software Center, and a user can install it on demand.

After you create the deployment, clients in the target collection will show the task sequence in Software Center.

Note

If multiple users are signed in on the device, task sequence deployments might not appear in Software Center until other users are signed out.