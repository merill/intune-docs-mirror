---
layout: Conceptual
title: Features and capabilities - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/features-and-capabilities
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about the primary management capabilities of Configuration Manager.
ms.date: 2021-07-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 3995a74e-5f4c-d5a6-a3b8-90dbae72bb3d
document_version_independent_id: 3a340659-fe40-56f7-8873-b176a6b2aca7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/features-and-capabilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/features-and-capabilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/features-and-capabilities.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: f57035c9-b65f-02b5-c460-d4841f597a54
---

# Features and capabilities - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article summarizes the primary management features of Configuration Manager. Each feature has its own prerequisites, and how you use each might influence the design and implementation of your Configuration Manager hierarchy. For example, if you want to deploy software updates to devices in your hierarchy, you need a software update point site system role.

## Co-management

Co-management is one of the primary ways to attach your existing Configuration Manager deployment to the Microsoft 365 cloud. It enables you to concurrently manage Windows devices by using both Configuration Manager and Microsoft Intune. Co-management lets you cloud-attach your existing investment in Configuration Manager by adding new functionality like Conditional Access. For more information, see [What is co-management](../../../comanage/overview)?

## Cloud-attached management

Use features like the cloud management gateway and Microsoft Entra ID to manage internet-based clients.

For more information, see the following articles:

- [Cloud management gateway overview](../../clients/manage/cmg/overview)
- [Plan for Microsoft Entra ID](../security/plan-for-security#azure-active-directory)
- [Azure services](../../servers/deploy/configure/azure-services-wizard)

## Real-time management

Use CMPivot to immediately query online devices, then filter and group the data for deeper insights. Also use the Configuration Manager console to manage and deploy Windows PowerShell scripts to clients. For more information, see [CMPivot](../../servers/manage/cmpivot) and [Create and run PowerShell scripts](../../../apps/deploy-use/create-deploy-scripts).

## Application management

Helps you create, manage, deploy, and monitor applications to a range of different devices that you manage. Deploy, update, and manage Microsoft 365 Apps from the Configuration Manager console. Additionally, Configuration Manager integrates with the Microsoft Store for Business and Education to deliver cloud-based apps. For more information, see [Introduction to application management](/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management).

## OS deployment

Deploy an in-place upgrade of Windows, or capture and deploy OS images. Image deployment can use PXE, multicast, or bootable media. It can also help redeploy existing devices using Windows Autopilot. For more information, see [Introduction to OS deployment](../../../osd/understand/introduction-to-operating-system-deployment).

## Software updates

Manage, deploy, and monitor software updates in the organization. Integrate with Windows Delivery Optimization and other peer caching technologies to help control network usage. For more information, see [Introduction to software updates](../../../sum/understand/software-updates-introduction).

## Company resource access

Lets you give users in your organization access to data and applications from remote locations. This feature includes Wi-Fi, VPN, email, and certificate profiles. For more information, see [Protect data and site infrastructure](../../../protect/understand/protect-data-and-site-infrastructure).

## Compliance settings

Helps you to assess, track, and remediate the configuration compliance of client devices in the organization. Additionally, you can use compliance settings to configure a range of features and security settings on devices you manage. For more information, see [Ensure device compliance](../../../compliance/understand/ensure-device-compliance).

## Endpoint Protection

Provides security, antimalware, and Windows Firewall management for computers in your organization. This area includes management and integration with the following Windows Defender suite features:

- Windows Defender Antivirus
- Microsoft Defender for Endpoint
- Windows Defender Exploit Guard
- Windows Defender Application Guard
- Windows Defender Application Control
- Windows Defender Firewall

For more information, see [Endpoint Protection](../../../protect/deploy-use/endpoint-protection).

## Inventory

Helps you identify and monitor assets.

### Hardware inventory

Collects detailed information about the hardware of devices in your organization. For more information, see [Introduction to hardware inventory](../../clients/manage/inventory/introduction-to-hardware-inventory).

### Software inventory

Collects and reports information about the files that are stored on client computers in your organization. For more information, see [Introduction to software inventory](../../clients/manage/inventory/introduction-to-software-inventory).

### Asset Intelligence

Provides tools to collect inventory data and monitor software license usage in your organization. For more information, see [Introduction to Asset Intelligence](../../clients/manage/asset-intelligence/introduction-to-asset-intelligence).

## On-premises mobile device management

Enrolls and manages devices by using the on-premises Configuration Manager infrastructure with the management functionality built into the device platforms. (Typical management uses a separately installed Configuration Manager client.) This feature currently supports managing Windows 10 Enterprise and Windows 10 Mobile devices. For more information, see [Manage mobile devices with on-premises infrastructure](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure).

## Power management

Manage and monitor the power consumption of client computers in the organization. Configure power plans, and use Wake-on-LAN to do maintenance outside of business hours. For more information, see [Introduction to power management](../../clients/manage/power/introduction-to-power-management).

## Remote control

Provides tools to remotely administer client computers from the Configuration Manager console. For more information, see [Introduction to remote control](../../clients/manage/remote-control/introduction-to-remote-control).

## Reporting

Use the advanced reporting capabilities of SQL Server Reporting Services from the Configuration Manager console. This feature provides hundreds of default reports. For more information, see [Introduction to reporting](../../servers/manage/introduction-to-reporting).

## Software metering

Monitor and collect software usage data from Configuration Manager clients. You can use this data to determine whether software is used after it's installed. For more information, see [Monitor app usage with software metering](../../../apps/deploy-use/monitor-app-usage-with-software-metering).