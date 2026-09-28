---
layout: Conceptual
title: Advanced Analytics Overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: Discover what Microsoft Intune Advanced Analytics is, how it extends endpoint analytics with advanced device insights, proactive troubleshooting, and enhanced reporting.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 6602b05a-a917-ac87-b729-93e442a2187f
document_version_independent_id: 6602b05a-a917-ac87-b729-93e442a2187f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 63588776-b4fb-74a4-c31d-e62639c04a9e
---

# Advanced Analytics Overview - Microsoft Intune | Microsoft Learn

Microsoft Intune Advanced Analytics delivers deep, actionable insights into the health and performance of your organization's endpoints. Built on the foundation of [endpoint analytics](../endpoint-analytics/), it helps IT teams proactively manage user experience and optimize productivity through data-driven intelligence. By turning raw telemetry into meaningful insights, Advanced Analytics reduces support costs, accelerates problem resolution, and ensures a more reliable technology experience for every user.

## Available reports and capabilities

Advanced Analytics enhances endpoint analytics with the following reports and capabilities:

> 
> Identifies CPU and RAM performance issues by device, model, and manufacturer to guide purchasing decisions.

> 
> Monitors battery health for Windows devices to ensure long battery life and a better user experience.

> 
> Tracks device health for regressions in user experience and productivity after configuration changes.

> 
> Shows detailed events with low latency to help troubleshoot device issues quickly.

> 
> Provides near real-time data about the state and configuration of Windows devices.

> 
> Allows you to run queries directly in Intune to retrieve inventory data across multiple devices and platforms.

> 
> Allows you to use scope tags to filter reports for a subset of devices. See scores, insights, and recommendations specific to those devices.

## Prerequisites

To use Advanced Analytics features, devices must meet the [endpoint analytics prerequisites](../endpoint-analytics/#prerequisites) and you must [configure endpoint analytics](../endpoint-analytics/configure) in your tenant.

This section details **additional prerequisites** specific to Advanced Analytics. Certain features may have their own additional prerequisites; see the individual feature articles for more information.

![](../media/icons/16/cloud.svg)**Cloud requirements**

> 
> - Public cloud
> - Sovereign cloud environments:
>     - U.S. Government Community Cloud (GCC) High
>     - U.S. Department of Defense (DoD)
> 
> 
>     Note
> 
>     Support for Advanced Analytics in DoD environments doesn't include the [*Device query*](device-query) functionality or the [*Resource performance*](resource-performance) report. For more information, see [Microsoft Intune for US Government GCC service description](../fundamentals/government-service).
> 

![](../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> Advanced Analytics features support Windows devices that are:
> 
> - Managed by Intune
> - Co-managed (Intune + Configuration Manager)
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> This feature requires a subscription in addition to Microsoft Intune Plan 1 or Plan 2. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

## Get started with Advanced Analytics

Before deploying Advanced Analytics, complete these foundational tasks:

- Assess your organization's privacy and compliance requirements for device data. Review the Intune [data platform schema](ref-data-platform-schema) to understand which data is captured.
- Define escalation and support procedures for handling analytics findings.
- Train staff on IT processes you plan to optimize, such as help desk triage, hardware refresh cycles, and app updates. Treat this as a continuous improvement cycle for faster and more proactive issue resolution.

### Enable Advanced Analytics

When license requirements are met, then Advanced Analytics capabilities are automatically enabled in your tenant.

Note

It might take up to 48 hours after you buy licenses or start a trial to see Advanced Analytics features in your tenant.

For the extra reports and capabilities on Windows devices:

- Devices must be enrolled in Intune and onboarded to endpoint analytics.
- [Device query for multiple devices](device-query-multiple-devices) requires a properties catalog policy to be configured and deployed.

### Advanced Analytics in the Intune admin center

Advanced Analytics is built into Microsoft Intune and appears in the **Reports** &gt; **Endpoint analytics** section, as well as other areas of the Intune admin center. When enabled, it adds the following enhancements:

- Endpoint analytics reports are extended with:
    - [Resource performance report](resource-performance)
    - [Battery health report](battery-health)
    - [Anomalies report](anomalies)
    - [Device scopes](device-scopes)
- Single device views are extended with:
    - [Battery health report](battery-health)
    - [Device timeline report](device-timeline), which replaces the [application reliability report](../endpoint-analytics/app-reliability)
    - [Resource performance report](resource-performance)
    - [Device query](device-query)
- Additional capabilities:
    - [Device query for multiple devices](device-query-multiple-devices) under the **Devices** node in the Intune admin center
    - [STIG audit baseline](../device-security/security-baselines/stig-audit-baseline) to assess Windows device compliance against Department of Defense (DoD) Security Technical Implementation Guide requirements

### Integrate Advanced Analytics into business processes

After completing the setup tasks, follow these steps to embed Advanced Analytics into daily operations:

1. **Update support processes**to:
    - Use the [device timeline report](device-timeline) to identify patterns, such as restarts or updates linked to anomalies.
    - Use [device query](device-query) to retrieve live device data for troubleshooting.
    - Use [device query for multiple devices](device-query-multiple-devices) to gain insights across your entire device fleet.
2. **Schedule regular reviews**of:
    - [Anomalies reports](anomalies) after OS or app updates to catch issues early.
    - [Battery health reports](battery-health) to identify devices needing attention for better performance and user experience.
    - [Resource performance reports](resource-performance) to track performance by device, model, and manufacturer—helpful for future purchasing decisions.