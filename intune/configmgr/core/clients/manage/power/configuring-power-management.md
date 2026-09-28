---
layout: Conceptual
title: Configure power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/configuring-power-management
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
description: Set up power management in Configuration Manager.
ms.date: 2019-09-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a2978b99-9bc2-cb59-be9b-3e8dac3d050f
document_version_independent_id: 9127f4d8-64d4-9ecf-c8cf-b8e39f424765
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/configuring-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/configuring-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/configuring-power-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: cd8846a3-cc4e-dc47-7721-ed8a1402bbfe
---

# Configure power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article explains how to set up power management in Configuration Manager.

## Enable and configure client settings

This procedure configures the *default client settings* for power management. It applies to all the computers in your hierarchy.

If you want to apply these settings to only some computers, create a *custom device client setting*. Then assign it to a collection that contains the computers for power management. For more information, see [How to configure client settings](../../deploy/configure-client-settings).

1. In the Configuration Manager console, go to the **Administration** workspace, select the **Client Settings** node, and select **Default Client Settings**.
2. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
3. Select the **Power Management** group.
4. Enable the client setting to **Allow power management of devices**.
5. Configure the additional client settings that you require. For more information, see [About client settings - Power Management](../../deploy/about-client-settings#power-management).

Clients configure these settings when they next download client policy. To initiate policy retrieval for a single client, see [How to manage clients](../manage-clients#start-policy-retrieval).

## Exclude computers

You can prevent collections of computers from receiving power management settings. If a computer is a member of *any* collection that you exclude from power management settings, that computer doesn't apply power management settings. This behavior applies even if it's a member of another collection that does apply power management settings.

You might want to exclude computers from power management for the following reasons:

- You have a business requirement for computers to be turned on at all times.
- You have a control collection of computers on which you don't want to apply power management settings.
- Some of your computers are incapable of applying power management settings.
- You want to exclude computers that run Windows Server from power management.

Note

If you configure the client setting to **Allow users to exclude their device from power management**, users can exclude their own computers from power management by using Software Center.

To find out which computers are excluded from power management, run the report **Computers Excluded**. For more information about this report see [How to monitor and plan for power management](monitor-and-plan-for-power-management#BKMK_Excluded).

Important

Excluding a computer from power management causes all power settings to be reverted to their original values. You cannot revert individual power settings to their original values.

### How to exclude a collection of computers from power management

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Device Collections** node.
2. Select the collection that you want to exclude from power management. In the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
3. Switch to the **Power Management** tab, and select **Never apply power management settings to computers in this collection**.