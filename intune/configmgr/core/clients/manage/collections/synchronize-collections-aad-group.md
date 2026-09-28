---
layout: Conceptual
title: Synchronize collection members to Microsoft Entra groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/synchronize-collections-aad-group
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
description: Synchronize collection members to Microsoft Entra groups.
ms.date: 2022-03-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a73cf95f-3648-bb48-9cde-94df8d535d9f
document_version_independent_id: a73cf95f-3648-bb48-9cde-94df8d535d9f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/synchronize-collections-aad-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/synchronize-collections-aad-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/synchronize-collections-aad-group.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: a8654b7c-6b21-1e6d-9e89-0c45673b835b
---

# Synchronize collection members to Microsoft Entra groups - Configuration Manager | Microsoft Learn

You can enable the synchronization of collection memberships to a Microsoft Entra group. This synchronization allows you to use your existing on premises grouping rules in the cloud by creating Microsoft Entra group memberships based on collection membership results. You can synchronize device or user collections. Only resources with a Microsoft Entra ID record are reflected in the Microsoft Entra group. Both Microsoft Entra hybrid joined and Microsoft Entra joined devices are supported. The synchronization of collection memberships is a one-way process from Configuration Manager to Microsoft Entra ID. Ideally, Configuration Manager should be the authority for managing the membership for the target Microsoft Entra groups.

Synchronizations can either be full or incremental and they have slightly different behaviors: 

- Full synchronization: Occurs on the first synchronization after enabling it. You can force a full synchronization by selecting the collection, and then choosing **Synchronize Membership** from the ribbon. A full synchronization will overwrite members of the Microsoft Entra group.
- Incremental synchronization: Occurs every 5 minutes. Changes made in Microsoft Entra ID aren't reflected in Configuration Manager collections, but they aren't overwritten by Configuration Manager.

Example synchronization scenario:

1. From Microsoft Entra ID, create a group called `Group1` and add `DeviceA`, `DeviceB`, and `DeviceC`.
    - Ideally, objects wouldn't be added from Microsoft Entra ID since Configuration Manager should manage the group membership.
2. From Configuration Manager, create a collection called `Collection1` then add `DeviceB`, and `DeviceC`.
3. Enable synchronization for `Collection1` to `Group1`.
4. The first synchronization is a full synchronization so, `Group1` now contains `DeviceB`, and `DeviceC`. `DeviceA` was removed from the group during the full synchronization.
5. Remove `DeviceC` from `Collection1` and wait for an incremental synchronization.
6. `Group1` now contains only `DeviceB`.
7. From Microsoft Entra ID, add `DeviceD` to `Group1` and wait for an incremental synchronization.
8. `Group1` now contains `DeviceB` and `DeviceD`.
9. From Configuration Manager, select `Collection1`, and choose **Synchronize Membership** from the ribbon to force a full synchronization.
10. `Group1` now contains only `DeviceB`

## Prerequisites

