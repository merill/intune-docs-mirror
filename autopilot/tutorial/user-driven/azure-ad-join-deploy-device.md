---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra join - Step 8 of 8 - Deploy the device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/azure-ad-join-deploy-device
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
description: How to - Windows Autopilot user-driven Microsoft Entra join - Step 8 of 8 - Deploy the device.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 1b3de0b8-dc5a-efcd-b9d1-bee1651a18ed
document_version_independent_id: 1b3de0b8-dc5a-efcd-b9d1-bee1651a18ed
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/azure-ad-join-deploy-device.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/azure-ad-join-deploy-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/azure-ad-join-deploy-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 9acb4bc8-f5bb-fb01-d4e8-7323fec8194c
---

# Windows Autopilot user-driven Microsoft Entra join - Step 8 of 8 - Deploy the device | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](azure-ad-join-automatic-enrollment)
- Step 2: [Allow users to join devices to Microsoft Entra ID](azure-ad-join-allow-users-to-join)
- Step 3: [Register devices as Windows Autopilot devices](azure-ad-join-register-device)
- Step 4: [Create a device group](azure-ad-join-device-group)
- Step 5: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](azure-ad-join-esp)
- Step 6: [Create and assign Windows Autopilot profile](azure-ad-join-autopilot-profile)
- Step 7: [Assign Windows Autopilot device to a user (optional)](azure-ad-join-assign-device-to-user)

- **Step 8: Deploy the device**

For an overview of the Windows Autopilot user-driven Microsoft Entra join workflow, see [Windows Autopilot user-driven Microsoft Entra join overview](azure-ad-join-workflow#workflow).

## Deploy the device

Once all of the configurations for the Windows Autopilot user-driven Microsoft Entra join deployment are completed in Intune and in Microsoft Entra ID, the next step is to start the Windows Autopilot deployment process on the device. If desired, deploy any additional applications and policies that should run during the Windows Autopilot deployment to a device group that the device is a member of.

To start the Windows Autopilot deployment process on the device, acquire a device that is part of the device group created in the previous [Create a device group](azure-ad-join-device-group) step. Once the device is acquired, follow these steps:

1. If a wired network connection is available, connect the device to the wired network connection.
2. Power on the device.
3. Once the device boots up, one of two things occurs depending on the state of network connectivity:

    - If the device is connected to a wired network and has network connectivity, the device might reboot to apply critical security updates (if available or applicable). After the reboot to apply critical security updates, the Windows Autopilot process begins.
    - If the device isn't connected to a wired network or if it doesn't have network connectivity, it prompts to connect to a network. Connectivity to the Internet is required:

        1. The out-of-box experience (OOBE) begins and a screen asking for a country or region appears. Select the appropriate country or region, and then select **Yes**.
        2. The keyboard screen appears to select a keyboard layout. Select the appropriate keyboard layout, and then select **Yes**.
        3. An additional keyboard layouts screen appears. If needed, select additional keyboard layouts via **Add layout**, or select **Skip** if no additional keyboard layouts are needed.

            Note

            When there's no network connectivity, the device can't download the Windows Autopilot profile to know what country/region and keyboard settings to use. For this reason, when there's no network connectivity, the country/region and keyboard screens appear even if these screens are set to hidden in the Windows Autopilot profile. These settings need to be specified in these screens in order for the network connectivity screens that follow to work properly.
        4. The **Let's connect you to a network** screen appears. At this screen, either plug the device into a wired network (if available), or select and connect to a wireless Wi-Fi network.
        5. Once network connectivity is established, the **Next** button should become available. Select **Next**.
        6. At this point, the device might reboot to apply critical security updates (if available or applicable). After the reboot to apply critical security updates, the Windows Autopilot process begins.

1. Once the Windows Autopilot process begins, the Microsoft Entra sign-in page appears. At the Microsoft Entra sign-in page, if a user was assigned to the device, their username might be pre-populated in this screen. Enter the Microsoft Entra credentials for the user and then select **Next** (Windows 10) or **Sign in** (Windows 11) to sign in. If necessary, proceed through the multi-factor authentication (MFA) screens.
2. After authenticating with Microsoft Entra ID, the Enrollment Status Page (ESP) appears. The Enrollment Status Page (ESP) displays progress during the provisioning process across three phases:

    - **Device preparation** (Device ESP)
    - **Device setup** (Device ESP)
    - **Account setup** (User ESP)

    The first two phases of **Device preparation** and **Device setup** are part of the Device ESP while the final phase of **Account setup** is part of the User ESP.
3. Once **Account setup** and the user ESP process completes, the provisioning process completes, the ESP finishes, and the desktop appears. At this point, the end-user can start using the device.

## Deployment tips

- Before the Windows Autopilot deployment is started, Microsoft recommends having:

    - At least one type of policy and at least one application assigned to the devices.
    - At least one type of policy and at least one application assigned to the users.

    These assignments ensure proper testing of the Windows Autopilot deployment during both the device ESP phase and user ESP phase of the ESP. It might also prevent possible issues when there are either no policies or no applications assigned to the devices or the users.

- Depending on how the Windows Autopilot profile was configured at the **Create and assign Windows Autopilot profile**step, additional screens might appear during the Windows Autopilot deployment appear such as:
    - **Language**/**Country**/**Region** or **Keyboard** screens before the Microsoft Entra sign-in page.
    - **Privacy** screen when the user ESP/**Account setup** begins but before the user is automatically signed in.

- To view and hide detailed progress information in the ESP during the provisioning process:
    - **Windows 10**: To show details, next to the appropriate phase select **Show details**. To hide the details, next to the appropriate phase select **Hide details**.
    - **Windows 11**: To show details, next to the appropriate phase select **∨**. To hide the details, next to the appropriate phase select **∧**.