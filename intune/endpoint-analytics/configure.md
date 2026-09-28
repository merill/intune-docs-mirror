---
layout: Conceptual
title: Configure Endpoint Analytics - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: endpoint-analytics
description: Step-by-step guide to configure endpoint analytics in Microsoft Intune, enroll devices, and manage data collection policies for device insights.
ms.date: 2025-10-09T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: manage-intune-cm
locale: en-us
document_id: b4b631eb-b686-02b9-433f-5a337043ae14
document_version_independent_id: b4b631eb-b686-02b9-433f-5a337043ae14
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/endpoint-analytics/configure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: endpoint-analytics/configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/endpoint-analytics/configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 77b5cf9d-3f60-a29a-73ac-14d4a4d71bdf
---

# Configure Endpoint Analytics - Microsoft Intune | Microsoft Learn

::: zone pivot="intune"

Configure endpoint analytics in Intune by creating a data collection policy and adjusting settings that define your analytics experience.

::: zone-end

::: zone pivot="cm"

Configure endpoint analytics in Configuration Manager by enabling data upload, turning on data collection for devices. Then, adjust settings in the Intune admin center that define your analytics experience.

**Co-managed devices:** We recommend using Intune for configuration. For details, see [Configure endpoint analytics with Intune](?pivots=intune). You don't need to shift co-management workloads to Intune. When co-management is enabled, enrolled devices automatically send the required functional data to the Microsoft cloud.

::: zone-end

## Before you begin

