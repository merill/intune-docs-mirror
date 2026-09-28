---
layout: Conceptual
title: Launch tenant attached CMPivot - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/cmpivot-start
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
description: Launch CMPivot for Microsoft Intune tenant attached devices.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 021f7e40-38a9-7b11-0308-63e46f8acb86
document_version_independent_id: ba15fd58-738f-5133-37e6-5e7ba8ec2ccc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/cmpivot-start.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/cmpivot-start
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/cmpivot-start.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 3f46f2e3-1ef3-2694-229f-3956f0f345fe
---

# Launch tenant attached CMPivot - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Bring the power of on-premises [CMPivot](../core/servers/manage/cmpivot) to the Microsoft Intune admin center. Allow additional personas, like Helpdesk, to be able to initiate real-time queries from the cloud against an individual ConfigMgr managed device and return the results back to the admin center. This gives all the traditional benefits of CMPivot, which allows IT Admins and other designated personas the ability to quickly assess the state of devices in their environment and take action.

## Prerequisites

The following items are required to use CMPivot from the admin center:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details)
- Upgrade the target devices to the latest version of the Configuration Manager client.
- Target clients require a minimum of PowerShell version 4.
- To gather data for the following entities, target clients require a minimum of PowerShell version 5.0:
    - Administrators
    - Connection
    - IPConfig
    - SMBConfig

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Run CMPivot** permission on the **Collection** in Configuration Manager
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

## Launch CMPivot

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **CMPivot**.
5. Type your query in the script pane, then select **Run**.

## Save CMPivot queries to favorites

Save your frequently used queries to a **Favorites** folder in CMPivot to keep all your most used queries in one place. You can also add tags to your queries to help search and find queries.

The functionality is similar to one already present in the Configuration Manager console. The queries saved in the Configuration Manager console will not automatically be added to your **Favorites** folder. You will need to create new queries and add them to this folder.

To save your query, select the **Save** option after typing in your query. You can customise the name and tags for your query. You can view all your saved favorite queries, under the **Favorites** folder on the left panel, along with all other CMPivot entities.

[![Favorite queries folder on the left panel, above all CMPivot entities folder](media/16702226-cmpivot-favorites.png)](media/16702226-cmpivot-favorites.png#lightbox)

## Close CMPivot

To close CMPivot and return to the device information, use the `X` icon in the top right of CMPivot.

[![Close CMPivot with the X icon in Microsoft Intune admin center](media/6024392-close-cmpivot.png)](media/6024392-close-cmpivot.png#lightbox)