---
layout: Conceptual
title: Configure Windows Autopilot Profiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/profiles
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
description: Learn how to configure device profiles for Windows Autopilot deployment. Profiles determine the deployment mode, and customize the out-of-box experience.
ms.date: 2026-10-21T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
- essentials-manage
ms.topic: how-to
locale: en-us
document_id: 10ac13d0-abf9-f271-deb9-94c8b2cf6825
document_version_independent_id: 10ac13d0-abf9-f271-deb9-94c8b2cf6825
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/profiles.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/profiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 225f81d3-d2f7-83b7-d57b-387fd734cfa7
---

# Configure Windows Autopilot Profiles | Microsoft Learn

After you create the [device group](enrollment-autopilot), you can apply a Windows Autopilot deployment profile to each device in the group. Deployment profiles determine the deployment mode, and customize the out-of-box experience (OOBE) for end users.

You can create Windows Autopilot profiles by using the following resources:

- [Microsoft 365 admin center](https://admin.microsoft.com/)
- [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431)
- [Intune graph](/en-us/graph/api/resources/intune-graph-overview)

For Intune managed devices, you can only create and assign pre-provisioning, self-deploying, and co-management profiles in Intune.

## Create a Windows Autopilot deployment profile

Use Windows Autopilot deployment profiles to configure Windows Autopilot devices. You can create up to 350 profiles per tenant.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In **Devices | Overview**, under **By platform**, select **Windows**.
4. In **Windows | Windows devices**, under **Device onboarding**, select **Enrollment**.
5. In **Windows | Windows enrollment**, under **Windows Autopilot**, select **Deployment profiles**.
6. In **Windows Autopilot deployment profiles**, select **Create profile** and then select either **Windows PC** or **HoloLens**. This article explains how to set up Windows Autopilot for a Windows PC. For more information about Windows Autopilot and HoloLens, see [Windows Autopilot for HoloLens 2](/en-us/hololens/hololens2-autopilot).
7. In **Create profile**, on the **Basics** page, enter a **Name** and optional **Description**.
8. To automatically register all devices in the assigned groups to Windows Autopilot, set **Convert all targeted devices to Autopilot** to **Yes**.

    All corporate owned, non-Windows Autopilot devices in assigned groups register with the Windows Autopilot deployment service. Personally owned devices aren't registered to Windows Autopilot. Allow 48 hours for the registration to process. When you unenroll and reset the device, Windows Autopilot enrolls it again. After a device is registered in this way, disabling this setting or removing the profile assignment doesn't remove the device from the Windows Autopilot deployment service. You must [remove the device directly](add-devices#delete-windows-autopilot-devices).

    Note

    Using the setting **Convert all targeted devices to Autopilot** doesn't automatically convert existing Microsoft Entra hybrid devices in the assigned groups into a Microsoft Entra device. The setting only registers the devices in the assigned groups for the Windows Autopilot service.
9. Select **Next**.
10. On the **Out-of-box experience (OOBE)** page, for **Deployment mode**, select one of these two options:

    - **User-driven**: Devices with this profile are associated with the user enrolling the device. User credentials are required to enroll the device.
    - **Self-deploying**: Devices with this profile aren't associated with the user enrolling the device. User credentials aren't required to enroll the device. When a device has no user associated with it, user-based compliance policies don't apply to it. When self-deploying mode is used, only compliance policies targeting the device are applied.

    ![Screenshot of OOBE page.](images/create-profile-out-of-box.png)

    Note

    Options that are dimmed or shaded in the selected deployment mode aren't currently supported.
11. In **Join to Microsoft Entra ID as**, select **Microsoft Entra joined**.
12. Configure the following options:

    - **Microsoft Software License Terms**: Select whether to show the EULA to users.
    - **Privacy settings**: Select whether to show privacy settings to users.

        Important

        The default value for the Diagnostic Data setting is set to **Full** during the out-of-box experience. For more information, see [Windows Diagnostics Data](/en-us/windows/privacy/windows-diagnostic-data).

        Warning

        When you hide **Privacy settings**, location services are disabled by default. When privacy settings are hidden and location services are needed, use appropriate policies configured in Intune or other MDM solution to enable location services.
    - **Hide change account options**: Select **Hide** to prevent change account options from displaying on the company sign-in and domain error pages. This option requires [company branding to be configured in Microsoft Entra ID](/en-us/azure/active-directory/fundamentals/customize-branding).
    - **User account type**: Select the user's account type: **Administrator** or **Standard** user. Selecting **Administrator** automatically adds the user joining the device to the local Administrators group. This setting doesn't enable the built-in Administrator account.
    - **Allow pre-provisioned deployment** ([Requirements](pre-provision#requirements)): Select **Yes** to allow pre-provisioning support.

        Note

        When you set **Allow pre-provisioned deployment** to **No**, you can still press the Windows key five times during OOBE to invoke pre-provisioning and progress down that path. However, Intune enforces this setting and a pre-provisioning failure with error code 0x80180005 occurs.
    - **Language (Region)**: Select the language to use for the device. This option is available in all Deployment modes.
    - **Automatically configure keyboard**: If you select a **Language (Region)**, select **Yes** to skip the keyboard selection page. This option is available in all Deployment modes.

        Note

        Language and keyboard settings require Ethernet connectivity. Wi-Fi connectivity isn't supported because of the requirement to select a language, locale, and keyboard to make that Wi-Fi connection.
    - **Apply device name template** (requires Microsoft Entra join type): Select **Yes** to create a template to use when naming a device during enrollment.

        Names must be 15 characters or less, and can have letters, numbers, and hyphens. Names can't be all numbers. Use the [%SERIAL% macro](/en-us/windows/client-management/mdm/accounts-csp) to add a hardware-specific serial number. Or, use the [%RAND:x% macro](/en-us/windows/client-management/mdm/accounts-csp) to add a random string of numbers, where x equals the number of digits to add. You can only provide a prefix for hybrid devices in a [domain join profile](windows-autopilot-hybrid#create-and-assign-a-domain-join-profile).
13. Select **Next**.
14. On the **Assignments** page, select **Selected groups** for **Assign to**.

    ![Screenshot of Assignments page.](images/create-profile-assignments.png)
15. Select **Select groups to include**, and select the groups to include in this profile.
16. To exclude any groups, select **Select groups to exclude**, and select the groups to exclude.

    Note

    When you use the assignment **All Devices**, you can't use exclusions. Attempting to exclude groups while targeting to all devices might cause assignment problems and might require uploading device hashes again.
17. Select **Next**.
18. On the **Review + Create** page, select **Create** to create the profile.

    ![Screenshot of Review page.](images/create-profile-review.png)

### Assignment of Windows Autopilot deployment profiles to devices

Intune periodically checks for new devices in the assigned groups, and then begins the process of assigning deployment profiles to those devices. Due to several factors involved in the process of Windows Autopilot profile assignment, an estimated time for the assignment can vary from scenario to scenario. These factors include Microsoft Entra ID groups, membership rules, hash of a device, Intune and Windows Autopilot service, and internet connection.

Before you deploy a device, ensure that a Windows Autopilot deployment profile is assigned to the device. To ensure the process is complete:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen, monitor the **Profile Status** column for a device that just had a deployment profile assigned to it. The profile status changes from **Unassigned** to **Assigning** and finally to **Assigned**.
7. After the device is showing **Assigned**, open the properties of the device by selecting it.
8. In the device properties pane, ensure that **Date assigned** is populated. If **Date assigned** isn't yet populated, wait until it populates before deploying the device.

## Edit a Windows Autopilot deployment profile

After you create a Windows Autopilot deployment profile, you can edit certain parts of the deployment profile.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In **Windows | Windows enrollment**, under **Windows Autopilot**, select **Deployment profiles**.
6. Select the profile to edit.
7. Select **Properties** to change the name or description of the deployment profile. Select **Save** after making changes.
8. Select **Settings** to make changes to the OOBE settings. Select **Save** after making changes.

    Note

    Changes to the profile apply to devices assigned to that profile. The updated profile doesn't apply to a device that's already enrolled in Intune until after the device is reset and enrolled again.

If you register a device in Windows Autopilot and don't assign a profile, it receives the default Windows Autopilot profile. If a device shouldn't go through Windows Autopilot, remove the Windows Autopilot registration.

## Windows Autopilot profile priority

If you assign a group to multiple Windows Autopilot profiles, the device gets the oldest created profile to resolve the conflict. If no other profile applies to the device and there's a default profile (any Windows Autopilot profile assigned to all devices), the default profile is applied. If you assign a device to a security group that you didn't assign to a Windows Autopilot profile, the device gets the default profile targeted to all devices. To see when a Windows Autopilot profile was created:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Deployment Profiles**.
6. In the **Windows Autopilot deployment profiles** screen, under **Name**, select the Windows Autopilot profile name where you want to view the create date.
7. When the Windows Autopilot deployment profile screen opens, the date the Windows Autopilot deployment profile was created is displayed under **Essentials** and next to **Created**.

## Windows Autopilot deployments report

You can view details about each device deployed through Windows Autopilot in a report. To see the report, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Monitor** &gt; **Windows Autopilot deployment status**. The data is available for 30 days after deployment.

This report is in preview. Only new Intune enrollment events trigger device deployment records. Deployments that don't trigger a new Intune enrollment don't appear in this report. This case includes any kind of reset that maintains enrollment and the user portion of Windows Autopilot pre-provisioning.

## Windows Autopilot profile tutorials

The following articles are tutorials on configuring and assigning a Windows Autopilot deployment profile for each of the Windows Autopilot scenarios using Intune:

- [User-driven Microsoft Entra join: Create and assign user-driven Microsoft Entra join Windows Autopilot profile](tutorial/user-driven/azure-ad-join-autopilot-profile)
- [User-driven Microsoft Entra hybrid join: Create and assign user-driven Microsoft Entra hybrid join Windows Autopilot profile](tutorial/user-driven/hybrid-azure-ad-join-autopilot-profile)
- [Pre-provision Microsoft join: Create and assign a pre-provisioned Microsoft Entra join Windows Autopilot profile](tutorial/pre-provisioning/azure-ad-join-autopilot-profile)
- [Pre-provision Microsoft Entra hybrid join: Create and assign a pre-provisioned Microsoft Entra hybrid join Windows Autopilot profile](tutorial/pre-provisioning/hybrid-azure-ad-join-autopilot-profile)
- [Self-deploying mode: Create and assign self-deploying Windows Autopilot profile](tutorial/self-deploying/self-deploying-autopilot-profile)