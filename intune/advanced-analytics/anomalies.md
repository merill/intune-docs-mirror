---
layout: Conceptual
title: Anomalies Report for Proactive Device Issue Detection - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/anomalies
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: Use the anomalies report in Advanced Analytics to monitor device health, identify issues early, and prioritize fixes to improve endpoint reliability.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 933f4d19-9af7-5e52-a398-56fa95e29cc7
document_version_independent_id: 933f4d19-9af7-5e52-a398-56fa95e29cc7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/anomalies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/anomalies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/anomalies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: a53c3bcb-838e-e0f0-f20d-80335290f353
---

# Anomalies Report for Proactive Device Issue Detection - Microsoft Intune | Microsoft Learn

The anomalies report in Advanced Analytics helps IT admins proactively identify device health issues before they affect users. It monitors for application hangs, crashes, and Stop Error Restarts, providing visibility into problems before they reach support channels.

The feature correlates deployment objects and configuration changes to speed troubleshooting and suggest root causes. Device correlation groups reveal patterns among affected devices and flag others that are at risk.

## Before you begin

- Review [Scores, baselines, and insights in endpoint analytics](../endpoint-analytics/scores) to understand these concepts.
- Confirm that your environment meets all [prerequisites](./#prerequisites).

## Review the report

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Endpoint analytics** &gt; **Overview**.
2. Select the **Anomalies** tab, which provides an overview of the anomalies detected in your organization.

[![Screenshot of the anomalies report with severity counts and a list of detected anomalies, including status, affected devices, and occurrence dates.](media/anomalies/severity-summary-and-anomaly-list.png)](media/anomalies/severity-summary-and-anomaly-list.png#lightbox)

- Use sorting and filtering capabilities to refine the list of anomalies.
- To view more information about a specific anomaly, select it from the list. Review details such as the app name, affected devices, when the issue was first detected and last occurred, and any device groups that might be contributing to the problem. [![Screenshot of the anomaly details pane with severity, state, affected devices, detection dates, analytics model, and device correlation groups.](media/anomalies/anomaly-detail-and-correlation-groups.png)](media/anomalies/anomaly-detail-and-correlation-groups.png#lightbox)
- Select a device correlation group from the list to see common factors among devices. Devices are correlated by shared attributes such as app version, driver update, OS version, or device model. You can view the number of devices currently affected and those at risk. The **prevalence rate** shows the percentage of affected devices in a correlation group. [![Screenshot of an expanded device correlation group with common factors such as app version and publisher, plus prevalence and an affected devices link.](media/anomalies/correlation-group-common-factors.png)](media/anomalies/correlation-group-common-factors.png#lightbox)
- Select **View Affected Devices** to display a list of devices with key attributes. Filter to view devices in specific correlation groups or show all devices affected by the anomaly. The device timeline also shows additional anomalous events. [![Screenshot of the affected devices list filtered by correlation group, showing device name, status, manufacturer, model, OS version, and occurrence dates.](media/anomalies/affected-devices.png)](media/anomalies/affected-devices.png#lightbox)

## Review anomaly detection data

Investigate flagged device correlation groups using the device timeline and resource reports to determine root causes. Device correlation groups help identify root causes for high and medium severity anomalies, as well as at-risk devices that may be impacted in the future.

**Best practices:**

- Periodically review the anomalies dashboard to understand the current baseline and prioritize investigations and resolutions for new issues.
- Investigate new reported issues to identify common factors, such as device hardware, as shown in advanced analytics.
- Prioritize anomalies to investigate based on severity and internal knowledge, such as application criticality.
- Use the [device timeline](device-timeline) report to check for patterns, such as device restarts or updates tied to anomalies.
- Work with IT teams to identify other factors, such as recent application updates, that could impact anomalies.
- Review possible remediation actions noted in the anomaly report (for example, driver or application updates).
- Integrate resolutions into L1/L2 support to keep teams aware of current known issues. Consider working with your ITSM team to record known anomalies under investigation.
- Test remediation actions on a subset of devices and monitor results before rolling out to more devices. After remediation, proactively roll out to at-risk devices.
- Review anomalies reports after major updates or incidents to check for new issues that need investigation and resolution.
- To better understand detection methods, review the statistical models used by anomaly detection.

## Statistical models for determining anomalies

The analytical model detects device cohorts facing anomalous sets of Stop Error Restarts and application hangs or crashes that need admin attention. Patterns identified from sensor telemetry and diagnostics logs determine these device cohorts.

- **Threshold-based heuristic model**: This model sets one or more threshold values for application hangs, crashes, or Stop Error Restarts. Devices are flagged as anomalous if they breach the set threshold. The model is simple and effective for surfacing prominent or static issues. Thresholds are currently predetermined and not customizable.
- **Paired t-tests model**: Paired t-tests compare pairs of observations in a dataset, looking for statistically significant differences between their means. For example, comparing Stop Error Restarts on the same device before and after a policy change, or app crashes after an OS update.
- **Population Z-score model**: This model calculates the standard deviation and mean of a dataset, then uses those values to determine which data points are anomalous. The Z-score for each data point represents the number of standard deviations from the mean. Data points outside a certain range are considered anomalous. This model is well suited for highlighting outlier devices or apps but requires large datasets to be accurate.
- **Time series Z-score model**: This variation of the Z-score model is designed for detecting anomalies in time series data—sequences of data points collected at regular intervals, such as Stop Error Restarts over time. Standard deviation and mean are calculated for a sliding window, allowing the model to adapt to temporal patterns and changes in data distribution.

Note

Device cohorts are only identified for medium and high-severity anomalies.