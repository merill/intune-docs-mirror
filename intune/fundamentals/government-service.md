---
layout: Conceptual
title: Microsoft Intune Government Service overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/government-service
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn more about the Intune government service offerings and features. This article is designed to serve as an overview of the Microsoft Intune offering for government community cloud (GCC) High and United States Department of Defense (DoD) environments.
ms.date: 2026-09-08T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: acabello
locale: en-us
document_id: e6c638a5-4e16-4250-e9fc-b64dd87d7ac3
document_version_independent_id: e6c638a5-4e16-4250-e9fc-b64dd87d7ac3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/government-service.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/government-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/government-service.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9ca72641-15bf-eb2d-a328-e026ce69c191
---

# Microsoft Intune Government Service overview - Microsoft Intune | Microsoft Learn

Note

This article applies to Microsoft Intune features only. If you're looking for information on other features, then go to that specific documentation. For example, for Microsoft Teams devices, see [Teams Rooms on Windows and Android](/en-us/microsoftteams/rooms/teams-devices-feature-comparison).

The Intune U.S. government service description is as an overview of the service offering in the Government Community Cloud (GCC) High and U.S. Department of Defense (DoD) environments.

This article lists the feature differences compared to the commercial offering of [Microsoft Intune](what-is-intune). To learn more about Intune for GCC customers, see [EMS offers for US Government and Microsoft 365 interoperability](/en-us/enterprise-mobility-security/solutions/ems-govt-service-description#ems-offers-for-us-government-and-microsoft-365-interoperability).

## Intune commercial and government instances

The Intune GCC High and DoD offerings are built on the Microsoft Azure Government Cloud. This cloud is designed to interoperate with Microsoft 365 GCC High and DoD environments.

Intune has two service instances:

- **Commercial service**: The commercial service is available to anyone with an Intune license and is used by most Intune customers.
- **Government cloud**: This service is also known as **GCC High** or **DoD**. This instance is a datacenter that's physically separate from the commercial instances. The datacenter is locked down and is only used by government customers who purchase the appropriate license.

These government instances are also known as **IL4** and **IL5**, where **IL** refers to Impact Level.

- In the government cloud, the Intune service instance is shared with GCC High and DoD tenants. This architecture is slightly different than other services, such as Microsoft 365 and Azure.
- GCC is the same instance as Microsoft Intune in the commercial space. Other services, like Microsoft 365, have a separate GCC instance. Intune doesn't have a separate GCC instance.

    So, when you see **GCC** in this Intune article, it refers to the commercial service. When you see **GCC High** or **DoD**, it refers to the government cloud.

    GCC instances are commonly used by state and local government customers that require extra accreditation for the cloud services they use.

## Enroll in government tenant

![Screenshot that shows the Microsoft government cloud, including GCC High and DoD services, is physically separate from the public cloud and commercial cloud instances.](media/government-service/migration-public-government-cloud.png)

If your resources are in a commercial tenant and you want to move to the government cloud, the devices need to unenroll from the current tenant, and then re-enroll in the new tenant. There isn't a built-in way to migrate from the commercial service to the government cloud, and vice versa.

This process is similar to unenrolling from another mobile device management (MDM) service and enrolling in Intune. For more information, see [Deployment guide: Setup or move to Microsoft Intune](setup-migration#currently-use-a-third-party-mdm-provider).

Administrators can get help locking down their Intune tenants using the Secure Technical Implementation Guide (STIG). To get guidance from the `cyber.mil` website, see the [STIGs Document Library](https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=mdm-emm) (opens the `public.cyber.mil` website).

## Compliance and certifications

Intune is Common Criteria certified and is on the National Information Assurance Partnership (NIAP) Product Compliance List (PCL). To see the certification materials, see [NIAP - Product Details](https://www.niap-ccevs.org/products/11298).

For information on the US Federal Risk and Authorization Management Program (FedRAMP) accreditation and Microsoft, see [FedRAMP](/en-us/compliance/regulatory/offering-fedramp).

## Supported Intune features in GCC High and DoD

The following features are available and supported in Microsoft GCC High and/or DoD clouds:

| Feature | Availability |
| --- | --- |
| Log Analytics | You can send Intune log data to Azure Storage, Event Hubs, or Log Analytics.  For more information on this feature, see [Send log data to storage, event hubs, or log analytics from Intune](../governance/integrate-azure-monitor). |
| Microsoft Defender for Endpoint security settings management | On devices onboarded to Defender but not enrolled in Intune, you can use Intune endpoint security policies to manage Defender security settings. This support extends to the US Government Community Cloud (GCC), US Government Community High (GCC High), and Department of Defense (DoD) environments. For more information on this feature, see [Defender for Endpoint security settings management](../device-security/microsoft-defender/security-settings-management). |
| Microsoft Intune advanced capabilities | The following Intune advanced capabilities support the GCC High and DoD environments:- [Advanced Analytics](../advanced-analytics/)- [Endpoint Privilege Management](../epm/overview)- [Enterprise Application Management (EAM)](../app-management/deployment/enterprise-app-management)- [Firmware-over-the-air update](../device-updates/android/manage-fota)- [Microsoft Tunnel for Mobile Application Management](../device-security/microsoft-tunnel/mam)- [Specialty devices management](../device-management/specialty-devices)The following Intune advanced capabilities support GCC High environments only and aren't supported in DoD:- [Cloud PKI](../cloud-pki/)- [Remote Help](../remote-help/) |
| Mobile Threat Defense (MTD) | Mobile Threat Defense (MTD) connectors for Android and iOS/iPadOS devices with MTD vendors that **also support** the GCC High environment can be used. When you sign in to a GCC High tenant, you see the connectors that are available in these environments. |
| Platform support | You can use the same operating systems - Android, Android Open Source Project (AOSP), iOS/iPadOS, Linux, macOS, and Windows. - **Android (AOSP)**: There are some device restrictions. For more information, see [Supported operating systems and browsers in Intune - AOSP](ref-supported-platforms#android). - **Linux**: Generally available. |
| Standard MDM features | You can use app policies, device configuration profiles, compliance policies, and more. |
| Windows Autopilot device preparation | Some features are available now, such as user-driven deployments, and some are still in the planning phase. For more information about Windows Autopilot solutions, see [Compare Windows Autopilot device preparation and Windows Autopilot](/en-us/autopilot/device-preparation/compare).  To get started with Windows Autopilot device preparation, see [Windows Autopilot Device Preparation overview](/en-us/autopilot/device-preparation/overview). |

## Intune features planned for GCC High and DoD

The following features are currently not available and aren't supported in GCC High and DoD clouds. Planning is started to support these features for GCC High and DoD environments. If ETAs are available, then they're listed.

| Feature | Feature documentation |
| --- | --- |
| **Autopatch and updates** | [Windows Autopatch](/en-us/windows/deployment/windows-autopatch/overview/windows-autopatch-overview) |
|  | [Feature updates for Windows in Intune](../device-updates/windows/manage-feature-updates) |
|  | [Quality updates for Windows in Intune](../device-updates/windows/manage-quality-updates) |
|  | [Expedite updates for Windows in Intune](../device-updates/windows/configure-expedite-policy) |
|  | [Driver updates for Windows in Intune](../device-updates/windows/configure-driver-update-policy) |
|  | [Delivery Optimization for Win32 Apps](/en-us/windows/deployment/do/waas-delivery-optimization) |
| **BIOS and DFCI** | [BIOS configuration profiles for Windows in Intune](../device-configuration/templates/configure-bios-windows) |
|  | [Device Firmware Configuration Interface (DFCI) Management](/en-us/autopilot/dfci-management) |
| **Security Copilot** | [What is Microsoft Security Copilot?](/en-us/copilot/security/microsoft-security-copilot) |
| **Windows Device Health Attestation (DHA)** | [Device Health Attestation](/en-us/windows-server/security/device-health-attestation) |
| **[Windows Autopilot device preparation](/en-us/autopilot/device-preparation/overview)** | Customize out-of-box experience (OOBE) and rename devices during provisioning based on organizational structure |
|  | Self-deploying and pre-provisioning mode |
|  | More admin-specified configurations delivered before allowing desktop access |
|  | Enhanced optional desktop onboarding experience inside the Windows Company Portal app |
|  | The ability to associate a device with a tenant. Provisioning modes which require Windows Autopilot registration are not supported. |

## Intune features not available in GCC High and DoD

The following features aren't available and there's currently no planning to support these features for GCC High and DoD environments:

| Feature | Availability |
| --- | --- |
| [App and driver compatibility reports for Windows updates](../device-updates/windows/monitor-compatibility) | n/a |
| [Apple Managed account federation](/en-us/entra/external-id/customers/how-to-apple-federation-customers) | n/a |
| [Chrome Enterprise Connector](../device-enrollment/configure-chrome-enterprise-connector) | n/a |
| [eSIM cellular support on Windows](../device-configuration/templates/configure-esim-download-server) | n/a |
| [Intune PowerBI connector for DWH](/en-us/power-query/connectors/) | n/a |
| [Microsoft Connected Cache for Enterprise and Education](/en-us/windows/deployment/do/mcc-ent-edu-overview) | n/a |
| [Microsoft Store for Business](/en-us/windows/configuration/store/?tabs=intune) | n/a |
| On-premises Exchange Connector | n/a |
| [Remediations](../device-management/tools/deploy-remediations) | n/a |
| [Reports for feature update policies](../device-updates/windows/monitor-feature-updates) | n/a |
| [ServiceNow connector](../device-management/tools/setup-servicenow) | n/a |
| [TeamViewer connector (legacy)](../device-management/tools/teamviewer-legacy) and [TeamViewer integration](../device-management/tools/setup-teamviewer) | n/a |
| [Windows Autopilot](/en-us/autopilot/overview) | n/a |
| [Windows Backup for Organizations](/en-us/windows/configuration/windows-backup/?tabs=intune) | n/a |
| [Windows Diagnostic Data processor configuration](/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enable-windows-diagnostic-data-processor-configuration) | n/a |
| [Windows Enterprise multi-session remote desktops (AVD)](../solutions/azure-virtual-desktop-multi-session) | n/a |
| [Windows Subscription Activation](/en-us/windows/deployment/windows-subscription-activation?pivots=windows-11) | n/a |