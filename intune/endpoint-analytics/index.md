---
layout: Conceptual
title: Endpoint analytics overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/endpoint-analytics/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: endpoint-analytics
description: Discover how Microsoft Intune endpoint analytics provides actionable insights to optimize device performance, improve user experience, and enable proactive IT troubleshooting.
ms.date: 2025-11-26T00:00:00.0000000Z
ms.topic: overview
zone_pivot_groups: manage-intune-cm
locale: en-us
document_id: 395c65c8-2168-8307-e68c-fb52632d9e2d
document_version_independent_id: 395c65c8-2168-8307-e68c-fb52632d9e2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/endpoint-analytics/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: endpoint-analytics/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/endpoint-analytics/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: b113673f-5ea5-8f0b-ed50-52d269d083e6
---

# Endpoint analytics overview - Microsoft Intune | Microsoft Learn

Endpoint analytics helps IT professionals assess and improve the user experience across managed devices. It provides data-driven insights into device performance, startup times, app reliability, and battery health—empowering IT teams to proactively identify and remediate issues that impact productivity.

Endpoint analytics contributes to the technology experiences category within [Microsoft Adoption Score](/en-us/microsoft-365/admin/productivity/productivity-score), offering device-level insights that complement broader organizational productivity metrics.

The service integrates with Microsoft Intune, enabling IT pros to:

- Enroll devices directly from Intune.
- Use Configuration Manager for co-managed environments.
- Manage data collection and configuration.
- View analytics in the Intune admin center.
- Apply remediations or adjust policies based on insights.

[![Screenshot of the endpoint analytics overview page](media/shared/overview.png)](media/shared/overview.png#lightbox)

## Available reports

Endpoint analytics organizes insights into reports that highlight performance and reliability issues across managed devices. These reports help IT teams identify trends, diagnose problems, and implement improvements to enhance the overall user experience. Endpoint analytics includes the following reports:

> 
> Identifies devices with slow boot times and factors that delay startup.

> 
> Monitors app crashes and stability trends to improve user experience.

> 
> Evaluates device readiness for secure and efficient remote work.

> 
> Provides deeper insights and extended reporting capabilities (**requires additional licensing**).

## Prerequisites

To use endpoint analytics, ensure your environment meets the following prerequisites:

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Endpoint analytics supports the following Windows editions:
> 
> - Pro
> - Pro Education
> - Enterprise
> - Education
> 

![](../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> Endpoint analytics supports devices that are:
> 
> - Managed by Intune
> - Co-managed (Intune + Configuration Manager)
> - Managed by Configuration Manager (via tenant attach)
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 
> 
> Devices must also meet the following requirements:
> 
> - The **Connected User Experiences and Telemetry** service (DiagTrack) must be enabled and running.
> 

![](../media/icons/16/network-connectivity.svg)**Network and connectivity requirements**

::: zone pivot="intune"

> 
> To enroll Intune-managed devices to endpoint analytics, they need to send required functional data to Microsoft public cloud. Ensure the following endpoints are accessible from Intune-managed devices:
> 
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://*.events.data.microsoft.com` | Used by managed devices to send [required functional data](ref-data-collection#data-collection) to the Intune data collection endpoint. |
> 
> 
> For more information and troubleshooting proxy configurations, see [Troubleshoot endpoint analytics](troubleshoot#proxy-server-authentication).

::: zone-end

::: zone pivot="cm"

> 
> Configuration Manager-managed devices send data to Intune via the connector on the Configuration Manager role and they don't need directly access to the Microsoft public cloud. If your environment uses a proxy server, configure the proxy server to allow the following endpoints:
> 
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://graph.windows.net` | Used to automatically retrieve settings when attaching your hierarchy to endpoint analytics on Configuration Manager Server role. For more information, see [Configure the proxy for a site system server](../configmgr/&gt; core/plan-design/network/proxy-server-support.md#configure-the-proxy-for-a-site-system-server). |
> | `https://*.manage.microsoft.com` | Used to synch device collection and devices with endpoint analytics on Configuration Manager Server role only. For more information, see [Configure the proxy for a site system server](../configmgr/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server). |
> 
> 
> If you have co-management enabled, enrolled devices send required functional data directly to Microsoft public cloud. In this case, ensure the following endpoints are accessible from co-managed devices:
> 
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://*.events.data.microsoft.com` | Used by managed devices to send [required functional data](ref-data-collection#data-collection) to the Intune data collection endpoint. |
> 
> 
> For more information and troubleshooting proxy configurations, see [Troubleshoot endpoint analytics](troubleshoot#proxy-server-authentication).

::: zone-end

![](../media/icons/16/licensing.svg)**Licensing requirements**

::: zone pivot="intune"

> 
> Devices enrolled in endpoint analytics need a valid license for the use of Microsoft Intune. For more information, see [Microsoft Intune licensing](../fundamentals/licensing).

::: zone-end

::: zone pivot="cm"

> 
> Devices enrolled in endpoint analytics need a valid license for the use of Microsoft Intune. For more information, see [Microsoft Configuration Manager licensing](../configmgr/core/understand/learn-more-editions).

::: zone-end

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> Role requirements vary based on whether you're configuring endpoint analytics or reviewing the data.
> 
> To [configure endpoint analytics](configure), you need an account with at least one of the following Intune roles:
> 
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator): Grants read/write permissions to endpoint analytics.
> - A [custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - **Endpoint Analytics/Read** — View scores and performance reports.
>     - **Endpoint Analytics/Create, Update, Delete** — Manage settings and baselines.
>     - **Organization/Read** and **Managed Devices/Read** — Required for device visibility.
>     - **Device configurations/Create, Read, Assign** — Required to create and assign the data collection policy
> 
> 
> To [access endpoint analytics reports](scores), you need an account with at least one of the following Intune roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator): Grants read permissions to endpoint analytics.
> - [Read Only Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator): Grants read permissions to endpoint analytics.
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager): Grants read permissions to endpoint analytics.
> - [School Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator): Grants read/write permissions to endpoint analytics.
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - **Endpoint Analytics/Read** — View scores and performance reports.
>     - **Organization/Read** and **Managed Devices/Read** — Required for device visibility.
> 
> 
> You can also use an account that has the following Microsoft Entra built-in roles:
> 
> - [Reports Reader](/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader): Grants read permissions to endpoint analytics.
> 

::: zone pivot="cm"

## Configuration Manager requirements

To use endpoint analytics, your environment must have [tenant attach](../configmgr/tenant-attach/device-sync-actions) enabled. Tenant attach connects Configuration Manager to Intune, allowing you to manage devices from the Intune admin center and perform actions such as device sync and remote tasks.

Note

Using multiple Configuration Manager hierarchies with a single endpoint analytics instance isn't supported.

::: zone-end