---
layout: Conceptual
title: Overview of Windows Autopilot device preparation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/overview
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Windows Autopilot device preparation is used to set up and configure new devices, getting them ready for productive use.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: overview
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
- essentials-overview
locale: en-us
document_id: b049bc1a-0823-53b2-8f37-93c0cc733639
document_version_independent_id: b049bc1a-0823-53b2-8f37-93c0cc733639
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/overview.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 6b5742eb-415e-cbb7-acca-d4d97f0afad6
---

# Overview of Windows Autopilot device preparation | Microsoft Learn

Windows Autopilot device preparation is used to set up and configure new devices, getting them ready for productive use. Windows Autopilot device preparation aims to simplify device deployment by delivering consistent configurations, enhancing the overall setup speed, and improving troubleshooting capabilities.

This article explores the capabilities of the Windows Autopilot device preparation, its benefits for administrators, and the user experience it offers including:

- Reducing the time IT spends on deploying devices.
- Reducing the infrastructure required to maintain the devices.
- Maximizing ease of use for all types of end users.
- Improved troubleshooting.
- Near real-time deployment status and monitoring.

Note

This article is for **Windows Autopilot device preparation**. For **Windows Autopilot**, see [Overview of Windows Autopilot](../overview).

## Requirements

- Windows 11, version 24H2 or later.
- Windows 11, version 23H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later.
- Windows 11, version 22H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later.
- Microsoft Entra ID - only Microsoft Entra join is supported.
- If the device is registered as a Windows Autopilot device, which deployment runs depends on the device's association state. If the device isn't associated with the tenant, the Windows Autopilot profile takes precedence. If the device is associated, device association takes precedence and the Windows Autopilot device preparation deployment runs. To use Windows Autopilot device preparation on a registered device without associating it, first [deregister the device](../registration-overview#deregister-a-device).

For additional detailed requirements, see [Windows Autopilot device preparation requirements](requirements).

## Process overview

When new Windows devices are initially deployed, Windows Autopilot device preparation uses the OEM-optimized version of Windows client. The OEM-optimized version of Windows client is preinstalled on the device, so custom images and drivers don't need to be maintained for every device model. Instead of re-imaging the device, with Windows Autopilot device preparation, the existing Windows installation can be transformed into a "business-ready" state that can:

- Deliver Windows Autopilot device preparation configuration during device provisioning.
- Automatically add devices to the device security group and receive selected applications and PowerShell scripts assigned to the group.

## Windows Autopilot device preparation improvements

Windows Autopilot device preparation is an improved profile experience that incorporates common customer asks. It improves the onboarding experience by providing a profile experience to deploy configurations efficiently, consistently, and remove the complexity out of troubleshooting. Its goal is to be:

- Simple.
- Fast.
- Observable.
- Reliable.

New features in Windows Autopilot device preparation include:

- **Utilizing enrollment time grouping in Intune** - Device is added to a device security group at enrollment time and configuration is delivered immediately. This feature provides a faster and more reliable setup. For more information, see Enrollment Time Grouping.
- **Granular reporting** - Improved monitoring and troubleshooting. Monitoring and reporting with near real-time status of deployments, including:

    - Applications status
    - PowerShell scripts status
    - Deployment time. For more information, see [Windows Autopilot device preparation reporting and monitoring](reporting-monitoring).
- **Support for Government Community Cloud High (GCCH) and Department of Defense (DoD) environments** - Windows Autopilot device preparation supports [GCCH and DoD](/en-us/intune/fundamentals/government-service) environments.

Important

[Windows 365 Flex in shared mode](/en-us/windows-365/enterprise/introduction-windows-365-frontline) isn't supported for GCCH and DoD at this time.

## Capabilities

Windows Autopilot device preparation capabilities include:

- Set up user-driven or automatic deployment flow.
- By default, making sure users are standard non-administrator users.
- Select application and PowerShell script to be delivered during device setup.
- Simplified and clear OOBE user experience with percentage progress indicator for user-driven flows.
- Deployment report for better troubleshooting.

## Improved experiences

### Admin experience

- Windows Autopilot device preparation simplifies admin configuration by having a single profile to provision all policies in one location, including deployment and OOBE settings.
- Line-of-business (LOB) and Win32 applications can be deployed in the same deployment.

### User experience

Windows Autopilot device preparation also improves the user experience in the following ways:

- A simplified view during OOBE where the percentage of progress is displayed.
- The experience is more consistent.
- The user is informed when the OOBE setup is complete.
- When issues arise, logs can be exported with ease.
- The end-user gets to the desktop faster.

### Troubleshooting and Reporting

Windows Autopilot device preparation offers near real-time status updates on deployments. Windows Autopilot device preparation monitoring includes application and PowerShell script status information, allowing for improved troubleshooting and reporting. Deployment monitoring includes the following features:

- Easily track which devices that went through Windows Autopilot device preparation.
- Track status and deployment phase for each device in near real-time.
- Each device has the following details in the monitoring report:
    - Device details.
    - Profile name and version.
    - Deployment status details.
    - Apps applied with status.
    - Scripts applied with status.

### Enrollment Time Grouping

The key to Windows Autopilot device preparation is Enrollment Time Grouping. With Enrollment Time Grouping, when a user authenticates into a device, the device is added to a pre-defined device security group during enrollment. Applications, scripts, and policies assigned to the device group are then deployed to the device. Direct assignment of devices to the device group allows the applications, scripts, and policies assigned to the device group to deploy quicker and more efficiently versus when using a dynamic device group.

Enrollment time grouping consists of the following phases:

- **Configure applications and policies to a security group** - User authenticates and the Windows Autopilot device preparation configuration is delivered.
- **Select applications and PowerShell scripts to get installed during OOBE** - Selected applications and PowerShell scripts assigned to the device security group are installed. The device also joins the device security group.

For Windows Autopilot device preparation:

- The device group is selected in the Windows Autopilot device preparation profile.
- Only applications and PowerShell scripts selected in the Windows Autopilot device preparation profile are deployed during OOBE. Any additional applications or PowerShell scripts assigned to the device group will be deployed after the Windows Autopilot device preparation deployment is complete.
- For policies, Windows Autopilot device preparation syncs any policies assigned to the device group. However, Windows Autopilot device preparation doesn't track if the policies are applied during the deployment. The policies might be applied either during the deployment or after the deployment is complete.

For more information, see [Enrollment time grouping in Microsoft Intune](/en-us/intune/intune-service/enrollment/enrollment-time-grouping).

### Corporate identifiers for Windows

Windows Autopilot device preparation supports the Intune corporate identifier enrollment feature. Corporate identifiers in Intune allows pre-uploading of Windows device identifiers (serial number, manufacturer, model) and ensures only trusted devices go through Windows Autopilot device preparation.

Windows Autopilot device preparation only requires corporate identifiers for Windows if Intune enrollment restrictions are being used to block personal device enrollments. For more information, see:

- [Identify devices as corporate-owned](/en-us/intune/intune-service/enrollment/corporate-identifiers-add).
- [What are enrollment restrictions?](/en-us/intune/intune-service/enrollment/enrollment-restrictions-set).
- [Create device platform restrictions](/en-us/intune/intune-service/enrollment/create-device-platform-restrictions).

### Device association

Windows Autopilot device preparation supports device association, which binds a physical Windows 11 device to your tenant before enrollment. Associated devices are automatically marked as corporate-owned and can receive device-targeted policy assignments and additional OOBE customizations. For more information, see [Overview of Windows Autopilot device association](device-association/overview).

## Tutorial

For tutorials with detailed instructions on configuring Windows Autopilot device preparation, see [Windows Autopilot device preparation scenarios](tutorial/scenarios).