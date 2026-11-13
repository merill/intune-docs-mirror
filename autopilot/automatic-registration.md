---
layout: Conceptual
title: Automatic Registration of Existing Devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/automatic-registration
author: madakeva
ms.author: madakeva
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Automatically register existing devices with Windows Autopilot through Intune or another MDM service. Learn the requirements and how to convert targeted devices.
ms.date: 2026-10-30T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
locale: en-us
document_id: 0f313c76-083f-0431-a800-5ed3c5713b69
document_version_independent_id: 0f313c76-083f-0431-a800-5ed3c5713b69
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/automatic-registration.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: automatic-registration
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/automatic-registration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7f28d1aa-c61e-c7e2-ac73-0de1aaaa386e
---

# Automatic Registration of Existing Devices | Microsoft Learn

## Requirements

An existing device can automatically register if it meets the following criteria:

- Runs a [supported version](/en-us/windows/release-information/) of Windows
- Enrolled in a mobile device management (MDM) service such as Intune
- A corporate device that isn't already registered with Windows Autopilot

For devices that meet these requirements, the MDM service can request the hardware hash from the device. After it has the hardware hash, it can automatically register the device with Windows Autopilot.

For more information about how to automatically register devices for Windows Autopilot with Microsoft Intune, see [Create a Windows Autopilot deployment profile](profiles#create-a-windows-autopilot-deployment-profile) and review the description of the **Convert all targeted devices to Autopilot** setting. See the following example:

![Screenshot that shows how to convert all targeted devices.](images/convert-devices.png)

Note

Using the **Convert all targeted devices to Autopilot** setting in the Windows Autopilot profile doesn't automatically convert existing hybrid Microsoft Entra devices in the assigned groups into Microsoft Entra devices. The setting only registers the devices in the assigned groups for the Windows Autopilot service. For more information, see [Create a Windows Autopilot deployment profile](profiles#create-a-windows-autopilot-deployment-profile).

## Windows Autopilot for existing devices

When you use the [Windows Autopilot for existing devices](existing-devices) scenario, you don't need to preregister devices with Windows Autopilot. Instead, use a configuration file (AutopilotConfigurationFile.json) that contains the Windows Autopilot profile settings. You can then register the device with Windows Autopilot by using the **Convert all targeted devices to Autopilot** setting.