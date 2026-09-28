---
layout: Conceptual
title: Microsoft Intune architecture - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/architecture
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- triage
ms.subservice: fundamentals
description: Reference architecture for a Microsoft Intune deployment, including cloud and on-premises components and Microsoft and third-party integrations.
ms.date: 2026-05-12T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: davidra
locale: en-us
document_id: ec3d8a8e-31d9-e524-948d-df4ecd6d2de3
document_version_independent_id: ec3d8a8e-31d9-e524-948d-df4ecd6d2de3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/architecture.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/architecture.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: eb7705ca-6904-703b-e4ad-fd77b2003bd1
---

# Microsoft Intune architecture - Microsoft Intune | Microsoft Learn

This article describes the architecture of a Microsoft Intune deployment: the cloud and on-premises components and the Microsoft and third-party products Intune integrates with.

For an introduction to what Intune does, see [What is Microsoft Intune?](what-is-intune). For a conceptual walkthrough of how Intune manages identities, devices, and apps, see [Microsoft Intune core concepts](core-concepts).

[![Diagram that shows Microsoft Intune in a reference architecture with Microsoft Entra, Microsoft 365, Configuration Manager, on-premises connectors, and managed endpoints.](media/architecture/intune-reference-architecture.png)](media/architecture/intune-reference-architecture.png#lightbox)

The diagram organizes a typical Intune deployment into seven tiers:

1. **Cloud control plane**: Microsoft-hosted Intune services.
2. **Managed endpoints**: devices that Intune manages.
3. **Endpoint family services**: Microsoft products whose primary purpose is endpoint management.
4. **Connectors and extensions**: cloud-based external services Intune integrates with.
5. **Peer integrations**: other Microsoft products that integrate with Intune.
6. **Partner ecosystem**: third-party products and services that integrate with Intune.
7. **On-premises services**: customer-operated infrastructure that integrates with the Intune cloud.

Each tier is described in the following sections.

## Cloud control plane

The cloud control plane is the set of Microsoft-hosted services that constitute the Intune tenant. They store configurations, deliver policy, expose programmatic interfaces, and surface the admin and user experiences.

[![Diagram of the cloud control plane.](media/architecture/cloud-control-plane.png)](media/architecture/cloud-control-plane-on.png#lightbox)

| Component | Role |
| --- | --- |
| **Microsoft Intune service** | The cloud control plane that stores configurations and orchestrates policy delivery. |
| **[Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431)** | Web console for administrators. |
| **[Microsoft Graph API](/en-us/graph/intune-concept-overview)** | Public programming interface. Every admin center action is backed by a Graph API call. |
| **[Microsoft Intune Company Portal app and website](../app-management/configuration/configure-company-portal)** | User-facing surface that enrolls devices, surfaces required apps, and shows compliance status. |

## Managed endpoints

Intune supports the following platforms: Android, iOS, iPadOS, Linux, macOS, tvOS, visionOS, and Windows. Specialty scenarios include kiosks, frontline devices, and rugged hardware managed through platform-specific enrollment paths.

[![Diagram of managed endpoints as they relate to the cloud control plane.](media/architecture/managed-endpoints.png)](media/architecture/managed-endpoints-on.png#lightbox)

Devices come under management through several modes:

- **Mobile device management (MDM)**: typical for organization-owned devices; Intune manages the entire device.
- **Mobile application management (MAM)**: typical for personal (BYOD) devices; Intune manages only work apps and data.
- **Automated enrollment** for organization-owned hardware: Windows Autopilot, Apple Automated Device Enrollment, and Android Enterprise.

For the full supported-OS matrix, see [Supported operating systems and browsers for Intune](ref-supported-platforms).

## Endpoint family services

Endpoint family services are Microsoft products whose primary purpose is endpoint management. Each specializes in a specific aspect of the endpoint lifecycle.

[![Diagram of endpoint family services as they relate to the cloud control plane.](media/architecture/endpoint-family-services.png)](media/architecture/endpoint-family-services-on.png#lightbox)

| Service | What it does | When to use |
| --- | --- | --- |
| **[Windows Autopilot](/en-us/autopilot/overview)** | Cloud-based provisioning for new and existing Windows devices, with options for user-driven, self-deploying (zero-touch), pre-provisioning, and reset | Shipping devices directly from OEM to end users, or repurposing existing devices at scale |
| **[Windows 365](/en-us/windows-365/enterprise/overview)** | Cloud-hosted Windows desktops (Cloud PCs) | Remote workers, BYOD, contractors, regulated workloads |
| **[Windows Autopatch](/en-us/windows/deployment/windows-autopatch/overview/windows-autopatch-overview)** | Managed update service for Windows, Microsoft 365 Apps for enterprise, Microsoft Edge, Microsoft Teams, and device drivers and firmware | Reducing manual update administration |
| **[Endpoint analytics](../endpoint-analytics/)** | Telemetry and recommendations on device health and performance | Identifying performance issues and reducing help-desk volume |

## Connectors and extensions

Connectors and extensions are cloud-based external services that Intune integrates with. They have no on-premises footprint. Intune communicates with them over the internet.

[![Diagram of connectors and extensions as they relate to the cloud control plane.](media/architecture/connectors-and-extensions.png)](media/architecture/connectors-and-extensions-on.png#lightbox)

| Connector | Role |
| --- | --- |
| **[Microsoft Cloud PKI](../cloud-pki/)** | Cloud-hosted PKI that issues, renews, and revokes SCEP certificates for Intune-managed devices without requiring on-premises AD CS, NDES, or the certificate connector. Supports a fully cloud-hosted hierarchy or anchoring to your existing private root (BYOCA). |
| **[Apple Business / VPP](../app-management/deployment/manage-vpp-apple)** | Token-based integration for Apple app delivery. |
| **[Apple Push Notification service (APNs)](../device-enrollment/apple/create-mdm-push-certificate)** | Required for Apple device management. |
| **[Managed Google Play](../app-management/deployment/add-managed-google-play)** | Android Enterprise app catalog. |
| **[Microsoft Store](../app-management/deployment/add-microsoft-store)** | Built-in catalog for Windows apps. |

## Peer integrations

Peer integrations are Microsoft products that work alongside Intune. They have their own primary purpose; integration with Intune is one of many uses.

[![Diagram of peer integrations as they relate to the cloud control plane.](media/architecture/peer-integrations.png)](media/architecture/peer-integrations-on.png#lightbox)

| Product | Role |
| --- | --- |
| **[Microsoft 365 apps](../app-management/deployment/add-microsoft-365-windows)** | Deployed to managed endpoints via Intune. |
| **[Endpoint security in Microsoft Defender](../device-security/microsoft-defender/configure-integration)** | Feeds real-time device risk signals into Intune compliance evaluation and Conditional Access decisions. Also serves as a mobile threat defense (MTD) source for iOS, iPadOS and Android. |
| **[Copilot in Intune](../copilot/)** | Microsoft Security Copilot capabilities surfaced inside the Microsoft Intune admin center. |
| **[Microsoft Purview](/en-us/purview/device-onboarding-mdm)** | Sensitivity labels and endpoint data loss prevention (DLP) policies that apply to data on Intune-managed devices. |

## Partner ecosystem

The partner ecosystem includes third-party products and services that integrate with Intune through documented APIs, connectors, or configuration patterns.

[![Diagram of the partner ecosystem as it relates to the cloud control plane.](media/architecture/partner-ecosystem.png)](media/architecture/partner-ecosystem-on.png#lightbox)

| Category | Description and examples |
| --- | --- |
| **[Mobile threat defense (MTD) partners](../device-security/mobile-threat-defense/overview)** | Third-party services that feed device risk signals into Intune. Examples: Lookout, Zimperium, Check Point. Endpoint security in Microsoft Defender is also an MTD source: see Peer integrations. |
| **[Device compliance partners](../device-security/compliance/third-party-partners)** | Non-Intune MDMs that become the MDM authority for assigned user groups and report device compliance state into Microsoft Entra ID for Intune Conditional Access. Supported on Android, iOS, iPadOS, and macOS. Examples: Jamf Pro, Ivanti EPMM, BlackBerry UEM, Omnissa Workspace ONE, Kandji, SOTI MobiControl. |
| **IT service management (ITSM) partners** | Incident and asset integration. Examples: [ServiceNow](../device-management/tools/setup-servicenow), Jira. |
| **Remote support partners** | Remote control and assistance. Example: [TeamViewer](../device-management/tools/setup-teamviewer). |
| **Device vendor portals** | Vendor-specific management for specialty hardware. Examples: [Surface Management Portal](/en-us/surface/surface-management-portal), Lenovo, Intel vPro. |
| **Network access control (NAC) partners** | Network-tier access enforcement. Examples: Cisco ISE, Aruba ClearPass. |

## On-premises services

On-premises services are customer-operated infrastructure that runs on your network and integrates with the Intune cloud control plane.

[![Diagram of on-premises services as they relate to the cloud control plane.](media/architecture/on-premises-services.png)](media/architecture/on-premises-services-on.png#lightbox)

| Component | Role |
| --- | --- |
| **[Microsoft Tunnel Gateway](../device-security/microsoft-tunnel/overview)** | VPN gateway for iOS, iPadOS and Android Enterprise devices and apps. Runs in a container on Linux. |
| **[Certificate Connector for Microsoft Intune](certificates/connector/overview)** | Bridges Intune to your on-premises certificate services to issue SCEP and PKCS certificates, import PFX certificates for S/MIME, and revoke certificates. |
| **[Microsoft Configuration Manager](../configmgr/core/understand/introduction)** | On-premises peer to Intune for Windows clients and servers. Integrates with Intune through co-management and tenant attach. See Co-management and tenant attach. |

### Co-management and tenant attach

Microsoft Configuration Manager is the on-premises peer to Intune for Windows clients and servers. It manages desktops, Windows servers, and laptops on your network or connected over the internet via cloud management gateway. Configuration Manager and Intune integrate through:

- **[Co-management](../configmgr/comanage/overview)**: lets Configuration Manager and Intune both manage Windows clients. You move workloads to the cloud at your own pace.
- **[Tenant attach](../configmgr/tenant-attach/prerequisites)**: brings Configuration Manager-managed devices into the Intune admin center for visibility, remote actions, cloud-based reporting, endpoint security policy authoring (Antivirus, ASR), CMPivot, PowerShell scripts, application installs, and a unified device timeline.

By using co-management and tenant attach, organizations that already run Configuration Manager can add Intune capabilities without rebuilding their environment.