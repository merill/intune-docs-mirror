---
layout: Conceptual
title: Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 7 of 11 - Create and assign pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-autopilot-profile
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
description: How to - Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 7 of 11 - Create and assign hybrid pre-provisioned Microsoft Entra join Windows Autopilot profile.
ms.date: 2024-09-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: d784d605-8d47-4fc7-1435-642e3ee961a1
document_version_independent_id: d784d605-8d47-4fc7-1435-642e3ee961a1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-autopilot-profile.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-autopilot-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-autopilot-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 4680460c-1bf2-e301-1980-d0960813369f
---

# Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 7 of 11 - Create and assign pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile | Microsoft Learn

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)

- **Step 7: Create and assign Microsoft Entra hybrid join Windows Autopilot profile**

- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

For an overview of the Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join workflow, see [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

## Create and assign a pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile

The Windows Autopilot profile specifies how the device is configured during Windows Setup and what is shown during the out-of-box experience (OOBE).

The difference between a Microsoft Entra join and a Microsoft Entra hybrid join is that the Microsoft Entra hybrid join scenario joins both an on-premises domain and Microsoft Entra ID during Windows Autopilot. The pre-provisioned Microsoft Entra join scenario only joins Microsoft Entra ID during Windows Autopilot.

Tip

For Configuration Manager admins, the Windows Autopilot profile is similar to some of the configuration that takes place during a task sequence via an `unattend.xml` file. The unattend.xml file is configured during the **Apply Windows Settings** and **Apply Network Settings** steps. Note however that Windows Autopilot doesn't use `unattend.xml` files.

To create a pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile, follow these steps:

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

    - For **Deployment mode**, select **User-driven**.
    - For **Join to Microsoft Entra ID as**, select **Microsoft Entra hybrid joined**. After this option is selected, several the options underneath this option will change.
    - For **Skip AD connectivity check**, select **No**. This section of the tutorial assumes that the device undergoing Windows Autopilot is an on-premises internal client and that has direct connectivity to the on-premises domain and domain controllers. For off-premise/Internet scenarios where VPN connectivity is required, see Off-premises/Internet scenarios and VPN connectivity.
    - For **Microsoft Software License Terms**, select **Hide** to skip the EULA page.
    - For **Privacy settings**, select **Hide** to skip the privacy settings.
    - For **Hide change account options**, select **Hide**.
    - For **User account type**, select the desired account type for the user (**Administrator** or **Standard** user). If **Administrator** is chosen, the user is added to the local Admin group.
    - For **Allow pre-provisioned deployment**, select **Yes**.
    - For **Language (Region)**, select **Operating system default** to use the default language for the operating system being configured. If another language is desired, select the desired language from the drop-down list.
    - For **Automatically configure keyboard**, select **Yes** to skip the keyboard selection page.
    - The **Apply device name template** is greyed out for Microsoft Entra hybrid join scenarios. Although not as robust, device names can be specified during the [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile) step.

    Note

    The above settings are selected to minimize needed user interaction during device setup. However, some of the settings that are hidden can instead be shown as desired. For example, some regions might require that **Privacy settings** always be shown.

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

## Off-premises/Internet scenarios and VPN connectivity

Windows Autopilot for pre-provisioned Microsoft Entra hybrid join supports off-premises/Internet scenarios where direct connectivity to Active directory and domain controllers isn't available. However, an off-premises/Internet scenario doesn't eliminate the need for connectivity to Active Directory and a domain controller during the domain join. In an off-premises/Internet scenario, connectivity to Active Directory and a domain controller can be established via a VPN connection during the Windows Autopilot process.

For off-premises/Internet scenarios requiring VPN connectivity, the only change in the Windows Autopilot profile would be in the setting **Skip AD connectivity check**. In the Create and assign pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile section, the **Skip AD connectivity check** setting should be set to **Yes** instead of to **No**. Setting this option to **Yes** prevents the deployment from failing since there's no direct connectivity to Active Directory and domain controllers until the VPN connection is established.

In addition to changing the **Skip AD connectivity check** setting to **Yes** in the Windows Autopilot profile, VPN support also relies on the following requirements:

- The VPN solution can be deployed and installed with Intune.
- The VPN solution needs to support one of the following options:
    - Lets the user manually establish a VPN connection from the Windows sign-in screen.
    - Automatically establishes a VPN connection as needed.

The VPN solution would need to be installed and configured via Intune during the Windows Autopilot process. Configuration would need to include deploying any required device certificates if needed by the VPN solution. Once the VPN solution is installed and configured on the device, the VPN connection can be established, either automatically or manually by the user, at which point the domain join can occur. For more information and support on VPN solutions during Windows Autopilot, consult the respective VPN vendor.

Note

Some VPN configurations aren't supported because the connection isn't initiated until the user signs into Windows. Unsupported VPN configurations include:

- VPN solutions that use user certificates
- Non-Microsoft UWP VPN plug-ins from the Windows Store

## Next step: Configure and assign domain join profile