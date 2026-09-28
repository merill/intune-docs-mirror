---
layout: Conceptual
title: Overview for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/automatic/automatic-workflow
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
description: Overview for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune.
ms.date: 2025-11-21T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 059fbdfb-eb55-28b6-814d-ec190155fe31
document_version_independent_id: 059fbdfb-eb55-28b6-814d-ec190155fe31
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/automatic/automatic-workflow.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/automatic/automatic-workflow
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/automatic/automatic-workflow.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/72cb4d1c-66f7-4281-99d5-e04a64d084fc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d9ebaec0-4879-449e-9781-0afdce99fe0a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 3d897970-31d7-2ff5-2294-5595d84c8a46
---

# Overview for Windows Autopilot device preparation in automatic mode for Windows 365 in Intune | Microsoft Learn

This step by step tutorial guides through using Intune to perform a Windows Autopilot device preparation in automatic mode for Windows 365. You can use Windows Autopilot device preparation policies in automatic mode to provision these supported SKUs:

- Windows 365 Flex in shared mode
- Windows 365 Enterprise
- Windows 365 Flex in dedicated mode
- Windows 365 Cloud Apps

The purpose of this tutorial is a step by step guide for all the configuration steps required for a successful Windows Autopilot device preparation in automatic mode for Windows 365 deployment using Intune. The tutorial is also designed as a walkthrough in a lab or testing scenario, but can be expanded for use in a production environment.

Before beginning, refer to the [How to: Plan your Microsoft Entra join implementation](/en-us/azure/active-directory/devices/azureadjoin-plan) to make sure all requirements are met for joining devices to Microsoft Entra ID.

## Windows Autopilot device preparation in automatic mode for Windows 365 overview

Windows Autopilot device preparation in automatic mode for Windows 365, also known as Windows Autopilot device preparation automatic mode, is a solution that adds an additional Windows Autopilot device preparation policy that can be included in Windows 365 provisioning policies. By including the Windows Autopilot device preparation policy in the Windows 365 provisioning policies, it ensures that essential required device-targeted apps and scripts in Intune are installed on Cloud PCs during the provisioning process before the user signs in. This feature helps increase standardization of Cloud PCs while reducing the management overhead that comes with IT admins creating and managing their own custom images with pre-installed applications.

Windows Autopilot device preparation tracks the installation progress of specified Intune applications and scripts during Cloud PC provisioning. Instead of marking Cloud PCs as **Provisioned** after Intune enrollment, Windows Autopilot device preparation and Windows 365 wait until those workloads are fully installed. IT admins see a new status of **Preparing** reflected in the console while Windows Autopilot device preparation is underway.

## Windows Autopilot device preparation in automatic mode for Windows 365 process

1. The Windows 365 Cloud PC agent creates the Cloud PC.
2. Once the Cloud PC is created, the Cloud PC agent joins Microsoft Entra.
3. The Cloud PC agent triggers Intune enrollment.
4. The Cloud PC agent calls the Windows Autopilot device preparation policy assigned to the Cloud PC provisioning policy and the configuration is applied including:
5. The Intune management extension is installed.
6. The deployment syncs with Intune and checks if line-of-business (LOB) and Microsoft 365 applications are selected in the Windows Autopilot device preparation policy. It also syncs all MDM policy at this time, but application of the policy isn't tracked during the deployment. If this step fails, the **Deployment Status** shows up as **Failed** during the phase **Policy installation** in the [Windows Autopilot device preparation reporting and monitoring](../../reporting-monitoring).
7. If there are LOB and Microsoft 365 applications selected in the policy, then they're installed. If any application installation fails, the **Deployment Status** shows up as **Failed** during the phase **Apps installation** in the [Windows Autopilot device preparation reporting and monitoring](../../reporting-monitoring).
8. The deployment checks if PowerShell scripts are selected in the Windows Autopilot device preparation policy. If there are PowerShell scripts selected in the policy, then they run. If any script fails, the **Deployment Status** shows up as **Failed** during the phase **Scripts installation** in the [Windows Autopilot device preparation reporting and monitoring](../../reporting-monitoring).
9. The deployment checks if Win32, Microsoft Store, or Enterprise App Catalog applications are selected in the Windows Autopilot device preparation policy. If there are Win32, Microsoft Store, or Enterprise App Catalog applications selected in the policy, then they're installed. If any application installation fails, the **Deployment Status** shows up as **Failed** during the phase **Apps installation** in the [Windows Autopilot device preparation reporting and monitoring](../../reporting-monitoring).

    Important

    As part of a Windows Autopilot device preparation in automatic mode for Windows 365 deployment:

    - Up to 25 essential applications can be installed.
    - Up to 10 essential PowerShell scripts can be run.

## Workflow

The following steps are needed to configure and then perform a Windows Autopilot device preparation in automatic mode for Windows 365 in Intune:

- Step 1: [Set up Windows automatic Intune enrollment](automatic-automatic-enrollment)
- Step 2: [Create an assigned device group](automatic-device-group)
- Step 3: [Assign applications and PowerShell scripts to device group](automatic-assign-apps-scripts)
- Step 4: [Create Windows Autopilot device preparation policy](automatic-autopilot-policy)
- Step 5: [Create a Cloud PC provisioning policy](automatic-cloud-pc-provisioning-policy)
- Step 6: [Monitor the deployment](automatic-monitor)

Note

Although the workflow is designed for lab or testing scenarios, it can also be used in a production environment.

## Walkthrough