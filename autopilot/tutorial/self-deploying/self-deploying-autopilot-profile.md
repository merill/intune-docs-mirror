---
layout: Conceptual
title: Windows Autopilot self-deploying mode - Step 5 of 5 - Create and assign self-deploying mode Windows Autopilot profile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/self-deploying/self-deploying-autopilot-profile
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
description: How to - Windows Autopilot self-deploying mode - Step 5 of 5 - Create and assign self-deploying mode Windows Autopilot profile.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: f8fcc99f-7482-e359-f5b4-2c8aed0ab3b6
document_version_independent_id: f8fcc99f-7482-e359-f5b4-2c8aed0ab3b6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/self-deploying/self-deploying-autopilot-profile.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/self-deploying/self-deploying-autopilot-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/self-deploying/self-deploying-autopilot-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae31b7df-ba99-5000-d2b8-36acbb75166c
---

# Windows Autopilot self-deploying mode - Step 5 of 5 - Create and assign self-deploying mode Windows Autopilot profile | Microsoft Learn

Windows Autopilot self-deploying mode steps:

- Step 1: [Set up Windows automatic Intune enrollment](self-deploying-automatic-enrollment)
- Step 2: [Register devices as Windows Autopilot devices](self-deploying-register-device)
- Step 3: [Create a device group](self-deploying-device-group)
- Step 4: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](self-deploying-esp)

- **Step 5: Create and assign Windows Autopilot profile**

- Step 6: [Deploy the device](self-deploying-deploy-device)

