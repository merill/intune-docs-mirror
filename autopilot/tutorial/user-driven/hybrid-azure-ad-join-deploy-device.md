---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra hybrid join - Step 10 of 10 - Deploy the device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-deploy-device
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
description: How to - Windows Autopilot user-driven Microsoft Entra hybrid join - Step 10 of 10 - Deploy the device.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: db2c0003-eac2-61bc-0817-77acf32366a5
document_version_independent_id: db2c0003-eac2-61bc-0817-77acf32366a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/hybrid-azure-ad-join-deploy-device.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/hybrid-azure-ad-join-deploy-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/hybrid-azure-ad-join-deploy-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 3797571a-9c95-893a-45a4-e09fb34f4fc1
---

# Windows Autopilot user-driven Microsoft Entra hybrid join - Step 10 of 10 - Deploy the device | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)

- **Step 10: Deploy the device**

For an overview of the Windows Autopilot user-driven Microsoft Entra hybrid join workflow, see [Windows Autopilot user-driven Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

## Deploy the device

Once all of the configurations for the Windows Autopilot user-driven Microsoft Entra hybrid join deployment are completed in Intune and in Microsoft Entra ID, the next step is to start the Windows Autopilot deployment process on the device. If desired, deploy any additional applications and policies that should run during the Windows Autopilot deployment to a device group that the device is a member of.

Important

The Microsoft Entra hybrid join process requires connectivity to both the Internet and a domain controller. If the connected network doesn't have connectivity to a domain controller, a solution such as a VPN that has connectivity to a domain controller is required.

To start the Windows Autopilot deployment process on the device, acquire a device that is part of the device group created in the previous [Create a device group](hybrid-azure-ad-join-device-group) step. Once the device is acquired, follow these steps:

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

1. Once the Windows Autopilot process begins, the Microsoft Entra sign-in page appears. At the Microsoft Entra sign-in page, if a user was assigned to the device, their username might be pre-populated in this screen. Enter the Microsoft Entra credentials for the user.

    If on-premises domain end-user credentials are different from Microsoft Entra end-user credentials, make sure that **Microsoft Entra end-user credentials** are used to sign in at this step. Don't use on-premises credentials to sign in at this step.
2. Once the credentials are entered, select **Next** (Windows 10) or **Sign in** (Windows 11) to sign in. If necessary, proceed through the multi-factor authentication (MFA) screens.
3. After authenticating with Microsoft Entra ID, the Enrollment Status Page (ESP) appears. The ESP displays progress during the provisioning process across three phases:

    - **Device preparation** (Device ESP)
    - **Device setup** (Device ESP)
    - **Account setup** (User ESP)

    The first two phases of **Device preparation** and **Device setup** are part of the Device ESP while the final phase of **Account setup** is part of the User ESP.
4. Once the **Device setup** phase of the Device ESP is complete, user ESP begins and the **User setup** phase starts. The ESP is temporarily dismissed and the Windows sign-on screen appears:

    1. Enter the keystroke CTRL + ALT + DEL to initiate Windows sign-on.
    2. Enter the on-premises domain credentials for the end-user.

        If on-premises domain end-user credentials are different from Microsoft Entra end-user credentials, make sure that the **on-premises domain end-user credentials** are used to sign in to the device at this step. Don't use the Microsoft Entra end-user credentials to attempt to sign in to the device at this step.
    3. Select ENTER on the keyboard to sign the end-user into the device.
5. The Enrollment Status Page (ESP) appears again and the **Account setup** phase of the user ESP continues.

    1. After a short period of time, the Microsoft Entra sign-in page might appear. Sign in with the end-user's Microsoft Entra credentials.

        If on-premises domain end-user credentials are different from Microsoft Entra end-user credentials, make sure that **Microsoft Entra end-user credentials** are used to sign in at this step. Don't use on-premises credentials to sign in at this step.
    2. Once the credentials are entered, select **Next**.
    3. The **Stay signed in to all your apps** screen appears. Make sure that the option **Allow my organization to manage my device** is selected, and then select **OK**.
    4. The **You're all set!** screen appears. Select **Done**.

        Note

        Under certain circumstances, the Microsoft Entra sign-in and subsequent pages might not appear and the end-user might be automatically signed in to Microsoft Entra ID. For example, if using [Active Directory Federation Services (ADFS)](/en-us/windows-server/identity/active-directory-federation-services) and [single sign-on (SSO)](/en-us/windows-server/identity/ad-fs/operations/ad-fs-single-sign-on-settings). If the end-user is automatically signed in to Microsoft Entra ID, then the Windows Autopilot deployment will proceed on to the next step automatically.
6. Once **Account setup** and the user ESP process completes, the provisioning process completes and the ESP finishes. Select the **Sign out** button to dismiss the ESP and go to the Windows sign-on screen. At this point, the end-user can sign in to the device using their on-premises domain end-user credentials and start using the device.

## Deployment tips

- Before the Windows Autopilot deployment is started, Microsoft recommends having:

    - At least one type of policy and at least one application assigned to the devices.
    - At least one type of policy and at least one application assigned to the users.

    These assignments ensure proper testing of the Windows Autopilot deployment during both the device ESP phase and user ESP phase of the ESP. It might also prevent possible issues when there are either no policies or no applications assigned to the devices or the users.

- Depending on how the Windows Autopilot profile was configured at the **Create and assign Windows Autopilot profile**step, additional screens might appear during the Windows Autopilot deployment such as:
    - **Language**/**Country**/**Region** or **Keyboard** screens before the Microsoft Entra sign-in page.
    - **Privacy** screen when the user ESP/**Account** setup begins but before the Windows sign-on screen appears.

- If the device is left alone with no interaction during the **Account setup** phase of the ESP, the device might enter the Windows lock screen. If the device does enter the Windows lock screen during **Account setup** of the ESP, unlock the device by entering the keystroke CTRL + ALT + DEL, entering the on-premises domain credentials for the end-user, and then selecting ENTER on the keyboard. Unlocking the device should go back to the Enrollment Status Page (ESP) and display the current progress of **Account setup**.

- To view and hide detailed progress information in the ESP during the provisioning process:
    - **Windows 10**: To show details, next to the appropriate phase select **Show details**. To hide the details, next to the appropriate phase select **Hide details**.
    - **Windows 11**: To show details, next to the appropriate phase select **∨**. To hide the details, next to the appropriate phase select **∧**.