---
layout: Conceptual
title: Automatic registration of existing devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/automatic-registration
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
description: Automatically add devices to Windows Autopilot.
ms.date: 2025-06-13T00:00:00.0000000Z
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
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 7f28d1aa-c61e-c7e2-ac73-0de1aaaa386e
---

# Automatic registration of existing devices | Microsoft Learn

## Requirements

An existing device can automatically register if it's:

- Running a [supported version](/en-us/windows/release-information/) of Windows
- Enrolled in a mobile device management (MDM) service such as Intune
- A corporate device that isn't already registered with Windows Autopilot

For devices that meet these requirements, the MDM service can ask the device for the hardware hash. After it has that, it can automatically register the device with Windows Autopilot.

For more information on how to automatically register devices for Windows Autopilot with Microsoft Intune, see [Create a Windows Autopilot deployment profile](profiles#create-a-windows-autopilot-deployment-profile) and review the description of the **Convert all targeted devices to Autopilot** setting. See the following example:

![Screenshot that shows how to convert all targeted devices.](images/convert-devices.png)

Note

Using the setting **Convert all targeted devices to Autopilot** in the Windows Autopilot profile doesn't automatically convert existing hybrid Microsoft Entra device in the assigned groups into a Microsoft Entra device. The setting only registers the devices in the assigned groups for the Windows Autopilot service. For more information, see [Create a Windows Autopilot deployment profile](profiles#create-a-windows-autopilot-deployment-profile).

## Windows Autopilot for existing devices

When the [Windows Autopilot for existing devices](existing-devices) scenario is used, devices don't need to be preregistered with Windows Autopilot. Instead, a configuration file (AutopilotConfigurationFile.json) containing all the Windows Autopilot profile settings is used. The device can then be registered with Windows Autopilot using the same **Convert all targeted devices to Autopilot** setting.