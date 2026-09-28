---
layout: Conceptual
title: Work From Anywhere Report in Endpoint Analytics - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/endpoint-analytics/work-from-anywhere
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: endpoint-analytics
description: Discover how the Work from Anywhere report in Microsoft Intune endpoint analytics provides insights into remote productivity, device readiness, and user experience.
ms.date: 2025-10-09T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: f96a9e91-3fe5-5ac5-802b-24fde788f988
document_version_independent_id: f96a9e91-3fe5-5ac5-802b-24fde788f988
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/endpoint-analytics/work-from-anywhere.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: endpoint-analytics/work-from-anywhere
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/endpoint-analytics/work-from-anywhere.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 9189acfe-8f4c-22e8-a194-2f214093e581
---

# Work From Anywhere Report in Endpoint Analytics - Microsoft Intune | Microsoft Learn

The work from anywhere report shows how ready your organization is for productive remote work. Use this report to review your scores, compare them to the selected baseline, and explore insights and recommendations to improve performance.

## Before you begin

- Review [Scores, baselines, and insights in endpoint analytics](scores) to understand these concepts.
- Confirm that your environment meets all [prerequisites](./#prerequisites).

## Review the report

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Reports** &gt; **Endpoint analytics** &gt; **Work from anywhere**.

[![Screenshot of the Work from anywhere report showing the scores and metrics](media/work-from-anywhere/overall-score.png)](media/work-from-anywhere/overall-score.png#lightbox)

### Work from anywhere score

The work from anywhere score is a number between 0 and 100. The score represents a weighted average of the percent of devices that have deployed the various insights for helping your end users be productive from anywhere. The score is computed for all active Intune and Configuration Manager devices that have opted into endpoint analytics.

Note

A device is considered active and will appear in the work from anywhere report if it has uploaded at least one endpoint analytics event, such as a boot, sign-in, or application crash event, in the past 29 days.

The following metrics are weighted and used to compute the **Work from anywhere score**:

- Windows
- Cloud management
- Cloud identity
- Cloud provisioning

Note

In the device-level views of Work from anywhere, admins will only see devices they have access to according to their assigned Scope tags. To learn more about Scope tags, see [Scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags). Aggregated insights, such as the Work from anywhere score, are calculated using all enrolled devices in the tenant. To apply Scope tags to aggregated insights, see [Device scopes in endpoint analytics](../advanced-analytics/device-scopes).

#### Windows

Newer versions of Windows provide a better user experience than older versions of Windows. The **Windows** metric measures the percent of devices on supported versions of Windows. The recommended remediation actions vary depending on how the devices are managed. For Intune and co-managed devices, use Intune to [move devices to an updated version of Windows](../device-updates/windows/manage-feature-updates). Your score is based on if these remediation actions have been completed or not.

[![Screenshot of the Windows fly out showing graph and insights](media/work-from-anywhere/windows-score.png)](media/work-from-anywhere/windows-score.png#lightbox)

#### Cloud management

Configuration Manager and Intune provide integrated cloud-powered management tools and unique co-management options to provision, deploy, manage, and secure endpoints and applications across an organization. With the power of cloud management, you can achieve several productivity benefits. Your end-users benefit when they can access corporate resources away from the corporate network. Eliminating the need for and performance overhead of Group Policy also results in a better end-user experience.

The **Cloud management** metric measures the percent of PCs that have attached to the Microsoft 365 cloud to unlock additional capabilities. There are multiple recommended actions for co-managed devices and their workloads, CMG, and tenant attached devices.

Benefits of each cloud management type:

| Benefits | [**Cloud management gateway (CMG)**](../configmgr/core/clients/manage/cmg/overview) | [**Tenant attach**](../configmgr/tenant-attach/device-sync-actions) | [**Co-management**](../configmgr/comanage/overview) | [**Intune**](../fundamentals/what-is-intune) |
| --- | --- | --- | --- | --- |
| Manage your clients anywhere | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| View and take action on all Windows PCs from Microsoft Intune admin center |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Modernize your directory approach with Microsoft Entra ID |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Enhance Zero Trust with Conditional Access |  |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Make device provisioning easier by enabling Windows Autopilot |  |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Gain more remote access with Intune |  |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Split PC management workloads between cloud and on-premises |  |  | ![](../media/icons/16/check.svg) |  |
| Simplify PC and driver updating with the cloud |  |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Consistent end-user experience for managing enrolled devices and installed apps |  |  | ![](../media/icons/16/check.svg) | ![](../media/icons/16/check.svg) |
| Reduce complexity with always up-to-date cloud only infrastructure | ![](../media/icons/16/check.svg) |  |  | ![](../media/icons/16/check.svg) |

#### Cloud identity

Cloud identity provides users with many productivity benefits including device-wide single sign-on to apps and services, Windows Hello sign-in, self-service BitLocker recovery, and corporate data roaming. The **Cloud identity** metric measures the percent of devices enrolled in Microsoft Entra ID or hybrid Microsoft Entra ID. Your Intune and co-managed devices are already enrolled in Microsoft Entra ID. The recommended remediation action for devices managed by Configuration Manager is to [enroll them in hybrid Microsoft Entra ID](/en-us/azure/active-directory/devices/hybrid-azuread-join-managed-domains).

[![Screenshot of the Cloud identity fly out showing insights for the metric](media/work-from-anywhere/cloud-identity.png)](media/work-from-anywhere/cloud-identity.png#lightbox)

#### Cloud provisioning

Cloud provisioning provides a simpler initial provisioning experience for Windows PCs than the native experience. It reduces the number of screens in the Out Of Box Experience (OOBE) and provides defaults, to ensure the device is correctly provisioning from the factory or on reset. The **Cloud provisioning** metric measures the percentage of machines that are either Windows 365 Cloud PCs or Windows Intune devices that are both registered and have a deployment profile created for Windows Autopilot.

Note

The **Autopilot profile assigned** metric indicates whether a Windows Autopilot deployment profile is assigned to the device. If a device inherits a default Windows Autopilot profile, it will not receive credit for having a deployment profile assigned. The Windows Autopilot Deployment profile becomes the default, when it is assigned to the All Devices security group. For more information, see [Windows Autopilot profile priority](/en-us/autopilot/profiles#windows-autopilot-profile-priority)

The recommended remediation actions are to register and create deployment profiles for existing devices in Windows Autopilot using Microsoft [Intune](/en-us/autopilot/enrollment-autopilot).

Note

Cloud provisioned devices that aren't enrolled into endpoint analytics won't be populated.

[![Screenshot of the cloud provisioning tab showing the device list](media/work-from-anywhere/cloud-provisioning.png)](media/work-from-anywhere/cloud-provisioning.png#lightbox)

## Windows 11 hardware readiness

The **Windows** metric provides Windows 11 hardware readiness insights for devices that are enrolled via Intune, co-management, or Configuration Manager version 2107 or newer with tenant attach enabled. To determine how many of your enrolled devices meet the [minimum system requirements](/en-us/windows/whats-new/windows-11-requirements#hardware-requirements) for Windows 11, select **Windows** to open the flyout on the **Overview** page in **Work from anywhere**. A chart is displayed showing which specific hardware requirements are the top blockers in your organization.

[![Screenshot of the Windows tab that displays a chart showing top hardware blockers in your organization and OS versions.](media/work-from-anywhere/windows-hardware.png)](media/work-from-anywhere/windows-hardware.png#lightbox)

In the **Windows** tab, a device-by-device view of Windows 11 hardware readiness is displayed. The **Windows 11 readiness status** column indicates whether a device is **Capable** or **Not capable** of upgrading to Windows 11 based on the minimum system requirements. The column also lists if a device is already **Upgraded** or if the status is **Unknown** for a device. The **Windows 11 readiness reason** column outlines the specific hardware requirements that aren't met for devices that have a readiness status of **Not capable**.

Note

- In most cases, devices with a Windows 11 readiness status of **Unknown** are inactive. To verify this, review the [last check in time](/en-us/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune) from Intune. If you see a large number of inactive devices in the report, consider adjusting your [device clean up rules](../governance/configure-cleanup-rules), or target only active devices with the [Intune data collection policy](configure) that controls endpoint analytics enrollment.
- Windows 11 hardware readiness insights do not impact your Work from anywhere score.

## No commercial median

The built-in baseline of **All organizations (median)** doesn't currently have metrics for the subscore metrics listed in this article.