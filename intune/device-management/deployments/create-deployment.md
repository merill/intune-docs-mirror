---
layout: Conceptual
title: Create and manage a deployment in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: wicale
ms.collection:
- M365-identity-device-management
description: Create, pause, resume, and cancel ring-based deployments of Intune apps and policies, and understand deleted-group behavior.
ms.date: 2026-08-26T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: wicale
locale: en-us
document_id: 6bd131bc-aa48-4a2d-55ea-fc1cdbce001a
document_version_independent_id: 6bd131bc-aa48-4a2d-55ea-fc1cdbce001a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/deployments/create-deployment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/deployments/create-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/deployments/create-deployment.md
platformId: b4f17ec7-d159-3c5d-1872-e5b0ec51f653
---

# Create and manage a deployment in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

This feature is in public preview. For more information, see [Public preview in Microsoft Intune](../../fundamentals/public-preview).

A deployment delivers one Intune payload, such as an app or device configuration policy, to devices through a gradual rollout. You can use a deployment plan or manually define rings, timing, and group assignments. For more information, see [Deployment plans and deployments overview](overview).

## Prerequisites

- **Permissions**: You need **Read** and **Assign** permissions for the payload's category:

    - For a device configuration payload, use the **Device configurations** category.
    - For an app payload, use the **Mobile apps** category.

    For more information, see [Permissions, scope tags, and approvals for deployments](rbac-scope-tags).
- **Payload**: The supported app or policy that you want to deploy must already exist in Intune.
- **No other active deployment**: The payload can't be selected in more than one scheduled or active deployment.
- **Groups**: Each ring must have at least one group assignment.

## Create a deployment

1. Sign in to the [Microsoft Intune admin center].
2. Select **Devices** from the left navigation menu.
3. Under **Manage devices**, select **Deployments**.
4. On the **Deployments** page, select **Create**.
5. On the **Basics** page, enter a **Name** and **Description**, and then select **Next**.
6. On **Payload selection**, select a **Payload type**:
    - **Device configuration**
    - **App**
7. Select **Add payload**, select one payload from the list, and then select **Select payload**.
8. Select **Next**.
9. On **Deployment schedule**, choose one of the following options:
    - To use an existing plan, continue to Use a deployment plan.
    - To configure a one-time schedule, continue to Manually configure rings.

### Use a deployment plan

1. On **Deployment schedule**, select **Load deployment plans**.
2. On **Select deployment plan**, set the first ring's **Start date** and **Start time**.
3. Search for or select a deployment plan, and then select **Select**.
4. After the plan loads, optionally update its groups and assignment filters for this deployment.
5. Select **Next**.
6. On **Review + create**, verify the deployment, and then select **Create**.

### Manually configure rings

1. On **Deployment schedule**, select **Add rings**.
2. On **Manage rings**, enter a name, start date, and start time for the first ring.
3. Select **Add ring** for each additional ring. Configure the interval between rings in days and hours.

    Important

    Deployments require at least a one-hour interval between rings.
4. Select **Save**.
5. Add groups to each ring. Each ring requires at least one group assignment.

    Important

    Adding the **All users** or **All devices** virtual group to a ring automatically makes it the final ring. Virtual groups and Microsoft Entra security groups can't be combined in the same ring.
6. Optionally, add exclude groups. Exclude groups apply to all rings in the deployment.
7. Select **Next**.
8. On **Review + create**, verify the deployment, and then select **Create**.

## Resolve an assignment collision

Intune checks for collisions between payload assignments and deployment-ring groups when you create a deployment and when each ring activates.

- If a collision is detected while you configure a deployment, remove the group from the payload assignment or deployment configuration before you select **Create**.
- If a collision is detected when a ring activates, the deployment enters an error state and pauses. Remove the colliding group from the payload's assignments, return to the deployment, and select **Resume**.

## Manage a deployment

After you create a deployment, you can update its name and description. You can't modify its selected payload, ring names, schedule, groups, or scope tag information through the deployment.

### Pause a deployment

Pausing a deployment stops ring progression. Assignments from rings that already activated remain on the payload.

1. Go to **Devices** &gt; **Manage devices** &gt; **Deployments**.
2. Select the active deployment.
3. Select **Pause**.

### Resume a deployment

Resuming a paused deployment allows ring progression to continue.

1. Go to **Devices** &gt; **Manage devices** &gt; **Deployments**.
2. Select the paused deployment.
3. Select **Resume**.

If a deployment is in an error state, resolve the error before you resume it.

### Cancel a deployment

Canceling a deployment stops future ring progression. Assignments from rings that already activated remain on the payload.

1. Go to **Devices** &gt; **Manage devices** &gt; **Deployments**.
2. Select the deployment.
3. Select **Cancel**.

Important

Canceling a deployment doesn't remove assignments that completed rings added to the payload. To remove those assignments, edit the payload's properties.

## Deployments and deleted groups

Deployments and deployment plans use Microsoft Entra groups to target devices and users across rings. Deleted groups affect deployments and plans as described in the following table.

| Group state | Deployments | Deployment plans |
| --- | --- | --- |
| **Permanently deleted group** | If an activating ring contains a permanently deleted group, the deployment enters an error state and displays **Group deleted from Microsoft Entra ID**. Cancel or delete the deployment, and create a new deployment if needed. | When you open a plan that contains a permanently deleted group, a banner displays **Group deleted from Microsoft Entra ID**. Remove all deleted groups before you create a deployment from or save the plan. |
| **Soft-deleted group** | If an activating ring contains a soft-deleted group, the deployment enters an error state and the group status displays **Soft-deleted**. During the 30-day recovery window, restore the group and resume the deployment, or cancel or delete the deployment. **Resume** remains unavailable until all soft-deleted groups are restored. If the deployment contains both soft-deleted and permanently deleted groups, you must cancel or delete it. | When you open a plan that contains a soft-deleted group, a banner appears and the **Group status** column displays **Soft-deleted**. Restore or remove all affected groups before you continue or save the plan. |
| **Deleted groups leave an empty ring** | Not applicable. | When you open the plan, a deletion banner and each group's deletion status appear. Remove the deleted groups and assign at least one group to each empty ring before you continue or save. |

For information about recovering groups during the soft-deletion window, see [Restore a deleted Microsoft 365 group or cloud security group](/en-us/entra/identity/users/groups-restore-deleted).