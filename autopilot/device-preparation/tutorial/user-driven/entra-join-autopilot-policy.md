---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 6 - Create a Windows Autopilot device preparation policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-autopilot-policy
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
description: Create a Windows Autopilot device preparation policy for a user-driven Microsoft Entra join deployment.
ms.date: 2026-08-25T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: eb5fe99f-2b03-8d96-c4b8-90fe658a6870
document_version_independent_id: eb5fe99f-2b03-8d96-c4b8-90fe658a6870
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-autopilot-policy.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-autopilot-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-autopilot-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f1dfff4-9c18-f554-c9d6-0f3e4638727f
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 6 - Create a Windows Autopilot device preparation policy | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](entra-join-automatic-enrollment)
- Step 2: [Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join)
- Step 3: [Create an assigned device group](entra-join-device-group)
- Step 4: [Create a user group](entra-join-user-group)
- Step 5: [Assign applications and PowerShell scripts to device group](entra-join-assign-apps-scripts)

- **Step 6: Create Windows Autopilot device preparation policy**

- Step 7, option 1: [Add Windows corporate identifier to device](entra-join-corporate-identifier)
- Step 7, option 2: [Associate devices](entra-join-device-association)

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

## Create user-driven Microsoft Entra join Windows Autopilot device preparation policy

The Windows Autopilot policy specifies how the device is configured during Windows Setup and what is shown during the out-of-box experience (OOBE).

To create a user-driven Microsoft Entra join Windows Autopilot device preparation policy, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot device preparation**, select **Device preparation policies**.
6. In the **Device preparation policies** screen, select **Create**, and then select **User Driven**.
7. The **Create profile** screen opens. In the **Introduction** page, select **Next**.
8. In the **Basics** page:

    1. In the **Name** text box, enter a name for the Windows Autopilot device preparation policy.
    2. In the **Description** text box, if desired, enter a description for the Windows Autopilot device preparation policy.
    3. Once a name and description is entered, select **Next**.
9. In the **Device group** page, select the **Search by group name..** box, and then either select or search for the device group created in [Step 3: Create an assigned device group](entra-join-device-group). Make sure to select the device group created in [Step 3: Create an assigned device group](entra-join-device-group) and not the user group created in [Step 4: Create a user group](entra-join-user-group). Once the correct device group is selected, select **Next**.
10. In the **Configuration settings** page, configure the various settings as desired and then select **Next**. For detailed information on the configurations on this page, see the next section Configuration settings.
11. In the **Scope tags** page, select **Next**.

    Note

    **Scope tags** are optional. For this tutorial, scope tags are being skipped and left at the default scope tag. However if a custom scope tag needs to be specified, do so at this page. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags).
12. In the **Assignments** page, select the **Search by group name..** box, and then either select or search for the user group created in [Step 4: Create a user group](entra-join-user-group). Make sure to select the user group created in [Step 4: Create a user group](entra-join-user-group) and not the device group created in [Step 3: Create an assigned device group](entra-join-device-group). Once the correct user group is selected, select **Next**.
13. In the **Review + create** page, review all settings to make sure they're all correct. Once everything is verified, select **Save** to finish creating the Windows Autopilot device preparation policy.

## Configuration settings

The **Configuration settings** page has several configuration options. The following section describes each option in the **Configuration settings** page and what each option should be set to for a Microsoft Entra join Windows Autopilot device preparation deployment.

In the **Configuration settings** page:

1. Expand the **Deployment settings** section by selecting it:

    1. **Deployment mode** - Select **User-driven** in the drop-down menu.
    2. **Deployment type** - Select **Single user** in the drop-down menu.
    3. **Join type** - Select **Microsoft Entra joined** in the drop-down menu.
    4. **User account type** - Select either **Standard User** or **Administrator** as desired by toggling the switch.

    Important

    By default, when a device is enrolled in Microsoft Entra ID, the user is automatically added to the **Administrator** group on the device. If this setting is set to **Standard User**, the Windows Autopilot device preparation deployment ensures that the user is removed from the **Administrator** group before the deployment completes, the user is signed in, and the user reaches the desktop.
2. Expand the **Out-of-box experience settings** section by selecting it.

    1. **Minutes allowed before showing installation error** - Enter the number of minutes allowed before failing a deployment.

        The value entered is for the whole deployment and not for an individual application install or PowerShell script. The acceptable value is an integer between 15 and 720.
    2. **Custom error message** - Enter a custom message to display to the end-user if the deployment fails.
    3. **Allow users to skip setup after multiple attempts** - Select either **Yes** or **No** as desired by toggling the switch.

        Normally after a deployment failure, a **Retry** button is displayed allowing the end-user to retry the deployment. Setting this option as **Yes** also adds a **Continue anyway** button that allows the deployment to just fail, signs the end-user in, and lets them continue to the desktop.
    4. **Show link to diagnostics** - Select either **Yes** or **No** as desired by toggling the switch.

        If there's a deployment failure, setting this option to **Yes** displays a link at the deployment failure page allowing the end-user to retrieve diagnostic logs.

    Important

    The out-of-box experience settings that follow—**Language (Region)**, **Automatically configure keyboard**, **Hide Microsoft Software License Terms**, **Hide privacy settings**, **Hide change account options**, and **Apply device name template**—are **only available to associated devices**. They take effect only when the device is bound to your tenant using [device association](entra-join-device-association), and they have no effect on devices that aren't associated, such as devices onboarded with corporate identifiers only. This limitation doesn't apply to the **Apps** or **Scripts** sections, which apply to all Windows Autopilot device preparation deployments.

    1. **Language (Region)** - Sets the language and region applied to the device during OOBE.
    2. **Automatically configure keyboard** - Skips the keyboard selection page in OOBE.

        Note

        When the device uses a Wi-Fi network connection during OOBE, the language and keyboard selection screens aren't hidden.
    3. **Hide Microsoft Software License Terms** - Hides the Microsoft Software License Terms (EULA) page in OOBE.
    4. **Hide privacy settings** - Hides the privacy settings page in OOBE.
    5. **Hide change account options** - Prevents change account options from appearing on the company sign-in and domain error pages. This setting requires company branding to be configured in Microsoft Entra ID.
    6. **Apply device name template** - Renames the device before enrollment using a custom prefix combined with `%RAND:4%` (four random characters) or `%SERIAL%` (the device serial number). The resulting device name can be up to 63 characters long.
