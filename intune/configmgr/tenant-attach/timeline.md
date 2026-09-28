---
layout: Conceptual
title: Tenant attach - Device timeline - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/timeline
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
description: View the timeline for Configuration Manager devices from the admin center.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.custom: sfi-image-nochange
locale: en-us
document_id: b2430d7b-36b4-1e8c-88b5-538777b498e3
document_version_independent_id: 674ef4f1-91ec-f8e6-4127-1cfd6c54fcef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/timeline.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/timeline
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/timeline.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c22630fe-cda2-8906-15d5-522479e978a8
---

# Tenant attach - Device timeline - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. When Configuration Manager synchronizes a device to Microsoft Intune through tenant attach, you can see a timeline of events. This timeline shows past activity on the device that can help you troubleshoot problems.

## Prerequisites

The following items are needed to use the timeline from the admin center:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details#prerequisites).
- Enable Endpoint analytics data collection in Configuration Manager:
    1. In the Configuration Manager console, go to **Administration** &gt; **Client Settings** &gt; **Default Client Settings**.
    2. Right-click and select **Properties** then select the **Computer Agent** settings.
    3. Set **Enable Endpoint analytics data collection** to **Yes**.
        - Only events collected after the client receives this policy will be visible in the admin center. Events prior to receiving the policy won't be accessible.

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission under **Collection** in Configuration Manager.
- The **Notify Resource** permission under **Collection** in Configuration Manager.
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

## Generate events

Devices send events once a day to the admin center. Only events collected after the client receives the **Enable Endpoint analytics data collection** policy are visible in the admin center. Generate test events easily by installing an application or an update from Configuration Manager, or restart the device. Events are kept for 30 days. Use the chart to view events that are collected.

## Collected events

| Event name | Provider name | Event ID |
| --- | --- | --- |
| Application Error | Application Error | 1000 |
| Application Hang | Application Hang | 1002 |
| Kernel Crash | Microsoft-Windows-WER-SystemErrorReporting | 1001 |
| Application Crash | Windows Error Reporting | 1001 |
| Windows Update Agent – Update Installation | Microsoft-Windows-WindowsUpdateClient | 19 |
| Unknown Shutdown | Boot | 0 |
| Initiated Shutdown | Boot | 1074 |
| Abnormal Shutdown | Boot | 41 |
| Boundary Group Change | Microsoft-ConfigMgr | 20000 |
| Application Deployment | Microsoft-ConfigMgr | 20001 |
| Configuration Manager – Update Installation | Microsoft-ConfigMgr | 20002 |
| Firmware version change | Microsoft-ConfigMgr | 20003 |
| Configuration Manager Reboot request | Microsoft-ConfigMgr | 20005 |
| Client repair | Microsoft-ConfigMgr | 20006 |
| State resync | Microsoft-ConfigMgr | 20007 |
| Inventory resync | Microsoft-ConfigMgr | 20008 |

## View the timeline

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Timeline**. By default, you're shown events from the last 24 hours.

    - Use the **Filter** button to change the **Time range**, **Event levels**, and **Provider name**.
    - If you select on an event, you'll see the detailed message for it.
    - Select **Sync** to fetch the recent data generated on client. The device sends events once a day to the admin center by default.
    - Select **Refresh** to reload the page and to see newly collected events.

    [![Timeline of events for a device](media/7141381-timeline.png)](media/7141381-timeline.png#lightbox)

## Known issues

You will receive a time out error if the following condition applies:

- You're opening **Timeline** for the very first time after restarting SMSExecutive on the service connection point's on-premises server.

To work around the issue, reload the **Timeline** page.