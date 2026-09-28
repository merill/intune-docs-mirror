---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 7 - Add Windows corporate identifier to device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-corporate-identifier
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
description: Add a Windows corporate identifier as one option for onboarding trusted devices with Windows Autopilot device preparation.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 9d03b025-5c1c-3e57-0296-e75fe8c0a1df
document_version_independent_id: 9d03b025-5c1c-3e57-0296-e75fe8c0a1df
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-corporate-identifier.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-corporate-identifier
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-corporate-identifier.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 2a9ca244-bd2f-1d47-5a8c-8dbb688b4853
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 7 - Add Windows corporate identifier to device | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](entra-join-automatic-enrollment)
- Step 2: [Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join)
- Step 3: [Create an assigned device group](entra-join-device-group)
- Step 4: [Create a user group](entra-join-user-group)
- Step 5: [Assign applications and PowerShell scripts to device group](entra-join-assign-apps-scripts)
- Step 6: [Create Windows Autopilot device preparation policy](entra-join-autopilot-policy)

- **Step 7, option 1: Add Windows corporate identifier to device**

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

## Add Windows corporate identifier for devices

Corporate identifiers in Intune allows pre-uploading of Windows device identifiers (serial number, manufacturer, model) and ensures only trusted Windows devices can be enrolled in Intune. If Intune enrollment restrictions are being used to block personal device enrollments, corporate identifiers need to be uploaded for all devices that are enrolled through Windows Autopilot device preparation before deployment. To add corporate identifier for devices in Intune, see [Add Windows corporate identifiers](/en-us/intune/device-enrollment/add-corporate-identifiers#add-windows-corporate-identifiers).

Note

Adding corporate identifiers is **one** of two ways to make sure only trusted devices are prepared. The other way is [device association](entra-join-device-association), which is optional. You don't need to use both. If you associate devices, they're automatically treated as corporate-owned, so you **don't** need to upload corporate identifiers for those devices. To use device association instead, see [Step 7, option 2: Associate devices](entra-join-device-association).

Important

This step of adding Windows corporate identifiers for devices is specific to Intune enrollments and isn't required if personal devices aren't being blocked in the environment. If personal devices aren't being blocked in the environment, this step can be skipped. The next step would instead be to deploy the device.

For more information, see:

- [Identify devices as corporate-owned](/en-us/intune/device-enrollment/add-corporate-identifiers).
- [What are enrollment restrictions?](/en-us/intune/device-enrollment/restrictions).
- [Create device platform restrictions](/en-us/intune/device-enrollment/create-platform-restrictions).

Once the corporate identifier is added for the device, then proceed with deploying the device.