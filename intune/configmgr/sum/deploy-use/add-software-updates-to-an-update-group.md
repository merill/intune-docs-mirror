---
layout: Conceptual
title: Add updates to an update group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/add-software-updates-to-an-update-group
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
description: Manually or automatically add software updates to a software update group in your environment.
ms.date: 2022-07-12T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: 12af12b3-43e4-01b6-f6d6-ac031a064cce
document_version_independent_id: ad1dae03-40ff-1635-06cd-bed158292045
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/add-software-updates-to-an-update-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/add-software-updates-to-an-update-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/add-software-updates-to-an-update-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab06385-661e-4214-8870-bbe4071c960d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/131ba09e-4280-4ae7-8622-1f9f1c0daad1
platformId: 0f5975a8-347b-ed52-c2f6-11d77ab2149d
---

# Add updates to an update group - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Software update groups provide you with an effective method to organize software updates in your environment. You can manually add software updates to a software update group or automatically add software updates to a software update group by using an ADR. You can also deploy a software update group manually or deploy the group automatically by using an ADR. After you deploy a software update group, you can add new software updates to the group and Configuration Manager will automatically deploy them. Use the following procedures to add software updates to a new or existing software update group.

Tip

- Starting in version 2203, you can organize software update groups and packages by using folders. This change allows for better categorization and management of software updates. For more information, see [Deploy software updates](deploy-software-updates#bkmk_folder).
- Devices running an unsupported operating systems will display as compliant since there aren't applicable updates to the operating system any longer.

## Add software updates to a new software update group

1. In the Configuration Manager console, select **Software Library**.
2. In the Software Library workspace, expand **Software Updates**, and then select **All Software Updates**.
3. Select the software updates to be added to the new software update group.
4. On the **Home** tab, in the **Update** group, select **Create Software Update Group**.
5. Specify the name for the software update group and optionally provide a description. Use a name and description that provide enough information for you to determine what type of software updates are in the software update group. To proceed, select **Create**.
6. Select **Software Update Groups** to display the new software update group.
7. Select the software update group, and in the **Home** tab, in the **Update** group, select **Show Members** to display a list of the software updates that are included in the group.

Note

Feature updates can't be added to a software update group. Use the following options to manage feature updates:

- [Windows servicing](../../osd/deploy-use/manage-windows-as-a-service)
- [Phased deployments](../../osd/deploy-use/create-phased-deployment-for-task-sequence)
- [Upgrade OS task sequences](../../osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

## Add software updates to an existing software update group

1. In the Configuration Manager console, select **Software Library**.
2. In the Software Library workspace, expand **Software Updates**, and then select **All Software Updates**.
3. Select the software updates that you want to add to the new software update group.

    - On the **All Software Updates** node, Configuration Manager displays all updates except those in the **Upgrades** classification and **Office 365 Client** product classification.
4. On the **Home** tab, in the **Update** group, select **Edit Membership**.
5. Select the software update group into which you want to add the software updates.
6. Select the **Software Update Groups** node to display the software update group.
7. Select the software update group, and in the **Home** tab, in the **Update** group, select **Show Members** to display a list of the software updates that are included in the software update group.

## Remove software updates from an existing software update group

1. In the Configuration Manager console, select **Software Library**.
2. In the Software Library workspace, expand **Software Updates**, and then select **Software Update Groups**.
3. Select the software update group from which you want to remove updates, then select **Show members**
4. Right-click on the update to remove and select **Edit Membership**.
    - Select multiple updates by using either the Shift or Ctrl keys.
    - From the **All Software Updates** node, you can also use **Edit Membership** from the ribbon after selecting an update.
5. Uncheck the box for the software update group from which you'd like to remove the update, then select **Ok**.