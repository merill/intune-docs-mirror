---
layout: Conceptual
title: Monitor clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/monitor-clients
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
description: Learn how to monitor the health and activity of clients in Configuration Manager.
ms.date: 2021-11-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 42c9ccff-7126-eab6-2d00-d8a8814c10b8
document_version_independent_id: 12cd6269-5e3b-12a2-1616-d52c36d07d62
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/monitor-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/monitor-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/monitor-clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3f16d65f-60f6-6b83-063e-05f9c4434df6
---

# Monitor clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Once you install the Configuration Manager client on the Windows devices in your site, monitor their health and activity in the Configuration Manager console.

## About client status

Configuration Manager provides the following types of information as client status:

- **Client online status**: The site considers a device as **online** if it's connected to its assigned management point. To indicate that the client is online, it sends ping-like messages to the management point. If the management point doesn't receive a message in five minutes, the site considers the client as **offline**.

    Tip

    These messages use the client notification channel. For more information, see [Ports used in Configuration Manager](../../plan-design/hierarchy/ports#BKMK_PortsClient-MP).
- **Client activity**: The site considers the client as **active** if it has communicated with Configuration Manager in the past seven days. The site considers the client **inactive** if it hasn't done the following actions in seven days:

    - Requested policy update
    - Sent a heartbeat message
    - Sent hardware inventory
- **Client check**: The state of the periodic evaluation that the Configuration Manager client runs on the device. The evaluation checks the device and can remediate some of the problems it finds. For more information, see [Client health checks](client-health-checks).

    Client check runs automatically during the Windows maintenance window.

    You can configure remediation not to run on specific devices, for example, a business-critical server. For more information, see [How to configure client status](../deploy/configure-client-status#automatic-remediation-exclusion).

    If there are more items that you want to evaluate, use Configuration Manager compliance settings to monitor other configurations. For more information about compliance settings, see [Plan for and configure compliance settings](../../../compliance/plan-design/plan-for-and-configure-compliance-settings).
- **Decommissioned**: The site has marked the device record for deletion. This behavior can happen when a new registration for same device assigns to the same or a different primary site in a hierarchy. The site deletes these devices the next time it runs the site maintenance task **Delete Aged Discovery Data**.
- **Obsolete**: The site has discovered a new device record with the same hardware ID, so it marks the old record as obsolete. Reports don't count obsolete records of the same device multiple times. You can still target policies to obsolete devices. If the site doesn't get a heartbeat for an obsolete record after 90 days of inactivity, it removes the obsolete device when it runs the site maintenance task **Delete Obsolete Client Discovery Data**.

Tip

The [Power BI sample reports](../../servers/manage/powerbi-sample-reports) for Configuration Manager includes a report called **Client Status**. This report can also help with monitoring clients. 

## Monitor individual clients

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select either the **Devices** node or choose a collection under **Device Collections**.

    The icons at the beginning of each row indicate the online status of the device:

    | Icon | Description |
    | --- | --- |
    | ![Online status icon for clients.](media/online-status-icon.png) | Device is online. |
    | ![Offline status icon for clients.](media/offline-status-icon.png) | Device is offline. |
    | ![Unknown status icon for clients.](media/unknown-status-icon.png) | Online status is unknown. |
    | ![Client not installed icon.](media/client-not-installed.png) | Client isn't installed on the device. |
2. For more detailed online status, add the client online status information to the device view. Right-click the column header and select the online status fields you want to add:

    - **Device Online Status**: Indicates whether the client is currently online or offline. (This status is the same information given by the icons.)
    - **Last Online Time**: Indicates when the client online status changed to online.
    - **Last Offline Time** indicates when the status changed to offline.
3. Select an individual client in the list pane to see more status in the detail pane. This information includes client activity and client check status.

## Monitor the status of all clients

1. In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Client Status** node. Review the overall statistics for client activity and client checks across the site. Change the scope of the information by choosing a different collection.
2. To drill down into detail about the reported statistics, choose the name of the reported information. For example, **Active clients that have passed client check or no results**. Then review the information about the individual clients.
3. Select **Client Activity** to see charts showing the client activity in your Configuration Manager site.
4. Select **Client Check** to see charts showing the status of client checks in your Configuration Manager site.

    Configure alerts to notify you when client check results or client activity drops below a specified percentage. The site can also alert you when remediation fails on a specified percentage of clients. For more information, see [How to configure client status](../deploy/configure-client-status).

For more information on the client's regular checks to keep healthy, see [Client health checks](client-health-checks).