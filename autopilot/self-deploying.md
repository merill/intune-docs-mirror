---
layout: Conceptual
title: Windows Autopilot self-deploying mode | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/self-deploying
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
description: Self-deploying mode allows a device to be deployed with little to no user interaction. This mode is designed to deploy Windows as a kiosk, digital signage device, or a shared device.
ms.date: 2024-09-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 437a06dd-58a8-f33f-e6d9-aff9df6d08fc
document_version_independent_id: 437a06dd-58a8-f33f-e6d9-aff9df6d08fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/self-deploying.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: self-deploying
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/self-deploying.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: ec39217f-1a2e-7974-9713-edadf18d10b4
---

# Windows Autopilot self-deploying mode | Microsoft Learn

Note

For more information about using Windows Autopilot to deploy HoloLens 2 devices, see [Windows Autopilot for HoloLens 2](/en-us/hololens/hololens2-autopilot).

Tip

For a guided walkthrough of Windows Autopilot self-deploying mode, see [Step by step tutorial for Windows Autopilot self-deploying mode in Intune](tutorial/self-deploying/self-deploying-workflow).

Windows Autopilot self-deploying mode allows deployment of a device with little to no user interaction. For devices with an Ethernet connection, no user interaction is required. For devices connected via Wi-Fi, the user must only:

- Select the language, locale, and keyboard.
- Make a network connection.

Self-deploying mode provides all the following features:

- Joins the device to Microsoft Entra ID.
- Enrolls the device in Intune or another mobile device management (MDM) service using Microsoft Entra ID for automatic MDM enrollment.
- Makes sure that all policies, applications, certificates, and networking profiles are provisioned on the device.
- Uses the Enrollment Status Page to prevent access until the device is fully provisioned.

Note

Windows Autopilot self-deploying mode is only supported for Microsoft Entra join devices. Windows Autopilot self-deploying mode isn't supported for Microsoft Entra hybrid join devices.

Self-deploying mode allows deployment of a Windows device as a kiosk, digital signage device, or a shared device.

Windows Autopilot now has a kiosk mode that supports Kiosk Browser, Microsoft Store apps, and specific versions of Microsoft Edge.

