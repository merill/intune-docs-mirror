---
layout: Conceptual
title: Resource Performance Report - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/resource-performance
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: Use the resource performance report in Intune to analyze CPU and RAM trends, identify at-risk devices, and act on recommendations to improve user experience.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ccca926f-f713-3c04-6bd4-5d3e741462ee
document_version_independent_id: ccca926f-f713-3c04-6bd4-5d3e741462ee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/resource-performance.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/resource-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/resource-performance.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/72cb4d1c-66f7-4281-99d5-e04a64d084fc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d9ebaec0-4879-449e-9781-0afdce99fe0a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: eee24177-87c5-cf4a-3a85-3852ba7e10f8
---

# Resource Performance Report - Microsoft Intune | Microsoft Learn

The resource performance report gives you a clear view of processor and memory performance on Windows devices and how these factors affect user experience. By tracking the performance score, you can spot emerging hardware issues that may reduce productivity and take proactive steps before support tickets occur.

The report also provides actionable insights—showing how much your score could improve by upgrading CPU or RAM and helping you identify devices for replacement before warranties expire.

## Before you begin

- Review [Scores, baselines, and insights in endpoint analytics](../endpoint-analytics/scores) to understand these concepts.
- Confirm that your environment meets all [prerequisites](./#prerequisites).

### Additional requirements

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> This report supports the following platforms:
> 
> - Windows
> - Windows 365 Cloud PCs
> 

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> If your organization has Windows 365 licenses, you also get access to the resource performance report for your Cloud PCs.

## Review the report

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Endpoint analytics** &gt; **Resource performance**.

[![Screenshot of the resource performance report with overall score, CPU and RAM spike time breakdown, 28-day trend, and prioritized recommendations.](media/resource-performance/score-breakdown-and-trends.png)](media/resource-performance/score-breakdown-and-trends.png#lightbox)

### Resource performance score

The resource performance score provides an overall performance rating (from 0 to 100) of CPU and RAM for your organization's Windows devices and Cloud PCs. This score is a weighted average of CPU spike time score and RAM spike time score.

This score helps identify device resources that need to be replaced to improve user experience and boost productivity.

### CPU spike time score

The CPU spike time score (from 0 to 100) is assigned based on the device's usage duration and the CPU spike time %, which is the percentage of the usage duration in which the device experiences CPU spikes. High usage and spikes indicate a poor experience with the device and result in low scores. Conversely, low spikes indicate a good experience with the device and result in high scores.

**CPU spike time %**: The daily metric trends graph plots the ratio of CPU spike times to total usage time. This CPU spike % data is averaged over a 14-day period ending on the date at the bottom of the graph.

Usage over 50% is considered a spike.

- To improve the performance of CPU in Windows devices, you could upgrade the processors by increasing the number of cores or the clock speed, optimize the operating system or adjust power settings.
- To improve the performance of CPU in Cloud PCs, you could upgrade to a higher configuration of Cloud PCs.

### RAM spike time score

The RAM spike time score (from 0 to 100) is assigned based on the device's usage duration and the RAM spike time %, which is the percentage of the usage duration in which the device experiences RAM spikes. High usage and spikes indicate a poor experience with the device and result in low scores. Conversely, low spikes indicate a good experience with the device and result in high scores.

**RAM spike time %**: The daily metric trends graph plots the ratio of RAM spike times to total usage time. This RAM spike % data is averaged over a 14-day period ending on the date at the bottom of the graph. Usage over 75% is considered a spike.

- To improve the performance of RAM in Windows physical devices, you could add more RAM, upgrade to higher-speed RAM, or modify UEFI/BIOS settings to optimize utilization.
- To improve the performance of RAM in Cloud PCs, you could upgrade to a higher configuration of Cloud PCs.

**Baseline** helps you see if you're meeting goals. You can set the baseline to the organizational median or a custom value.

### Insights and recommendations

The report provides a prioritized list of insights and recommendations to help improve your score.

#### Cloud PCs

Windows 365 Cloud PCs with higher CPU or RAM spike percentages than the organizational average can degrade user experience. Upgrading these Cloud PCs to a higher configuration can improve performance and productivity.

#### High CPU usage on physical devices

Windows physical devices with higher CPU spike percentages than the organizational average can lead to poor user experience and reduced productivity.

- Individual devices with high CPU spike %.
- Device models with high CPU spike %.

#### High RAM usage on physical devices

Windows physical devices with higher RAM spike percentages than the organizational average can also impact performance and productivity.

- Individual devices with high RAM spike %.
- Device models with high RAM spike %.

## Report tabs

The report is organized into tabs, each providing a different view of related data and insights.

### Model performance

Displays CPU and RAM performance metrics and scores by device model. Use this view to determine if issues are isolated to specific models.

### Device performance

Shows CPU and RAM performance metrics and scores for all Windows physical devices and Cloud PCs.

- Sort by a specific metric (for example, CPU spike time %) to identify devices with the lowest scores.
- Filter devices by a metric range (for example, RAM spike time score between 0 and 40). Search for a device by name.
- Select a device to get device-level details, including CPU and RAM spike time history over the last 14 days. The page also includes device details such as model, manufacturer, processor name, number of processor cores, the processor base speed, RAM, and disk type.

## Limitations

- Some data points in the report might show `--` when not available. When you export the report, data points that aren't available appear as `-1` in the generated .csv file.
- Health status appears differently in the report and the exported .csv

    - **HealthStatus .csv value**:
        - `0`: Unknown
        - `1`: Insufficient data
        - `2`: Needs attention
        - `3`: Meeting goals
- Some columns such as `ResourcePerfScore` and `TotalRamInMB` in the generated .csv file have data type *double* whereas the corresponding columns **Resource performance score** and **RAM** in the report have data type *int*.
- Column `MachineType` in the generated .csv file can take values `Physical`, `CPC`, and `Others` whereas the corresponding column **Device Type** in the report takes values *physical*, *virtual*, and *unknown* respectively.

## Best practices

- IT administrators should periodically review the resource performance dashboard, to investigate poor performing devices from CPU or RAM spikes.
- Identify cohorts of devices, either hardware type, or by groups of users, with poor performance.
- Investigate performance issues and resolutions before users report persistent problems. Use the Device Timeline and Device Query capabilities to find the root cause of issues.
- Leverage performance data to optimize hardware replacement costs, extending the life of devices with no performance problem, or replacing underperforming devices sooner for improved user experience.