- Supported version of Windows 10 (x64) or Windows 11 (x64)
- Windows Server OS 2019 and later (Standard or Datacenter)
- Integration with Microsoft Entra ID for [cloud management](../../../servers/deploy/configure/azure-services-wizard).
- [Microsoft Entra user discovery](../../../servers/deploy/configure/about-discovery-methods#azureaddisc)
- An HTTPS or [Enhanced HTTP](../../../plan-design/hierarchy/enhanced-http)-enabled management point
- Access to the **All Systems** collection

    Note

    The option to **Disable Microsoft Entra authentication for this tenant**, under Azure Services for Cloud Management in the console, must **not** be checked as this prevents client registration using Entra ID Authentication.

## Create a group and set the owner in Microsoft Entra ID

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Navigate to **Microsoft Entra ID** &gt; **Groups** &gt; **All groups**.
3. Select **New group**, enter a **Group name**, and optionally enter a **Group description**.
4. Make sure that **Membership type** is **Assigned**.
5. Select **Owners**, then add the identity that will create the synchronization relationship in Configuration Manager.

    Tip

    The Server App (Service Principle) of Microsoft Entra tenant will be the owner for the created Microsoft Entra group.
6. Select **Create** to finish creating the Microsoft Entra group.

## Enable collection synchronization for the Azure service

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Cloud Services**, and select the **Azure Services** node.
2. Select the cloud management service for the Microsoft Entra tenant where you created the group. Then in the ribbon, select **Properties**.
3. Switch to the **Collection Synchronization** tab, and select the option to **Enable Azure Directory Group Sync**.
4. Select **OK** to save the setting.

## Enable the collection to synchronize

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select either the **Device Collections** or **User Collections** node.
2. Select the collection to sync. Then in the ribbon, select **Properties**.
3. Switch to the **Cloud Sync** tab, and select **Add**.
4. If necessary, change the **Tenant** to where you created the Microsoft Entra group.
5. Type in your search criteria in the **Name starts with** field, then select **Search**. If you leave the criteria blank, the search returns all groups from the tenant. If it prompts you to sign in, use the identity you specified as the owner for the Microsoft Entra group.
6. Choose the target group, and then select **OK** to add the group. Select **OK** again to exit the collection's properties.

Wait about five to seven minutes before you can verify the group memberships in the Azure portal. To start a full synchronization, select the collection, and then in the ribbon select **Synchronize Membership**.

[![Screenshot of Synchronize collections to Microsoft Entra ID.](media/3607475-sync-collection-to-azuread.png)](media/3607475-sync-collection-to-azuread.png#lightbox)

## Use PowerShell

You can use PowerShell to synchronize collections. For more information, see the following cmdlet article:

[Set-CMCollectionCloudSync](/en-us/powershell/module/configurationmanager/set-cmcollectioncloudsync)

## Monitor the collection synchronization status

1. In the Configuration Manager console, go to the **Monitoring** workspace
2. select **Collection Cloud Sync** and select either the **Device Collections** or **User Collections** node.
3. The view lists all the collections that are enabled for cloud sync and relevant details.
4. Right click on column header and add additional columns to view more information.
5. On clicking each collection, you can view collection member status in the bottom tab.
6. The members are categorized based on sync status - Success, Failed, In Progress.
7. On clicking Failed tab, you can find the reason for failure across each member.

[![Screenshot of Collections Cloud Sync Status.](media/collection-aad-group-sync.png)](media/collection-aad-group-sync.png#lightbox)

Default Columns:

- Collection Id – Id of Collection
- Collection Name – Name of Collection
- Microsoft Entra group Id – Configured Microsoft Entra group Id
- Microsoft Entra group Name – Configured Microsoft Entra group Name
- Cloud Sync Status

    Success: If all members are synchronized to target Microsoft Entra group

    Partial Success: If at least one member is synchronized to target Microsoft Entra group

    Failed: If all members failed to synchronize to target Microsoft Entra group

    In Progress: Synchronization is in progress.
- Member Count – Count of members of collection
- Sync Completed – Count of members successfully synchronized
- Sync InProgress – Count of members pending synchronization
- Sync Failed – Count of members failed to synchronize

Optional Columns:

- Cloud Service Id – Azure Service Id which is used for Cloud Sync
- Collection Type – Type of Collection (Device or User)
- Last Full Sync Member Count – Count of members synchronized during last full sync
- Last Full Sync Status – Status of last full sync cycle
- Last Full Sync Time – Time of last full sync cycle
- Last Sync Member Count - Count of members synchronized during last sync
- Last Sync Status - Status of last sync cycle
- Last Sync Time - Time of last sync cycle

## Verify the Microsoft Entra group membership

1. Go to the [Azure portal](https://portal.azure.com).
2. Navigate to **Microsoft Entra ID** &gt; **Groups** &gt; **All groups**.
3. Find the group you created and select **Members**.
4. Confirm that the members reflect the resources in the Configuration Manager collection. Only resources with Microsoft Entra identity show in the group.