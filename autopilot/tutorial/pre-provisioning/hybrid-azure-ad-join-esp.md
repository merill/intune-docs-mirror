---
layout: Conceptual
title: Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 6 of 11 - Configure and assign the Enrollment Status Page (ESP) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-esp
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
description: How to - Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 6 of 11 - Configure and assign the Enrollment Status Page (ESP).
ms.date: 2025-09-24T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 80adb6a7-4095-196c-eec8-4676340f5da2
document_version_independent_id: 80adb6a7-4095-196c-eec8-4676340f5da2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-esp.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-esp
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-esp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f4636829-a6f5-cee1-dc9f-407138a37bbc
---

# Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 6 of 11 - Configure and assign the Enrollment Status Page (ESP) | Microsoft Learn

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)

- **Step 6: Configure and assign Windows Autopilot Enrollment Status Page (ESP)**

- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

For an overview of the Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join workflow, see [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If an ESP is already configured, assigned, and uses the same settings for the pre-provisioned Microsoft Entra hybrid join scenario, skip this step and move on to [Step 7: Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile).

## The Enrollment Status Page (ESP)

The main feature of the Enrollment Status Page (ESP) is to display progress and current status to the end user while the device is being set up and enrolled via the Windows Autopilot process. The other main feature of the ESP is to block a user from signing in and using the device until all required policies and applications are installed. Multiple ESP profiles can be created with different settings and assigned appropriately based on different needs and scenarios.

Out of box there's a default ESP that is assigned to all devices. The default setting in the default ESP is to not show app and profile progress during the Windows Autopilot process. However, Microsoft recommends changing this default via a separate custom ESP to show app and profile progress. Enabling and configuring an ESP allows end users to properly see the progress of their device being set up and prevents them using the device until the device is fully configured and provisioned. A user signing in to the device before being fully configured and provisioned can cause issues.

The ESP has two phases:

- **Device ESP** - The portion of the ESP that runs during the OOBE process and applies device policies and installs device applications.
- **User ESP** - The portion of the ESP that sets up user account, applies user policies, and installs user applications.

Device ESP runs first followed by the User ESP.

Tip

For Configuration Manager admins, an ESP is similar and analogous to Configuration Manager client settings.

## Windows Autopilot Enrollment Status Page (ESP) configuration options

When the Enrollment Status Page (ESP) is configured, it has several options that can be configured to meet the needs of the organization. The following lists the different options and their possible configurations:

- **Show app and profile configuration progress**:

    - **No**: The enrollment status page doesn't appear during device setup. To disable the configuration progress to users during the provisioning process, select **No**.
    - **Yes**: The enrollment status page appears during device setup. More options become available when this option is selected. Microsoft recommends selecting **Yes** and enabling displaying the enrollment status page configuration progress when using Windows Autopilot.
- **Show an error when installation takes longer than specified number of minutes**:

    - The default time-out is 60 minutes. Enter a higher value if more time is needed to install applications on the devices.
- **Show custom message when time limit or error occur**:

    - **No**: The default message is shown to users when an error occurs. That message is: **Setup could not be completed. Please try again or contact your support person for help.**
    - **Yes**: A custom message is shown to users when an error occurs. Enter a custom message in the provided text box.
- **Turn on log collection and diagnostics page for end users**:

    - **No**: The collect logs button isn't shown to users when an installation error occurs. The Windows Autopilot diagnostics page isn't shown on devices running Windows 11.
    - **Yes**: The collect logs button is shown to users when an installation error occurs. The Windows Autopilot diagnostics page is shown on devices running Windows 11. Logs and diagnostics might aid with troubleshooting. For this reason, Microsoft recommends enabling this option.
- **Only show page to devices provisioned by out-of-box experience (OOBE)**:

    - **No**: The enrollment status page (ESP) is shown during the device phase and the out-of-box experience (OOBE). The page is also shown during the user phase to every user who signs into the device for the first time.
    - **Yes**: The enrollment status page (ESP) is shown during the device phase and the OOBE. The page is also shown during the user phase, but only to the first user who signs into the device. It isn't shown to subsequent users who sign in to the device.
- **Install Windows quality updates (might restart the device)**: Use this setting to control checking and installation from Windows Updates the available quality updates, also known as monthly security update releases. The available options are:

    - **Yes**: At the end of OOBE, the device checks Windows Updates for any missing and applicable monthly security update releases. During this process, if updates are found, a page is displayed to the user showing update progress.
    - **No**: Monthly security update releases aren't installed during OOBE and the device instead continues to the desktop as usual. Messages regarding installation of monthly security update releases aren't displayed since they aren't installed.

        Important

        - This option is only supported for [currently supported versions of Windows 11](/en-us/windows/release-health/windows11-release-information).
        - When this option is enabled, monthly security update releases are installed during OOBE after the ESP completes.
        - For important detailed information regarding this option, see [Windows monthly security update release details](/en-us/intune/intune-service/enrollment/windows-enrollment-status#windows-monthly-security-update-release-details).
        - If this option is set to **No**, make sure to set the option **Block device use until all apps and profiles are installed** is set to **Yes** to ensure that monthly security update releases aren't installed. For more information, see [Windows monthly security update release details](/en-us/intune/intune-service/enrollment/windows-enrollment-status#windows-monthly-security-update-release-details).
- **Block device use until all apps and profiles are installed**:

    - **No**: Users can leave the ESP before Intune is finished setting up the device.

        Important

        Don't set this option to **No** if the option **Install Windows quality updates (might restart the device)** is set to **No**. For more information, see [Windows monthly security update release details](/en-us/intune/intune-service/enrollment/windows-enrollment-status#windows-monthly-security-update-release-details).
    - **Yes**: Users can't leave the ESP until Intune is done setting up the device.

        Enabling this option unlocks the following additional options:

        - **Allow users to reset device if installation error occurs**:

            - **No**: The ESP doesn't give users the option to reset theirs devices when an installation fails.
            - **Yes**: The ESP gives users the option to reset their devices when an installation fails.
        - **Allow users to use device if installation error occurs**:

            - **No**: The ESP doesn't give users the option to bypass the ESP when an installation fails.
            - **Yes**: The ESP gives users the option to bypass the ESP and use their devices when an installation fails.
        - **Block device use until these required apps are installed if they are assigned to the user/device**:

            - **All**: All assigned apps must be installed before users can use their devices.
            - **Selected**: Selected apps must be installed before users can use their devices. After enabling this option, select **Select apps** to select the managed apps from Intune that are required to be installed before users can use their device.

## Configure and assign the Enrollment Status Page (ESP)

To configure and assign the Windows Autopilot Enrollment Status Page (ESP), follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.

1 In the **Devices | Overview** screen, under **By platform**, select **Windows**.

1. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
2. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Enrollment Status Page**.
3. In the **Enrollment Status Page** screen that opens, select **Create**.
4. The **Create profile** screen opens. In the **Basics** page:

    1. Next to **Name**, enter a name for the ESP profile.
    2. Next to **Description**, enter a description.
    3. Select **Next**.
5. In the **Settings** page, toggle the option **Show app and profile configuration progress** to **Yes**.

    1. After the option **Show app and profile configuration progress** is toggled to **Yes**, several new options will appear. Configure these options based on the desired behavior for the ESP as described in the section Windows Autopilot Enrollment Status Page (ESP) configuration options:
    2. Once the different ESP options under the **Settings** page are configured as desired, select **Next**.
6. In the **Assignments** page:

    1. Under **Included groups**, select **Add groups**.
    2. In the **Select groups to include** window that opens, select the device groups to target the ESP profile. The device groups selected would normally be the device groups created in the **Create device group** step.
    3. After selecting the device group, select **Select** to close the **Select groups to include** window.

        Tip

        After selecting the device groups, the **Edit filter** option can be selected on each device group added to the assignment to further refine what devices are targeted for the ESP profile. For example, further filtering can be useful if some of the devices that are members in the device groups selected need to be excluded.
    4. Select **Next**.

    Note

    An ESP is assigned to a device group and not directly to individual devices. To assign an ESP to a specific device, the device must be a member of a device group that has an ESP assigned to it.
7. In the **Scope tags** page, select **Next**.

    Note

    **Scope tags** are optional and are a method to control who has access to the ESP configuration. For this tutorial, scope tags are being skipped and left at the default scope tag. However if a custom scope tag needs to be specified, do so at this screen. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags).
8. In the **Review + create** page, verify that the settings are correct and configured as desired. Once verified, select **Create** to save the changes and assign the ESP profile.

## Next step: Create and assign pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile