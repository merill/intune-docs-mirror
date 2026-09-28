---
layout: Conceptual
title: Windows Autopilot device preparation in automatic mode for Windows 365 - Step 4 of 6 - Create a Windows Autopilot device preparation policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/automatic/automatic-autopilot-policy
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
description: How to - Windows Autopilot device preparation in automatic mode for Windows 365 - Step 4 of 6 - Create a Windows Autopilot device preparation policy.
ms.date: 2025-06-11T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: e13bf4ae-776d-1003-07e0-8e5b4c713583
document_version_independent_id: e13bf4ae-776d-1003-07e0-8e5b4c713583
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/automatic/automatic-autopilot-policy.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/automatic/automatic-autopilot-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/automatic/automatic-autopilot-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/72cb4d1c-66f7-4281-99d5-e04a64d084fc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d9ebaec0-4879-449e-9781-0afdce99fe0a
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e31936aa-b6d3-3e75-e3b4-e85c98749bbb
---

# Windows Autopilot device preparation in automatic mode for Windows 365 - Step 4 of 6 - Create a Windows Autopilot device preparation policy | Microsoft Learn

Windows Autopilot device preparation in automatic mode for Windows 365 steps:

- Step 1: [Set up Windows automatic Intune enrollment](automatic-automatic-enrollment)
- Step 2: [Create an assigned device group](automatic-device-group)
- Step 3: [Assign applications and PowerShell scripts to device group](automatic-assign-apps-scripts)

- **Step 4: Create Windows Autopilot device preparation policy**

- Step 5: [Create a Cloud PC provisioning policy](automatic-cloud-pc-provisioning-policy)
- Step 6: [Monitor the deployment](automatic-monitor)

For an overview of the Windows Autopilot device preparation in automatic mode for Windows 365 workflow, see [Windows Autopilot device preparation in automatic mode for Windows 365 overview](automatic-workflow#workflow).

## Create an automatic mode for Windows 365 Windows Autopilot device preparation policy

The Windows Autopilot policy specifies how the device is configured during Windows Setup and what is shown during the out-of-box experience (OOBE).

To create an automatic mode for Windows 365 Windows Autopilot device preparation policy, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot device preparation**, select **Device preparation policies**.
6. In the **Device preparation policies** screen, select **Create**, and then select **Automatic**.
7. The **Create profile** screen opens. In the **Introduction** page, select **Next**.
8. In the **Basics** page:

    1. In the **Name** text box, enter a name for the Windows Autopilot device preparation policy.
    2. In the **Description** text box, if desired, enter a description for the Windows Autopilot device preparation policy.
    3. Once a name and description is entered, select **Next**.
9. In the **Device group** page, select the **Search by group name..** box, and then either select or search for the device group created in [Step 3: Create an assigned device group](automatic-device-group). Once the correct device group is selected, select **Next**.
10. In the **Configuration settings** page:

    1. The **Apps** section allows selection of up to 10 managed applications reference with the deployment. The applications specified here should be the essential applications that should be installed on the device before the end-user can start using the device. Under the **Apps** section:

        1. Select **Add**. The **Select Apps** pane opens.

            1. In the **Select Apps** pane:
            2. Scroll through the list of applications or use the **Search** box to search for desired applications.
            3. Once a desired application is found, select the **Add** button next to the application. The application is added to the list under **Selected Apps**.
            4. Once all of the desired applications are selected, select **Save**.

        All of the selected applications should display under **Allowed Applications**.

        Important

        The applications selected in this setting should be assigned to the device security group previously specified in the **Device group** page. If applicable, the applications should also be configured to install in the **System** context since it's installed during OOBE when no user is signed in.

        Note

        The following types of applications are supported for use with Windows Autopilot device preparation:

        - [Line-of-business (LOB)](/en-us/intune/app-management/deployment/add-lob-windows).
        - [Win32](/en-us/intune/app-management/deployment/create-win32-package).
        - [Microsoft Store](/en-us/intune/app-management/deployment/add-microsoft-store) - only Microsoft Store apps that support WinGet are supported.
        - [Microsoft 365](/en-us/intune/app-management/deployment/add-microsoft-365-windows).

        In addition, Windows Autopilot device preparation supports deploying both Win32 and line-of-business (LOB) applications in the same deployment.
    2. The **Scripts** section allows selection of up to 10 PowerShell scripts to install during the deployment. The PowerShell scripts specified here should be the essential PowerShell scripts that should run on the device before the end-user can start using the device. Under the **Scripts** section:

        1. Select **Add**. The **Select Scripts** pane opens.
        2. In the **Select Scripts** pane:

            1. Scroll through the list of PowerShell scripts or use the **Search** box to search for desired PowerShell scripts.
            2. Once a desired PowerShell script is found, select the **Add** button next to the PowerShell script. The PowerShell script is added to the list under **Selected Scripts**.
            3. Once all of the desired PowerShell scripts are selected, select **Save**.

        All of the selected PowerShell scripts should display under **Allowed Scripts**.

    Important

    The PowerShell scripts selected in this setting should be assigned to the device security group previously specified in the **Device group** page. The PowerShell script should also be configured to run in the **System** context since the PowerShell scripts run during OOBE when no user is signed in. The PowerShell script can be set to run in the **System** context by setting the option **Run this script using the logged on credentials** to **No** in the properties of the PowerShell script.

    1. Once all of the desired **Apps** and **Scripts** are selected, select **Next**.
11. In the **Scope tags** page, select **Next**.

    Note

    **Scope tags** are optional. For this tutorial, scope tags are being skipped and left at the default scope tag. However if a custom scope tag needs to be specified, do so at this page. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags).
12. In the **Review + create** page, review all settings to make sure they're all correct. Once everything is verified, select **Save** to finish creating the Windows Autopilot device preparation policy.

Tip

When a Windows Autopilot device preparation policy for automatic mode is created, there's no **Assignments** page for assigning the policy. Instead, the assignment is taken care of when creating the Cloud PC provisioning policy during [Step 5: Create a Cloud PC provisioning policy](automatic-cloud-pc-provisioning-policy).

## Next step: Create a Cloud PC provisioning policy