The [Kiosk Browser](https://www.microsoft.com/p/kiosk-browser/9ngb5s5xg2kp?rtc=1&amp;activetab=pivot:overviewtab) can be used when setting up a kiosk device. This app is built on Microsoft Edge and can be used to create a tailored, MDM-managed browsing experience.

The device configuration can be automated by combining self-deploying mode with MDM policies. Use the MDM policies to create a local account configured to automatically sign in. For more information, see:

- [Simplifying kiosk management for IT with Windows 10](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/simplifying-kiosk-management-for-it-with-windows-10/ba-p/187691).
- [Set up a kiosk or digital sign in Intune or other MDM service](/en-us/windows/configuration/setup-kiosk-digital-signage#set-up-a-kiosk-or-digital-sign-in-intune-or-other-mdm-service).

Optionally, a [device-only subscription](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/microsoft-intune-announces-device-only-subscription-for-shared/ba-p/280817) service can be used that helps manage devices that aren't affiliated with specific users. The Intune device SKU is licensed per device per month.

Note

Intune doesn't automatically configure a primary user when using self-deploying mode in Windows Autopilot to provision a Windows device. Some Intune capabilities rely on a primary user being set on a device. These features include user self-service BitLocker recovery key retrieval and using the Company Portal to install software **assigned to users**. Using self-provisioning mode for Windows Autopilot doesn't preclude a licensed user from logging into the device and using features entitled to that user such as Conditional Access. For more information, see [Windows Autopilot scenarios and capabilities](windows-autopilot-scenarios).

If desired, a primary user can be manually set after device provisioning via the Intune admin center. For more information, see [Change a devices primary user](/en-us/intune/intune-service/remote-actions/find-primary-user#change-a-devices-primary-user).

## Requirements

Important

A device can't automatically re-enroll through Windows Autopilot after an initial deployment with self-deploying mode. Instead, delete the device record in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). From the Microsoft Intune admin center, select **Devices** &gt; **All devices** &gt; select the devices to delete &gt; **Delete**. For more information, see [Updates to the Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/updates-to-the-windows-autopilot-sign-in-and-deployment/ba-p/2848452).

Self-deploying mode uses a device's Trusted Platform Module (TPM) 2.0 hardware to authenticate the device into an organization's Microsoft Entra tenant. Therefore, devices without TPM 2.0 can't be used with this mode. Devices must also support TPM device attestation. All new Windows devices should meet these requirements. The TPM attestation process also requires access to a set of HTTPS URLs that are unique for each TPM provider. For more information, see the entry for Windows Autopilot self-Deploying mode and Windows Autopilot pre-provisioning in [Networking requirements](requirements?tabs=networking#windows-autopilot-self-deploying-mode-and-windows-autopilot-pre-provisioning). For Windows Autopilot software requirements, see [Windows Autopilot software requirements](requirements?tabs=software).

Important

If a self-deploying mode deployment is attempted on a device that doesn't have support for TPM 2.0 or on a virtual machine, the process fails when verifying the device with an **0x800705B4** timeout error. This limitation includes Hyper-V virtual TPMs.

See [Windows Autopilot known issues](known-issues) and [Troubleshooting Windows Autopilot device import and enrollment](troubleshooting-faq#troubleshooting-windows-autopilot-device-import-and-enrollment) to review other known errors and solutions.

An organization-specific logo and organization name can be displayed during the Windows Autopilot process. To do so, Microsoft Entra Company Branding must be configured with the images and text that need to be displayed. See [Quickstart: Add company branding to your sign-in page in Microsoft Entra ID](/en-us/azure/active-directory/fundamentals/customize-branding) for more details.

## Step by step

To deploy in self-deploying mode Windows Autopilot, the following preparation steps need to be completed:

1. Create a Windows Autopilot profile for self-deploying mode with the desired settings. In Microsoft Intune, this mode is explicitly chosen when creating the profile. It isn't possible to create a profile in the Microsoft Store for Business or Partner Center for self-deploying mode.
2. If using Intune, create a device group in Microsoft Entra ID and assign the Windows Autopilot profile to that group. Ensure that the profile is assigned to the device before attempting to deploy that device.
3. Boot the device, connecting it to Wi-Fi if necessary, then wait for the provisioning process to complete.

## Validation

When using Windows Autopilot to deploy in self-deploying mode, the following end-user experience should be observed:

- Once the device connects to a network, the Windows Autopilot profile is downloaded.
- If connected to Ethernet, and the Windows Autopilot profile is configured to skip them, the following pages aren't displayed:

    - Language and locale.
    - Keyboard layout.

    Otherwise, manual steps are required:

    - If multiple languages are preinstalled in Windows, the user must pick a language.
    - The user must pick a locale and a keyboard layout, and optionally a second keyboard layout.
- If connected via Ethernet, no network prompt is expected. If no Ethernet connection is available and Wi-Fi is built in, the user needs to connect to a wireless network.
- Windows checks for critical out-of-box experience (OOBE) updates, and if any are available they're automatically installed, rebooting if necessary.
- The device joins Microsoft Entra ID.
- The device enrolls in Intune or other configured MDM services after it joins Microsoft Entra ID.
- The [enrollment status page](enrollment-status) is displayed.
- Depending on the device settings deployed, the device will either:

    - Remain at the sign-on screen, where any member of the organization can sign in by specifying their Microsoft Entra credentials.
    - Automatically sign in as a local account, for devices configured as a kiosk or digital signage.

Note

Deploying Exchange ActiveSync (EAS) policies using self-deploying mode for kiosk deployments causes autologon functionality to fail.

In case the observed results don't match these expectations, consult the [Troubleshooting Windows Autopilot overview](troubleshooting-faq#troubleshooting-windows-autopilot-overview) documentation.