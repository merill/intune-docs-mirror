---
layout: Conceptual
title: Security update status dashboard - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-update-status-dashboard
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: sccmavenger
ms.author: dannygu
ms.subservice: protect
description: Learn how the Security update status dashboard helps administrators assess update risk, investigate gaps, and prioritize remediation across supported workloads.
ms.reviewer: paoloma
ms.topic: concept-article
ms.date: 2026-06-15T00:00:00.0000000Z
locale: en-us
document_id: a1543c9c-b1a2-37a6-5af9-60b23209dcf9
document_version_independent_id: a1543c9c-b1a2-37a6-5af9-60b23209dcf9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-update-status-dashboard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-update-status-dashboard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-update-status-dashboard.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
platformId: 9b3ba66b-b67a-3d6e-32d0-ad050c8da098
---

# Security update status dashboard - Microsoft Intune | Microsoft Learn

The Security update status dashboard provides a fleet-wide view of security update currency across Windows client devices, Windows Server devices, and Microsoft 365 Apps. It helps administrators assess exposure, identify where segments of their fleet are not current on required security updates, and prioritize remediation across workloads based on relative risk.

At a high level, the dashboard answers one core question: **Where am I at risk?** It gives a concise summary of update posture. Use it as a starting point for triage and situational awareness, not for root-cause analysis.

