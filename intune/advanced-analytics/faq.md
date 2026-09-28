---
layout: FAQ
title: Advanced Analytics FAQ - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/faq
summary: >
  <p>This article addresses frequently asked questions about Advanced Analytics in Microsoft Intune.</p>

  <p><strong>Feature comparison and licensing</strong></p>

  <ul>

  <li><a href="#what-s-the-difference-between-endpoint-analytics-and-advanced-analytics">What's the difference between endpoint analytics and Advanced Analytics?</a></li>

  <li><a href="#do-i-need-additional-licensing-for-advanced-analytics">Do I need additional licensing for Advanced Analytics?</a></li>

  </ul>

  <p><strong>Integration and compatibility</strong></p>

  <ul>

  <li><a href="#can-advanced-analytics-integrate-with-other-monitoring-tools">Can Advanced Analytics integrate with other monitoring tools?</a></li>

  <li><a href="#are-there-limitations-with-device-types-or-os-versions">Are there limitations with device types or OS versions?</a></li>

  </ul>

  <p><strong>Data collection and refresh</strong></p>

  <ul>

  <li><a href="#how-often-is-analytics-data-refreshed">How often is analytics data refreshed?</a></li>

  <li><a href="#why-is-the-analytics-data-not-getting-updated">Why is the analytics data not getting updated?</a></li>

  <li><a href="#why-are-the-device-reports-incomplete">Why are the device reports incomplete?</a></li>

  <li><a href="#what-should-i-do-if-a-device-is-not-reporting-data">What should I do if a device is not reporting data?</a></li>

  </ul>

  <p><strong>Dashboards and baselines</strong></p>

  <ul>

  <li><a href="#can-i-customize-analytics-dashboards">Can I customize analytics dashboards?</a></li>

  <li><a href="#how-should-the-baselines-be-used">How should the baselines be used?</a></li>

  </ul>

  <p><strong>Anomaly detection</strong></p>

  <ul>

  <li><a href="#why-do-some-crashes-or-anomalies-sometimes-not-appear-in-the-anomalies-report--even-when-the-devices-are-correctly-licensed-and-enrolled">Why do some crashes or anomalies sometimes not appear in the anomalies report, even when the devices are correctly licensed and enrolled?</a></li>

  </ul>
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: This article provides answers to some frequently asked questions about Advanced Analytics.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: faq
locale: en-us
document_id: 672bc311-4c3f-2676-8a0c-4ff9fa74e967
document_version_independent_id: 672bc311-4c3f-2676-8a0c-4ff9fa74e967
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: f707a1db-3c7d-27c7-8d2c-2e28cadf3a93
---

# Advanced Analytics FAQ - Microsoft Intune | Microsoft Learn

This article addresses frequently asked questions about Advanced Analytics in Microsoft Intune.

**Feature comparison and licensing**

- What's the difference between endpoint analytics and Advanced Analytics?
- Do I need additional licensing for Advanced Analytics?

**Integration and compatibility**

- Can Advanced Analytics integrate with other monitoring tools?
- Are there limitations with device types or OS versions?

**Data collection and refresh**

- How often is analytics data refreshed?
- Why is the analytics data not getting updated?
- Why are the device reports incomplete?
- What should I do if a device is not reporting data?

**Dashboards and baselines**

- Can I customize analytics dashboards?
- How should the baselines be used?

**Anomaly detection**

- Why do some crashes or anomalies sometimes not appear in the anomalies report, even when the devices are correctly licensed and enrolled?

## Feature comparison and licensing

### What's the difference between endpoint analytics and Advanced Analytics?

Advanced Analytics builds on endpoint analytics by offering deeper insights, advanced reporting, and enhanced anomaly detection capabilities.

### Do I need additional licensing for Advanced Analytics?

Yes, Advanced Analytics requires specific licensing. Review the prerequisites for details.

## Integration and compatibility

### Can Advanced Analytics integrate with other monitoring tools?

Advanced Analytics doesn't provide a connector for data to be leveraged in other monitoring tools. Some features, such as Device Query for multiple devices, do support an export via .csv function, which could then be used in other tooling.

### Are there limitations with device types or OS versions?

Some features might be limited to specific Windows builds, OS versions, or device types. Review the prerequisites before deployment.

## Data collection and refresh

### How often is analytics data refreshed?

Data is typically updated every 24 hours. Real-time troubleshooting might require direct device queries.

### Why is the analytics data not getting updated?

Ensure devices are online and have connectivity to required Microsoft endpoints. Verify data collection settings and licensing status. Devices must restart at least once after the policy is applied for data to properly display.

### Why are the device reports incomplete?

Verify that targeted devices meet the [prerequisites](./#prerequisites). In some cases, end-to-end latency can exceed 24 hours if event details aren't uploaded from the client immediately. This delay often occurs with events such as restarts or stop errors when the device doesn't reboot right after the shutdown or error. When this happens, the event details are uploaded at the next available opportunity. The event then appears on the timeline with a timestamp that reflects when the event originally occurred.

### What should I do if a device is not reporting data?

Check device connectivity, enrollment status, and compliance with system requirements.

## Dashboards and baselines

### How should the baselines be used?

Baseline scores are shown on charts as triangle markers. There's a built-in baseline for All organizations (median), which allows you to compare your scores to a typical enterprise. You can create new baselines based on your current metrics so you can track progress or view regressions over time.

### Can I customize analytics dashboards?

Yes, dashboards can be tailored to highlight key metrics and device scopes relevant to your organization.

## Anomaly detection

### Why do some crashes or anomalies sometimes not appear in the anomalies report, even when the devices are correctly licensed and enrolled?

This is typically due to the volume and usage patterns of devices and apps. The device must be actively used, enrolled in endpoint analytics, and data collection is enabled. In addition, a high volume of events (such as critical errors or app crashes) is usually required before the event is flagged as anomalous.