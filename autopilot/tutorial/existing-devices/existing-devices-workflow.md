---
layout: Conceptual
title: Overview for Windows Autopilot deployment for existing devices in Intune and Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/existing-devices-workflow
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
description: Overview for Windows Autopilot deployment for existing devices in Intune and Configuration Manager.
ms.date: 2025-05-23T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: bf165d85-bd93-0983-a3bd-a943716579dc
document_version_independent_id: bf165d85-bd93-0983-a3bd-a943716579dc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/existing-devices-workflow.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/existing-devices-workflow
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/existing-devices-workflow.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7d759848-6de2-9bc8-236a-e676ec8ab62c
---

# Overview for Windows Autopilot deployment for existing devices in Intune and Configuration Manager | Microsoft Learn

This step by step tutorial guides through using Intune and Microsoft Configuration Manager to perform a Windows Autopilot deployment for existing devices.

The purpose of this tutorial is a step by step guide for all the configuration steps required for a successful Windows Autopilot deployment for existing devices using Intune and Microsoft Configuration Manager. The tutorial is also designed as a walkthrough in a lab or testing scenario, but can be expanded for use in a production environment. This tutorial assumes familiarity with Microsoft Configuration Manager and that Microsoft Configuration Manager is already set up and configured to support operating system deployments.

## Windows Autopilot deployment for existing devices overview

The main use case scenario for Windows Autopilot is to automate the configuration of Windows on a new device delivered directly from an IT department, OEM, or reseller. However, sometimes existing devices in an environment need to be repurposed, fixed, or updated to a later version of Windows by reinstalling Windows on the device. Reinstalling of Windows is usually performed via a reimage of the device, which is outside the capabilities of Windows Autopilot. Windows Autopilot also isn't able to perform a fresh install of Windows if the version of Windows is different than the one that is currently installed on the device. There might also be other conditions that prevent Windows Autopilot from performing a fresh install of Windows on the device. For example, corruption of the current Windows install or a hard drive failure.

Windows Autopilot can utilize Microsoft Configuration Manager task sequences tor scenarios where Windows needs to be:

- Reinstalled to a later version of Windows using a fresh installation of Windows.
- Updated to a later version of Windows using a fresh installation of Windows.

Microsoft Configuration Manager task sequences can reimage a device and perform a fresh installation of Windows. The Configuration Manager task sequence can also pre-install a Windows Autopilot profile on the device via a JSON file. Once the Configuration Manager task sequence is done, the device can then automatically run the Windows Autopilot deployment defined in the Windows Autopilot profile JSON file. When the Windows Autopilot profile JSON file is pre-installed on the device, the Windows Autopilot deployment can run on the device without having to first perform the following actions:

- Import the device into Intune as a Windows Autopilot device.
- Assign a Windows Autopilot profile to the device.

Windows Autopilot deployment for existing devices is useful for the following scenarios:

- Repurpose an existing device that isn't yet a Windows Autopilot device.
- Migrate an on-premises domain joined device that isn't part of Microsoft Entra ID to a Microsoft Entra join device.
- Convert an on-premises domain joined device that is Microsoft Entra hybrid joined to a Microsoft Entra join device.
- Reinstall Windows on devices that need to be repaired. For example, a device that has a corrupted Windows installation or where the hard drive was replaced.
- Upgrade older versions of Windows that don't support Microsoft Entra ID (Windows 8.1) to a version of Windows that does support Microsoft Entra ID (Windows 10/Windows 11).
- Using custom Windows images instead of the OEM provided Windows installation.

Windows Autopilot deployment for existing devices can be viewed as a method to prepare an existing device for a Windows Autopilot deployment.

Note

The JSON file for Windows Autopilot for existing devices only supports user-driven Microsoft Entra ID and user-driven hybrid Microsoft Entra Windows Autopilot profiles. Self-deploying and pre-provisioning Windows Autopilot profiles aren't supported with JSON files due to these scenarios requiring TPM attestation. TPM attestation only works where there's an existing Windows Autopilot device since the TPM attestation information is stored in the Windows Autopilot device object.

However, during the Windows Autopilot for existing devices deployment, if the following conditions are true:

- Device is already a Windows Autopilot device before the deployment begins
- Device has a Windows Autopilot profile assigned to it

then the assigned Windows Autopilot profile takes precedence over the JSON file installed by the task sequence. In this scenario, if the assigned Windows Autopilot profile is either a self-deploying or pre-provisioning Windows Autopilot profile, then the self-deploying and pre-provisioning scenarios are supported.

## Workflow

The following steps are needed to configure and then perform a Windows Autopilot deployment for existing devices deployment using Intune and Microsoft Configuration Manager:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

Important

- If enrollment restrictions are configured to block personal devices from enrolling, Windows Autopilot for existing devices can't be used. For more information, see [What are enrollment restrictions?: Blocking personal Windows devices](/en-us/intune/intune-service/enrollment/enrollment-restrictions-set#blocking-personal-windows-devices).
- Any devices registered using a .json file during a hybrid join scenario are normally enrolled as a Corporate device.

## Walkthrough