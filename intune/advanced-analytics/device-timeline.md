---
layout: Conceptual
title: Device Timeline Report - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/device-timeline
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: Use the device timeline report in Intune to review device event history, identify issues faster, and correlate incidents to start troubleshooting now.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 3beecbfb-dd35-ea18-631f-899524e51112
document_version_independent_id: 3beecbfb-dd35-ea18-631f-899524e51112
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/device-timeline.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/device-timeline
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/device-timeline.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b7ade21-9e0e-1c62-bc63-2ca8b1cc9b0d
---

# Device Timeline Report - Microsoft Intune | Microsoft Learn

The device timeline allows you to see a history of events that have occurred on a specific device.

## Before you begin

- Review [Scores, baselines, and insights in endpoint analytics](../endpoint-analytics/scores) to understand these concepts.
- Confirm that your environment meets all [prerequisites](./#prerequisites).

## Review the report

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. Select a device, then select **User Experience** &gt; **Device Timeline**. [![Screenshot of the device timeline report with an event histogram and event table showing boot, sign-in, app crash, and error details over time.](media/device-timeline/event-history-chart-and-table.png)](media/device-timeline/event-history-chart-and-table.png#lightbox)
3. Filter events by date, device, or user to focus on relevant incidents.

Note

The **Device timeline** tab replaces the **Application reliability** tab in tenants that have Advanced Analytics.

You can search by event name or details. To refine results, select **Add filter** to choose the event source, event level, and a time range of interest.

The device timeline shows events such as app crashes, unresponsive apps, device boots, sign ins, and detected anomalies. Use the timeline to correlate software updates, user actions, and system events during troubleshooting. Most events appear within 24 hours.

In some cases, events may take longer to appear if details can't upload immediately. For example, restart or stop error events might be delayed when the device doesn't reboot right away. These events upload at the next available opportunity and display the original timestamp when they occurred.

Note

Event timestamps are localized to the time zone of the logged-on Intune user.

## Limitations

- If your tenant uses Advanced Analytics, the **Device timeline** tab replaces the **Application reliability** tab in device drill-down views. Unlike the timeline, the **Application reliability** tab includes the *application reliability score* for the selected device. To view this score, go to the **Device performance** tab and search for the device.
- The device timeline is available only for Intune-managed devices (including co-managed). It isn't available for Configuration Manager-only devices in tenants with Advanced Analytics enabled.