3. Expand the **Apps** section by selecting it:

    The **Apps** section lets you select up to 25 managed applications to install during deployment. Select the essential applications that must be installed before the end user can use the device.

    Important

    The applications selected in this setting should be assigned to the device security group previously specified in the **Device group** page. If applicable, the applications should also be configured to install in the **System** context since it's installed during OOBE when no user is signed in.

    1. Under **Allowed Applications**, select **Add**. The **Select Apps** pane opens.
    2. In the **Select Apps** pane:

        1. Scroll through the list of applications or use the **Search** box to search for desired applications.
        2. Once a desired application is found, select the **Add** button next to the application. The application is added to the list under **Selected Apps**.
        3. Once all of the desired applications are selected, select **Save**.

    All of the selected applications should display under **Allowed Applications**.

    Note

    The following types of applications are supported for use with Windows Autopilot device preparation:

    - [Line-of-business (LOB)](/en-us/intune/app-management/deployment/add-lob-windows).
    - [Win32](/en-us/intune/app-management/deployment/create-win32-package).
    - [Microsoft Store](/en-us/intune/app-management/deployment/add-microsoft-store) - only Microsoft Store apps that support WinGet are supported.
    - [Microsoft 365](/en-us/intune/app-management/deployment/add-microsoft-365-windows).
    - [Enterprise App Catalog](/en-us/intune/app-management/deployment/add-enterprise-catalog-app).

    In addition, Windows Autopilot device preparation supports deploying both Win32 and line-of-business (LOB) applications in the same deployment.
4. Expand the **Scripts** section by selecting it:

    The **Scripts** section allows selection of up to 10 PowerShell scripts to install during the deployment. The PowerShell scripts specified here should be the essential PowerShell scripts that should run on the device before the end-user can start using the device.

    Important

    The PowerShell scripts selected in this setting should be assigned to the device security group previously specified in the **Device group** page. The PowerShell script should also be configured to run in the **System** context since the PowerShell scripts run during OOBE when no user is signed in. The PowerShell script can be set to run in the **System** context by setting the option **Run this script using the logged on credentials** to **No** in the properties of the PowerShell script.

    1. Under **Allowed Scripts**, select **Add**. The **Select Scripts** pane opens.
    2. In the **Select Scripts** pane:

        1. Scroll through the list of PowerShell scripts or use the **Search** box to search for desired PowerShell scripts.
        2. Once a desired PowerShell script is found, select the **Add** button next to the PowerShell script. The PowerShell script is added to the list under **Selected Scripts**.
        3. Once all of the desired PowerShell scripts are selected, select **Save**.

    All of the selected PowerShell scripts should display under **Allowed Scripts**.

Important

If a device is registered as a Windows Autopilot device, whether the Windows Autopilot deployment or the Windows Autopilot device preparation deployment runs depends on the device's association state:

- **The device isn't associated with your tenant.** Windows Autopilot registration takes precedence, and the Windows Autopilot deployment runs instead of the device preparation deployment.
- **The device is associated with your tenant.** Device association takes precedence, and the Windows Autopilot device preparation deployment runs.

To run device preparation on a registered device without associating it, first remove the device's Windows Autopilot registration. For more information, see [Deregister a device](../../../registration-overview#deregister-a-device).

## Policy priority

If multiple Windows Autopilot device preparation policies are assigned to a user, the policy with the highest priority takes precedence. On the **Home** &gt; **Enroll devices | Windows enrollment** &gt; **Device preparation policies** screen, the highest-priority policy appears at the top of the list and has the smallest number in the **Priority** column. To change a policy's priority, drag it to a different position in the list.

A device preparation policy can be assigned to a device or to a user. When a device has both a device-based assignment and a user-based assignment, the **device-based assignment takes precedence**. For example, if you assign a device preparation policy directly to a device when you [pre-associate the device](entra-join-device-association), that policy is used instead of any policy assigned to the user who signs in during enrollment.

## Next step: Onboard trusted devices

After you create the device preparation policy, choose **one** of the following methods to make sure only trusted devices are prepared. You don't need to use both:

- **Corporate identifiers** (optional) - Upload device identifiers so only trusted devices can enroll when personal-device enrollment is blocked.
- **Device association** (optional) - Bind devices to your tenant before enrollment. Associated devices are automatically treated as corporate-owned, so you **don't** need to upload corporate identifiers for them. Device association also enables the out-of-box experience settings that are only available to associated devices.

To use corporate identifiers:

To use device association instead:

Note

Windows Autopilot device preparation only requires [corporate identifiers for Windows](../../overview#corporate-identifiers-for-windows) if Intune enrollment restrictions are being used to block personal device enrollments. If enrollment restrictions aren't blocking personal devices and you aren't using device association, then the next step is to deploy the device.