- Confirm that your environment meets all prerequisites. For details, see [Prerequisites overview](./#prerequisites).

::: zone pivot="cm"

## Enable data upload in Configuration Manager

To enable data upload for endpoint analytics in Configuration Manager:

1. In the Configuration Manager console, go to **Administration** &gt; **Cloud Services** &gt; **Cloud Attach**.
2. Select **CoMgmtSettingsProd** then select **Properties**.
3. On the **Configure upload** tab, check the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager**.

Important

When you enable endpoint analytics data upload, your default client settings are automatically updated to allow managed endpoints to send relevant data to your Configuration Manager site server. If you use custom client settings, you might need to update and re-deploy them for data collection to occur.

[![Enable endpoint analytics for devices uploaded to Microsoft Endpoint Manager](media/configure/configure-upload-configmgr.png)](media/configure/configure-upload-configmgr.png#lightbox)

## Configure data collection client settings

The **Enable Endpoint analytics data collection** client setting lets managed devices send data required for endpoint analytics to your site server. This setting only controls local data collection—it doesn't determine whether data is uploaded to the cloud.

By default, this setting is enabled for devices targeted by the default client settings. For more information, see [About client settings in Configuration Manager](../configmgr/core/clients/deploy/about-client-settings). To change this behavior:

1. In the Configuration Manager console, go to **Administration** &gt; **Client Settings** &gt; **Default Client Settings**.
2. Right-click and select **Properties** then select the **Computer Agent** settings.
3. Set **Enable Endpoint analytics data collection** to **Yes** to configure devices for local data collection. Set to **No** to disable local data collection.

You can also modify the **Enable Endpoint analytics data collection** policy in custom client settings to configure a specific set of devices for local data collection. Don't forget to deploy or re-deploy your custom client setting after making changes.

Important

If you have an existing custom client agent setting that is deployed to your devices, you need to update the **Enable Endpoint analytics data collection** option in that custom setting and select **Ok** for it to take effect. For more information about this setting, see [Data collection settings](ref-data-collection#data-collection).

::: zone-end

## Enable endpoint analytics

When you open Endpoint analytics for the first time, a guided setup helps you configure data collection. As part of this process, Intune creates a *Windows health monitoring policy* to enable data collection.

1. In the [Microsoft Intune admin center], select [**Reports**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_ReportsMenu/%7E/overview).
2. Under **Analytics**, select [**Endpoint analytics**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Enrollment/ReportingMenu/%7E/uxAnalytics). [![Endpoint analytics introduction page.](media/configure/introduction.png)](media/configure/introduction.png#lightbox)
3. For **Collect device data from**, choose from the following options:
    - **All cloud-managed devices**: Assigns the policy to all Windows devices that are Intune-managed or co-managed.
    - **Selected devices**: Assigns the policy only to devices you select.
    - **I'll choose later**: Doesn't assign the policy now.
4. Select **Start**.

A configuration profile called *Intune data collection policy* is assigned to the targeted devices, which instructs the devices where to send the data.

::: zone pivot="cm"

Note

The Intune data collection policy is required for Intune-managed and co-managed devices. Devices managed solely by Configuration Manager don't need this policy assigned because data collection is controlled by Configuration Manager client settings.

::: zone-end

::: zone pivot="intune"

### Change the assignment of the Intune data collection policy

If you want to change which devices contribute data to endpoint analytics, you can change the assignment of the Intune data collection policy.

1. In the [Microsoft Intune admin center], select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**Configuration**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/configuration).
2. Select the profile named **Intune data collection policy**.
3. Select **Properties** &gt; **Assignments** &gt; **Edit**.
4. Change the assignment to include or exclude groups of devices.

You can also create a new profile if you want to target a different set of devices:

1. Create a Windows health monitoring policy. For instructions, see [Configure Windows health monitoring](../device-configuration/templates/configure-health-monitoring-windows).
2. Assign the policy to a group that contains as members the devices that you want to target.

::: zone-end

## Review data collection and sharing settings

To review the current configuration of endpoint analytics:

1. In the [Microsoft Intune admin center], select [**Reports**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_ReportsMenu/%7E/overview).
2. Under **Analytics**, select [**Endpoint analytics**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Enrollment/ReportingMenu/%7E/uxAnalytics). [![Endpoint analytics general settings page.](media/configure/settings.png)](media/configure/settings.png#lightbox)
3. From the **General** pane you can review if the Intune data collection policy is configured and if the Configuration Manager data collection is enabled.

### Consent to share data

When you share anonymized data and aggregate metrics, your organization helps keep the *All organizations (median)* baseline current.

You can revoke consent to share this data at any time. Before revoking consent, consider the impact on your reports and insights:

- Reports that rely on shared data—such as startup performance insights—are disabled.
- Existing report data becomes stale immediately, and no new data is added.
- Historical data remains visible for up to 60 days, after which it's removed.

To revoke consent:

1. Clear the checkbox that states **I consent to share anonymized and aggregate metrics to see updated Endpoint analytics scores and insights**.
2. Select **Yes** to confirm the action.
3. Optionally, stop gathering data. For instructions, see [How to stop data collection](ref-data-collection#stop-gathering-data).

## Configure baselines

Baselines help you compare your performance to industry norms or track progress using your own metrics.

To create a custom baseline and adjust the regression threshold:

1. In the [Microsoft Intune admin center], select [**Reports**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_ReportsMenu/%7E/overview).
2. Under **Analytics**, select [**Endpoint analytics**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Enrollment/ReportingMenu/%7E/uxAnalytics).
3. Select **Settings** &gt; **Baseline**. [![Endpoint analytics baseline settings page.](media/configure/settings-baseline.png)](media/configure/settings-baseline.png#lightbox)
4. Select **Create new** and enter a name. 
    Tip

    Include the date in the name for easier selection from the drop-down in reports.
5. Metrics are flagged red and marked as *regressed* if they fall below the current baseline. Because daily fluctuations are normal, set a **regression threshold** (default is 10%) so metrics are only flagged when they regress by more than the percentage you specify.

You can create up to 20 baselines per tenant. Delete old baselines when they're no longer needed.

## Review collected data

After devices receive the data collection policy, they begin sending data to endpoint analytics. The service processes and calculates the data before displaying results. It can take up to **24 hours after a restart** for data to appear in reports.

For startup performance metrics, devices must restart at least once.

To learn more about how data flows and is collected from devices to the Microsoft cloud, see [Data flow](ref-data-collection#data-flow).

When processing is complete, the **Overview** page updates with your organization's data:

- The **Endpoint analytics score** is a weighted average of the Startup performance, Application reliability, and Work from anywhere scores. For details, see [Startup performance](startup-performance), [Application reliability](app-reliability), and [Work from anywhere](work-from-anywhere).
- You can compare your current score to other scores by selecting a baseline.
    - Baseline markers are shown for your overall score and subscores. If any of the scores have regressed by more than the configurable threshold from the selected baseline, the score is displayed in red and the top-level score is flagged as needing attention.
    - A status of **insufficient data** means you don't have enough devices reporting to provide a meaningful score. We currently require at least five devices.
- **Insights and recommendations** is a prioritized list to improve your score. This list is filtered to the subnode's context when you navigate.

[![Screenshot of the endpoint analytics overview page.](media/shared/overview.png)](media/shared/overview.png#lightbox)