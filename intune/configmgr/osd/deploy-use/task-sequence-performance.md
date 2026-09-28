---
layout: Conceptual
title: Task sequence performance - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/task-sequence-performance
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
description: To improve the overall speed of the task sequence, run it with the Windows high-performance power plan.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 73b3c4e0-f61d-7c0f-2b7f-b45d5fe459ba
document_version_independent_id: 73b3c4e0-f61d-7c0f-2b7f-b45d5fe459ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/task-sequence-performance.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/task-sequence-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/task-sequence-performance.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 414c0d31-d73c-a402-2367-07d1c7fe5ccc
---

# Task sequence performance - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To improve the overall speed of the task sequence, run it with the high-performance power plan. It configures Windows to use its built-in high-performance power plan, which delivers maximum performance at the expense of higher power consumption. This option is on by default for new task sequences.

When the task sequence starts, in most scenarios it records the currently enabled power plan. It then switches the active power plan to the Windows default **High Performance** plan. If the task sequence restarts the computer, it repeats this process. At the end of the task sequence, it resets the power plan to the stored value. This functionality works in both Windows and Windows PE, but has no effect on virtual machines.

- If the task sequence starts in Windows PE, the task sequence doesn't record the currently enabled power plan for later reuse.
- An OS deployment task sequence that reimages the computer (wipe and load) doesn't preserve the power plan setting of the old OS. At the end of the task sequence, it restores the default **Balanced** power plan.

You can use this option on devices with [modern standby](/en-us/windows-hardware/design/device-experiences/modern-standby). It also supports other devices that don't have that default power plan. When you use this task sequence option, it creates a temporary power plan that's similar to the default for **High Performance**. This power plan modifies the timeout values to `0` for standby, monitor, disk, and hibernate when plugged in. These configurations prevent these devices from falling asleep during an OS deployment task sequence. After the task sequence completes, it reverts to the original power plan, and deletes the temporary plan.

Important

To take advantage of this Configuration Manager feature, after you update the site, update clients to the latest version. Also update boot images to include the latest client components. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Configure the task sequence

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Operating Systems**, and select the **Task Sequences** node.
2. Select the task sequence to configure, and then in the ribbon select **Properties**.
3. Switch to the **More Options** tab.

    Tip

    In version 2111 and earlier, this tab is named **Performance**.
4. Enable the option to **Run as high performance power plan**.

Warning

Be cautious with this setting on low performance hardware. Running intense system operations for an extended period of time can strain low-end hardware. Check with your hardware manufacturer for specific guidance.

## Known issues

Usually, when you change settings in task sequence properties, it updates all existing deployments. When you change this performance setting in the task sequence properties, it doesn't affect any existing deployments of the task sequence. To enable or disable this setting for high performance, create a new task sequence deployment.