[![Screenshot of the Security update status dashboard showing Windows client, Windows Server, and M365 applications compliance tiles.](media/security-update-status-dashboard/dashboard.png)](media/security-update-status-dashboard/dashboard.png#lightbox)

## Prerequisites

![](../media/icons/16/cloud.svg)**Cloud requirements**

> 
> This feature is supported in the public cloud environment only.

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To view the dashboard, use an account with at least the permission [Organization/Read](/en-us/intune/fundamentals/role-based-access-control/create-custom-role#organization) in Intune role-based access control. Grant this access through a built-in Intune role or through a [custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role).

![](../media/icons/16/data-sources.svg)**Data sources requirements**

> 
> The dashboard can draw from multiple Microsoft management and reporting systems to provide a unified view of update posture across workloads. Depending on the workload, sources can include Microsoft Intune, Microsoft Configuration Manager through tenant attach, Microsoft Defender for Endpoint, the Microsoft 365 Apps admin center, and supporting application or device telemetry.
> 
> Source-specific prerequisites apply and vary by workload:
> 
> - **Windows clients:**
>     - **Intune-managed devices:** Intune enrollment and the required reporting path for update data.
>     - **Configuration Manager-managed devices:** Co-management or another supported cloud-connected reporting configuration.
> - **Microsoft 365 Apps:** Onboard to the Microsoft 365 Apps admin center, with the required inventory and service connectivity enabled.
> - **Windows Server:** A supported cloud-connected path, such as tenant attach or MDE related onboarding.
> 
> 
> Validate requirements per workload before relying on the dashboard for operational decisions.

## How to access the dashboard

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**Monitor**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/monitor).
2. Select [Security update status](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_ManagedDevices/SecurityUpdateStatus.ReactView) to open the dashboard.

## What the dashboard shows

The dashboard is organized around workload tiles that summarize update status and risk across major product areas. The primary workloads are Windows client, Windows Server, and Microsoft 365 Apps.

- Risk level, such as **Current**, **Exposed**, or **Critical**
- Status distribution across device states
- Total device count
- Last updated timestamp for the report data shown in the tile, reflecting the dashboard refresh that occurs every six hours
- A breakdown of device state categories
- An action entry point, such as **Get current**, to initiate update actions and remediation

Color-coding is used to quickly communicate status: green indicates *Current*, orange indicates *Exposed*, red indicates *Critical*, and gray indicates an unknown or inactive state. Devices that don't check in for 90 days or more appear outside the primary status calculation so that stale data doesn't distort active risk reporting.

## Status definitions

The dashboard groups devices into status categories that represent how current these devices are relative to expected security update baselines.

| Icon | Risk level | Description |
| --- | --- | --- |
| ![check-icon](../media/icons/16/check.svg) | **Current** | Devices have the latest applicable security update installed, or are on the previous update within the short grace period immediately after a new release. |
| ![caution-icon](../media/icons/16/caution.svg) | **Exposed** | Devices are behind the latest applicable security update and moved beyond the initial grace period. In general, this status begins after roughly the first three days following a newly applicable update release. |
| ![error-icon](../media/icons/16/error.svg) | **Critical** | Devices are missing required updates long enough to represent materially higher risk. In general, devices that remain behind for a week or longer can move into this state, and unsupported versions are also treated as critical risk. |
| ![question-icon](../media/icons/16/question.svg) | **Unknown build** | The reported device version can't be mapped to a known supported release or update baseline. |
| ![circle-icon](../media/icons/16/circle.svg) | **Not checked in (90+ days)** | The device didn't report recently and is excluded from primary risk calculations to keep the dashboard focused on active fleet posture. |

After a newly released security update becomes applicable, devices on the previous update may remain classified as *Current* for a short period so the dashboard reflects normal deployment propagation instead of immediately treating the entire fleet as newly at risk.

## Risk levels

Use the distribution of devices across *Current*, *Exposed*, and *Critical* states to determine an overall risk level for each workload. This level isn't tracked in the dashboard and should be defined by the organization and its security posture to inform prioritization. These levels provide a fast, high-signal indicator of where administrators should focus first.

- **Low risk:** At least 85% of devices are *Current*.
- **Medium risk:** 51% to 84% of devices are *Current*.
- **High risk:** 50% or fewer devices are *Current*.

Risk level simplifies prioritization; it doesn't replace deeper investigation. A medium- or high-risk tile should lead to follow-up reporting that explains which devices are affected, why they're behind, and whether the cause is deployment timing, reporting latency, onboarding gaps, or unsupported versions.

## Why Windows Autopatch reporting matters

The dashboard shows where risk exists, but additional reporting often explains why devices are behind and what remediation path is most appropriate. Devices can appear as Exposed or Critical for several reasons beyond simply missing an update: a device might not be targeted by the intended policy, might be delayed by deployment settings, or might not be reporting as expected.

Windows Autopatch reporting helps administrators move from a summary of risk to a clearer view of policy alignment, coverage, and update management status. For supporting guidance, see:

- [Windows Autopatch update readiness overview](/en-us/windows/deployment/windows-autopatch/monitor/windows-autopatch-update-readiness-overview)
- [Windows Autopatch management status report](/en-us/windows/deployment/windows-autopatch/monitor/windows-autopatch-management-status-report)
- [Windows quality and feature update reports overview](/en-us/windows/deployment/windows-autopatch/monitor/windows-autopatch-windows-quality-and-feature-update-reports-overview)

Devices can also appear as Exposed or Critical during an active phased rollout. The dashboard reflects exposure based on update currency, not whether your deployment schedule is proceeding as planned. Rollout rings and staged deployment strategies aren't modeled directly in the dashboard state.

## Example workflow

To investigate and reduce risk surfaced by the dashboard:

1. Review the Security update status dashboard and identify the workload with the highest risk.
2. Open Windows Autopatch or Intune reporting to investigate the affected device populations.
3. Review quality update, feature update, or app update compliance details.
4. Analyze policy targeting and assignment coverage.
5. Adjust update policies or remediation steps as needed.
6. Return to the dashboard to confirm that device currency improves as remediation continues.

## Limitations

- The dashboard reflects supported Microsoft workloads and doesn't include third-party update visibility.
- The dashboard is a snapshot view of current posture. It doesn't model rollout rings or staged deployment logic directly.
- You can't remediate from the dashboard. Use the underlying management tools, such as Intune or Configuration Manager.
- The dashboard doesn't provide historical trend tracking.
- The dashboard is an aggregate estate view and might not honor every filtering expectation used in other reporting experiences.