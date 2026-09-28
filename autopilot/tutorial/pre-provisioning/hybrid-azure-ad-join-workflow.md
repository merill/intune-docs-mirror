---
layout: Conceptual
title: Overview for Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join in Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-workflow
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
description: Overview for Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join in Intune.
ms.date: 2024-09-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 4783b35c-22dd-75af-5d89-74f89de700c4
document_version_independent_id: 4783b35c-22dd-75af-5d89-74f89de700c4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-workflow.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-workflow
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-workflow.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 5ffb83ee-8543-e1a4-5ba5-31d3407aa98b
---

# Overview for Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join in Intune | Microsoft Learn

Important

Microsoft recommends deploying new devices as cloud-native using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

This step by step tutorial guides through using Intune to perform a Windows Autopilot for pre-provisioned deployment scenario when the devices are also joined to an on-premises domain, also known as Microsoft Entra hybrid join.

The purpose of this tutorial is a step by step guide for all the configuration steps required for a successful Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join deployment using Intune. The tutorial is also designed as a walkthrough in a lab or testing scenario, but can be expanded for use in a production environment.

Before beginning, refer to the [Plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan) to make sure all requirements are met for joining on-premises AD devices to Microsoft Entra ID.

Note

Before attempting the Windows Autopilot pre-provisioned Microsoft Entra hybrid join scenario, Microsoft recommends that the [Windows Autopilot user-driven Microsoft Entra hybrid join](../user-driven/hybrid-azure-ad-join-workflow) scenario is first configured, tested, and working. The Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join builds on top of Windows Autopilot user-driven Microsoft Entra hybrid join scenario. If the Windows Autopilot user-driven Microsoft Entra hybrid join scenario isn't working, then most likely the Windows Autopilot pre-provisioned deployment Microsoft Entra hybrid join scenario won't work either.

## Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join is a Windows Autopilot solution that automates the configuration of Windows on a new device. The device is normally delivered directly from one of the following sources to the end user:

- IT department.
- OEM.
- Reseller.

Windows Autopilot for pre-provisioned deployment uses the existing Windows installation installed by the OEM at the factory. The end-user only needs to perform a minimal number of actions during the deployment process such as:

- Powering on the device.
- In certain scenarios, selecting the language, locale, and keyboard layout.
- Connecting to a wireless network if the device isn't connected to a wired network.
- Signing in to the device with the end-user's on-premises domain credentials.
- In certain scenarios, signing in to Microsoft Entra ID with the end-user's Microsoft Entra credentials.

Windows Autopilot for pre-provisioned deployment can perform the following tasks during the deployment:

- Joins the device to an on-premises domain.
- Registers the device with Microsoft Entra ID.
- Enrolls the device in Intune.
- Installs applications.
- Applies device configuration policies such as BitLocker and Windows Hello for Business.
- Checks for compliance.
- The Enrollment Status Page (ESP) prevents an end-user from using the device until the device is fully configured.

Windows Autopilot for pre-provisioned deployment consists of two phases:

- Device ESP phase: Windows is configured and applications and policies assigned to the device are applied.
- User ESP phase: End-user signs into the device for the first time using on-premises domain credentials and applications and policies assigned to the user are applied.

Once the Windows Autopilot for pre-provisioned deployment is complete, the device is ready for the end-user to use. The Windows Autopilot deployment prompts the end-user to sign out of the device. Once the device is signed out, the end-user can sign back in with their on-premises domain credentials and begin to use the device.

## Differences between Windows Autopilot user-driven deployment and Windows Autopilot for pre-provisioned deployment

The main difference between Windows Autopilot user-driven deployment and Windows Autopilot for pre-provisioned deployment is:

- Windows Autopilot user-driven deployment: Both the Device ESP phase and the User ESP phase occur when the end-user goes through the Windows Autopilot deployment after turning on the device for the first time.
- Windows Autopilot for pre-provisioned deployment: Device ESP phase and user ESP phase are split and occur at two different points in time.

    - The IT department, OEM, or reseller handles the device ESP phase. This phase is known as the **Technician flow**. Once the Technician flow is complete, the device is powered down and delivered to the end-user.
    - When the end-user receives the device, they turn it on for the first time, and the device undergoes the user ESP phase. A portion of device ESP also reruns to ensure there are no new applications or policies assigned to the device since the Technician flow ran. This phase is known as the **User flow**.

The deployment is split up between the Technician flow and User flow phases so that the deployment is faster when the end-user receives the device. The deployment is faster when the end-user receives the device because the IT department, OEM, or reseller completed the first portion of the deployment during the Technician flow.

There's one possible disadvantage of Windows Autopilot for pre-provisioned deployment over Windows Autopilot user-driven deployment. If the OEM or reseller is unable to perform the Technician flow, then the device might need to first go to the organization's IT department. The organization's IT department then needs to run the Technician flow once they receive the device followed by delivering the device to the end-user. This extra step prevents the device from being shipped and delivered to the end-user directly from the OEM or reseller. This extra step can lengthen the amount of time before the end-user receives the device.

## Workflow

The following steps are needed to configure and then perform a Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join in Intune:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

Note

Although the workflow is designed for lab or testing scenarios, it can also be used in a production environment. Some of the steps in the workflow are interchangeable and interchanging some of the steps might make more sense in a production environment. For example, the **Create a device group** step followed by the **Register devices as Windows Autopilot devices** step might make more sense in a production environment.

## Walkthrough