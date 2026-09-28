---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 1 of 10 - Set up a Windows Autopilot profile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/setup-autopilot-profile
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 1 of 10 - Set up a Windows Autopilot profile.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 49ddae1c-374d-152b-ad98-4b9d5dd8e0bc
document_version_independent_id: 49ddae1c-374d-152b-ad98-4b9d5dd8e0bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/setup-autopilot-profile.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/setup-autopilot-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/setup-autopilot-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: c8a3562f-3b37-f6ae-9259-0230d3696534
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 1 of 10 - Set up a Windows Autopilot profile | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- **Step 1: Set up a Windows Autopilot profile**

- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Set up a Windows Autopilot profile

Windows Autopilot deployment for existing devices isn't a Windows Autopilot deployment where a Windows Autopilot profile is downloaded and applied to a device during the out-of-box experience (OOBE) of Windows Setup. Instead, it prepares a device to receive a Windows Autopilot profile by performing the following actions:

- Wipes the device.
- Installs a fresh copy of Windows.
- Installs a JSON file that contains the information for an existing Windows Autopilot profile.

The first step in a Windows Autopilot for existing devices deployment is to make sure there's already an existing valid Windows Autopilot profile in Intune so that the JSON file can be created. Since the JSON file only supports the user-driven Microsoft Entra join and user-driven Microsoft Entra hybrid join Windows Autopilot scenarios, one of the following steps from the respective scenario workflows can be used to create a valid Windows Autopilot profile:

- [User-driven Microsoft Entra join: Create and assign user-driven Microsoft Entra join Windows Autopilot profile](../user-driven/azure-ad-join-autopilot-profile)
- [User-driven Microsoft Entra hybrid join: Create and assign user-driven Microsoft Entra hybrid join Windows Autopilot profile](../user-driven/hybrid-azure-ad-join-autopilot-profile)

Note

In the above steps, it's not necessary to assign the Windows Autopilot profile for Windows Autopilot deployment for existing devices scenario to work. The Windows Autopilot profile only needs to be created so that the JSON file can then be created.

Once a valid Windows Autopilot profile is created and confirmed working on an existing Windows Autopilot device, then proceed to [Step 2: Install required modules to obtain Windows Autopilot profiles from Intune](install-modules).

## Next step: Install required modules to obtain Windows Autopilot profiles from Intune