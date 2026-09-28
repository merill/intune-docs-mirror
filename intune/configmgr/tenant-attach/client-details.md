---
layout: Conceptual
title: Tenant attach - ConfigMgr client details in the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/client-details
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
description: View client details for Configuration Manager devices from the admin center.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: c28f9e07-1230-6b42-a2ca-f5fd6e0ed5ae
document_version_independent_id: 2b8ba990-1e3e-733d-243e-8f5d8e3b0628
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/client-details.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/client-details
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/client-details.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7876ab3b-357f-ab57-8149-8e888908cf42
---

# Tenant attach - ConfigMgr client details in the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. You can see ConfigMgr client details including collections, boundary group membership, and real-time client information for a specific device in the admin center.

## Prerequisites

- All of the prerequisites for [Microsoft Intune tenant attach](device-sync-actions) and a tenant attached environment.
- One of the following browsers:
    - Microsoft Edge, version 77 and later
    - Google Chrome
- The user accounts triggering device actions have the following prerequisites:
    - The user account needs to be a synced user object in Microsoft Entra ID (hybrid identity). This means that the user is synced to Microsoft Entra ID from Active Directory.
        - For Configuration Manager version 2103, and later:  Has been discovered with [Microsoft Entra user discovery](../core/servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory user discovery](../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
        - Starting in Configuration Manager version 2207, you can choose to implement [Intune role-based access control for tenant-attached clients](../cloud-attach/use-intune-rbac) to allow cloud-only users access to tenant attached clients

## Permissions

The user account accessing tenant attach features within the Microsoft Intune admin center needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

Important

The "Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager" check box does not grant permissions to the user to perform cloud console requests that interact with Configuration Manager unless the user is assigned an Intune role.

## View ConfigMgr client details

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select the **Client details**.

    - The primary site updates the following fields once an hour:
        - **Last policy request**
        - **Last active time**
        - **Last management point**.

    [![Client details in Microsoft Intune admin center](media/6024387-device-details.png)](media/6024387-device-details.png#lightbox)
5. Select the **Collections** to list the client's collections. 

    [![Client collections in Microsoft Intune admin center](media/6024387-device-collections.png)](media/6024387-device-collections.png#lightbox)

## List a user’s devices based on usage in the troubleshooting portal

The troubleshooting portal in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) allows you to search for a user and view their associated devices. Tenant attached devices that are assigned [user device affinity automatically based on usage](../apps/deploy-use/link-users-and-devices-with-user-device-affinity#set-up-the-site-to-automatically-create-user-device-affinities) will now be returned when searching for a user.

### Prerequisites for listing a user's device in the troubleshooting portal

- An environment that's tenant attached with uploaded devices
- Install the latest version of the Configuration Manager client
- Target clients with **User and Device Affinity**[client settings](../core/clients/deploy/about-client-settings#user-and-device-affinity)to automatically create the affinities
    - For more information, see [Create user device affinity automatically based on usage](../apps/deploy-use/link-users-and-devices-with-user-device-affinity#set-up-the-site-to-automatically-create-user-device-affinities).

### View a user's devices

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Troubleshooting + support**.
3. On the **Troubleshoot** page, select **Change user** then search for a user.
4. The **Devices**chart lists the ConfigMgr devices associated with the user.
    - Devices that previously reported affinity will resend their affinity to reflect in the admin center.
    - Devices that aren't already associated with a user will be updated once the affinity threshold has been met and reported.