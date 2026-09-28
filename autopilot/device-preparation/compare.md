---
layout: Conceptual
title: Compare Windows Autopilot device preparation and Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/compare
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
description: Compare Windows Autopilot device preparation and Windows Autopilot features and when to use each.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: overview
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
locale: en-us
document_id: 5a0589ab-0697-7bd4-c352-06c9408439d0
document_version_independent_id: 5a0589ab-0697-7bd4-c352-06c9408439d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/compare.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/compare
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/compare.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: c22138c7-90d7-b68e-4f46-f3d43a21ea5b
---

# Compare Windows Autopilot device preparation and Windows Autopilot | Microsoft Learn

## Windows Autopilot device preparation vs. Windows Autopilot

| Feature | **Windows Autopilotdevice preparation** | **Windows Autopilot** |
| --- | --- | --- |
| Features | - Support for Government Community Cloud High (GCCH) and Department of Defense (DoD) environments.<br>- Faster, more consistent provisioning experience.<br>- Near real-time monitoring and troubleshooting info. | - Support for multiple device types ([HoloLens](/en-us/hololens/hololens2-autopilot), [Teams Meeting Room](/en-us/microsoftteams/rooms/autopilot-autologin)).<br>- Many customization options for the provisioning experience. |
| Supported modes | - [User-driven](tutorial/user-driven/entra-join-workflow).<br>- Automatic. | - [User-driven](../tutorial/user-driven/azure-ad-join-workflow).<br>- [Pre-provisioned](../tutorial/pre-provisioning/azure-ad-join-workflow).<br>- [Self-deploying](../tutorial/self-deploying/self-deploying-workflow).<br>- [Existing devices](../tutorial/existing-devices/existing-devices-workflow). |
| Join types supported | - Microsoft Entra join. | - Microsoft Entra join.<br>- Microsoft Entra hybrid join. |
| Device registration required? | No. | Yes. |
| Is it possible to bind devices to my tenant before enrollment? | Yes, you can [associate devices](tutorial/user-driven/entra-join-device-association). | Yes, you can [register devices](../registration-overview). |
| What do admins need to configure? | - Windows Autopilot device preparation policy.<br>- Device security group with **Intune Provisioning Client** as owner. | - Windows Autopilot deployment profile.<br>- Enrollment Status Page (ESP). |
| What configurations can be delivered during provisioning? | - Device-based only during the out-of-box experience (OOBE).<br>- Up to 25 essential applications (line-of-business (LOB), Win32, Microsoft Store, Microsoft 365).<br>- Up to 10 essential PowerShell scripts. | - Device-based during device ESP.<br>- User-based during user ESP.<br>- Up to [100 applications](/en-us/intune/intune-service/enrollment/windows-enrollment-status#block-access-to-a-device-until-a-specific-application-is-installed). |
| Reporting & troubleshooting | Windows Autopilot device preparation deployment report:<br>- Shows all Windows Autopilot device preparation deployments.<br>- More data available.<br>- Near real-time. | Windows Autopilot deployment report:<br>- Only shows Windows Autopilot registered devices.<br>- Not real-time. |
| Supports LOB and Win32 applications in same deployment? | Yes. | No. |
| Supported versions of Windows | - Windows 11, version 24H2 or later.<br>- Windows 11, version 23H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later.<br>- Windows 11, version 22H2 with [KB5035942](https://support.microsoft.com/topic/march-26-2024-kb5035942-os-builds-22621-3374-and-22631-3374-preview-3ad9affc-1a91-4fcb-8f98-1fe3be91d8df) or later. | - All [currently supported](/en-us/windows/release-health/supported-versions-windows-client#windows-11-supported-versions-by-servicing-option) versions of Windows 11 General Availability Channel.<br>- All [currently supported](/en-us/windows/release-health/supported-versions-windows-client#windows-10-supported-versions-by-servicing-option) versions of Windows 10 General Availability Channel. |

## Which Windows Autopilot solution to use

Which version of Windows Autopilot to use is dependent on many factors and variables, with each environment having different needs. Windows Autopilot device preparation in its initial offering isn't as feature rich as Windows Autopilot, but it does have some advantages and features not available in Windows Autopilot.

In general, the following are some of the major factors when considering between Windows Autopilot device preparation or Windows Autopilot:

| Requirement | **Windows Autopilotdevice preparation** | **WindowsAutopilot** |
| --- | --- | --- |
| Government Community Cloud High (GCCH) andDepartment of Defense (DoD) environments | ✅ | ❌ |
| User-driven scenario | ✅ | ✅ |
| Pre-provisioned scenario | ❌ | ✅ |
| Self-deploying scenario | ❌ | ✅ |
| Existing devices scenario | ❌ | ✅ |
| Automatic deployment scenario | ✅ | ❌ |
| Windows Autopilot reset support | ❌ | ✅ |
| Microsoft Entra join | ✅ | ✅ |
| Microsoft Entra hybrid join | ❌ | ✅ |
| [Windows Autopilot Reset](../tutorial/reset/autopilot-reset-overview) | ❌ | ✅ |
| Windows 11 | ✅ | ✅ |
| Windows 10 | ❌ | ✅ |
| Deploy Win32 and LOB applicationsin the same deployment | ✅ | ❌ |
| Simpler deployment configuration and experience | ✅ | ❌ |
| Extensive customization of deploymentand OOBE experience | ❌ | ✅ |
| No requirement to pre-stage devices | ✅ | ❌ |
| Install more than 10 applications during OOBE | ❌ | ✅ |
| Run more than 10 PowerShell scripts during OOBE | ❌ | ✅ |
| Near real-time monitoring | ✅ | ❌ |
| Block user from accessing desktop untiluser based configurations are applied | ❌ | ✅ |
| [HoloLens](/en-us/hololens/hololens2-autopilot) support | ❌ | ✅ |
| [Teams Meeting Room](/en-us/microsoftteams/rooms/autopilot-autologin) support | ❌ | ✅ |
| Device Firmware Configuration Interface([DFCI](../dfci-management)) Management support | ❌ | ✅ |
| [Windows Autopilot into co-management](/en-us/intune/configmgr/comanage/autopilot-enrollment) | ❌ | ✅ |

## Using Windows Autopilot device preparation and Windows Autopilot concurrently

Windows Autopilot device preparation and Windows Autopilot can be used concurrently and side by side within an organization. However, any one device in an environment can only run one of the two solutions. For a device that's registered with Windows Autopilot, which deployment runs depends on the device's association state. If the device isn't associated with the tenant, the Windows Autopilot profile takes precedence. If the device is associated, device association takes precedence and the Windows Autopilot device preparation deployment runs. To use Windows Autopilot device preparation on a registered device without associating it, first [deregister the device](../registration-overview#deregister-a-device).