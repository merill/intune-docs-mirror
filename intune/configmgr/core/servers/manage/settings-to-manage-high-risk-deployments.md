---
layout: Conceptual
title: Manage high-risk deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/settings-to-manage-high-risk-deployments
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
description: Configure deployment verification site settings in Configuration Manager to warn admins if they create a high-risk deployment.
ms.date: 2022-03-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 833fb8c4-39db-2a92-f0cc-d8d6d498e24e
document_version_independent_id: 6dbb74b2-fec2-8fa6-2763-25cf98a6f325
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/settings-to-manage-high-risk-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/settings-to-manage-high-risk-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/settings-to-manage-high-risk-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6bbdfdae-81c4-e15e-0132-4fb46e7c85d8
---

# Manage high-risk deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With Configuration Manager, you can configure *deployment verification* site settings. These settings warn administrators if they create a high-risk task sequence deployment. A high-risk deployment is:

- A deployment that's automatically installed
- Has the potential to cause unwanted results

For example, a task sequence with a purpose of **Required** that deploys an operating system is considered high-risk.

Warning

If you use PXE deployments, and configure device hardware with the network adapter as the first boot device, these devices can automatically start an OS deployment task sequence without user interaction. Deployment verification doesn't manage this configuration. While this configuration may simplify the process and reduce user interaction, it puts the device at greater risk for accidental reimage.

## Deployment verification settings

To reduce the risk of an unwanted high-risk deployment, you can configure size limits in these deployment verification settings:

- **Collection size limits**: When you create a deployment, hide collections that include more clients than your limit.

    - **Default size**: When you create a deployment, this setting hides collections by default that include more clients than this limit. You can still see these collections when creating the deployment, but they're hidden by default. The default value is **100**. To ignore this setting, enter a value of **0**.
    - **Maximum size**: When you create a deployment, this setting always hides collections with more clients than this limit. The default value is **0**, which ignores this setting. The **Maximum size** value must be greater than the **Default size** value.

        For example, you set **Default size** to 100 and the **Maximum size** to 1000. When you create a high-risk deployment, the **Select Collection** window only displays collections that include fewer than 100 clients. If you clear the setting to **Hide collections with a member count greater than the site's minimum size configuration**, the window displays collections that include fewer than 1000 clients.
- **Collections with site system servers**: When the target collection includes a computer with a site system role, block deployments or require verification before creating the deployment. When a deployment is blocked, select a different collection that meets the deployment verification criteria to continue creating the deployment.

Note

High-risk deployments are always limited to custom collections, collections that you create, and the built-in **Unknown Computers** collection. When you create a high-risk deployment, you can't select a built-in collection such as **All Systems**.

## Configure deployment verification

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, select **Sites**, and then select the primary site to configure.
2. In the ribbon, select **Properties**, and then switch to the **Deployment Verification** tab.
3. Configure the settings you want to use, and then select **OK** to save the configuration and close the properties.