For an overview of the Windows Autopilot self-deploying mode workflow, see [Windows Autopilot self-deploying overview](self-deploying-workflow#workflow).

## Create and assign self-deploying Windows Autopilot profile

The Windows Autopilot profile specifies how the device is configured during Windows Setup and what is shown during the out-of-box experience (OOBE).

Tip

For Configuration Manager admins, the Windows Autopilot profile is similar to some of the configuration that takes place during a task sequence via an `unattend.xml` file. The `unattend.xml` file is configured during the **Apply Windows Settings** and **Apply Network Settings** steps. Note however that Windows Autopilot doesn't use `unattend.xml` files.

To create a self-deploying mode Windows Autopilot profile, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Deployment Profiles**.
6. In the **Windows Autopilot deployment profiles** screen, select the **Create Profile** drop down menu and then select **Windows PC**.
7. The **Create profile** screen opens. In the **Basics** page:

    1. Next to **Name**, enter a name for the Windows Autopilot profile.
    2. Next to **Description**, enter a description.
    3. Select **Next**.

        Note

        Microsoft recommends setting the option **Convert all targeted devices to Autopilot** to **Yes**. This tutorial concentrates on new devices where the device is manually imported as a Windows Autopilot device using the hardware hash. However, this option can be helpful when assigning Windows Autopilot profiles to device groups that contain existing devices. For example, this option is helpful when using the [Windows Autopilot for existing devices](../existing-devices/existing-devices-workflow) scenario. With Windows Autopilot for existing devices, existing devices might need to be registered as a Windows Autopilot device after the Windows Autopilot deployment completes. For more information, see [Register device for Windows Autopilot](../existing-devices/register-device).

1. In the **Out-of-box experience (OOBE)** page:

    - For **Deployment mode**, select **Self-Deploying**.
    - **Join to Microsoft Entra ID as** defaults to **Microsoft Entra joined**, is greyed out, and can't be changed. Only **Microsoft Entra joined** is available because self-deploying mode only supports Microsoft Entra join. Self-deploying modes doesn't support Microsoft Entra hybrid join.
    - **Microsoft Software License Terms** defaults to **Hide**, is greyed out, and can't be changed.
    - **Privacy settings** defaults to **Hide**, is greyed out, and can't be changed.
    - **Hide change account options** defaults to **Hide**, is greyed out, and can't be changed.
    - **User account type** defaults to **Standard**, is greyed out, and can't be changed.
    - For **Language (Region)**, select **Operating system default** to use the default language for the operating system being configured. If another language is desired, select the desired language from the drop-down list.
    - For **Automatically configure keyboard**, select **Yes** to skip the keyboard selection page.

        Note

        If users should select their keyboard layout, then select **No** instead. However, the purpose of Windows Autopilot self-deploying mode is to deploy a device with minimal to no user interaction. Setting **Automatically configure keyboard** to **No** requires additional user interaction.
    - For **Apply device name template**, select **No**. Alternatively, **Yes** can be chosen to apply a device name template. Be aware of the following if the name template is selected to **Yes**:

        - Names must be 15 characters or less, and can have letters, numbers, and hyphens.
        - Names can't be all numbers.
        - Use the [%SERIAL% macro](/en-us/windows/client-management/mdm/accounts-csp) to add a hardware-specific serial number.
        - Use the [%RAND:x% macro](/en-us/windows/client-management/mdm/accounts-csp) to add a random string of numbers, where x equals the number of digits to add.

    Note

    If the language/region and keyboard screens are set to hidden, they might still be displayed if there's no network connectivity at the start of the Windows Autopilot deployment. When there's no network connectivity at the start of the deployment, the Windows Autopilot profile, where the settings to hide these screens is defined, hasn't downloaded yet. Once network connectivity is established, the Windows Autopilot profile is downloaded and any additional screen settings should work as expected.

1. Once the options in the **Out-of-box experience (OOBE)** page are configured as desired, select **Next**.
2. In the **Assignments** page:

    1. Under **Included groups**, select **Add groups**.

    Note

    Make sure to add the correct device groups under **Included groups** and not under **Excluded groups**. Accidentally adding the desired device groups under **Excluded groups** prevents devices in those device groups from receiving the Windows Autopilot profile.

    1. In the **Select groups to include** window that opens, select the groups that the Windows Autopilot profile should be assigned to. These device groups are normally the device groups created in the previous **Create device group** step. Once done, select **Select**.
    2. Under **Included groups** &gt; **Groups**, ensure the correct groups are selected, and then select **Next**.
3. In the **Review + Create** page, verify that all settings are set correctly, and then select **Create** to create the Windows Autopilot profile.

## Verify device has a Windows Autopilot profile assigned to it

Before deploying a device, ensure that a Windows Autopilot profile is assigned to a device group that the device is a member of. Windows Autopilot profile assignment to a device can take some time after the Windows Autopilot profile is assigned to the device group or after the device is added to the device group. To verify that the profile is assigned to a device, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen that opens:

    1. Find the desired device that Windows Autopilot deployment profile assignment status needs to be checked.
    2. Once the device is located, its current status is listed under the **Profile status** column. The status has one of the following values:

        - **Not assigned**: A Windows Autopilot deployment profile isn't assigned to the device.
        - **Assigning**: A Windows Autopilot deployment profile is being assigned to the device.
        - **Assigned**: A Windows Autopilot deployment profile is assigned to the device.
        - **Fix pending**: When a hardware change occurs on a device, this status displays while Intune tries to register the new hardware. When the link for the **Fix pending** status is selected, the following message appears:

            **We've detected a hardware change on this device. We're trying to automatically register the new hardware. You don't need to do anything now; the status will be updated at the next check in with the result.**

            If Intune is able to successfully register the new hardware, Intune updates the profile status when the device next checks into Intune. For more information on the **Fix pending** status, see the following articles:

            - [Why is the Windows Autopilot profile not applied after a hardware change occurred on a device?](../../troubleshooting-faq#why-is-the-windows-autopilot-profile-not-applied-after-a-hardware-change-occurred-on-a-device-).
            - [Return of key functionality for Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/return-of-key-functionality-for-windows-autopilot-sign-in-and/ba-p/3583130).
            - [Windows Autopilot motherboard replacement scenario guidance](../../autopilot-motherboard-replacement)
        - **Attention required**: If Intune is unable to register the new hardware after a hardware change occurs on a device, the device can't receive the Windows Autopilot profile until the device is reset and the device re-registers. For more information on this status and how to deregister/re-register a device, see the following articles:

            - [Why is the Windows Autopilot profile not applied after a hardware change occurred on a device?](../../troubleshooting-faq#why-is-the-windows-autopilot-profile-not-applied-after-a-hardware-change-occurred-on-a-device-).
            - [Return of key functionality for Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/return-of-key-functionality-for-windows-autopilot-sign-in-and/ba-p/3583130).
            - [Windows Autopilot motherboard replacement scenario guidance](../../autopilot-motherboard-replacement)
            - [Deregister a device](../../registration-overview#deregister-a-device)

        Before starting the Windows Autopilot deployment process on a device, make sure that in the **Windows Autopilot devices** page:

        - The device's **Profile status** status is **Assigned**.
        - In the properties of the device, **Date assigned** has a value.
        - In the properties of the device, **Assigned profile** displays the expected Windows Autopilot profile.

Note

Intune periodically checks for new devices in the assigned device groups, and then begins the process of assigning profiles to those devices. Due to several different factors involved in the process of Windows Autopilot profile assignment, an estimated time for the assignment can vary from scenario to scenario. These factors can include Microsoft Entra groups, membership rules, hash of a device, Intune and Windows Autopilot services, and internet connection. The assignment time varies depending on all the factors and variables involved in a specific scenario.

## Next step: Deploy the device