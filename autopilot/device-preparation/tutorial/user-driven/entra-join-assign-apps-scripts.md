---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 5 of 7 - Assign applications and PowerShell scripts to device group | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-assign-apps-scripts
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
description: How to - Windows Autopilot device preparation user-driven Microsoft Entra join - Step 5 of 7 - Assign applications and PowerShell scripts to device group.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 94035220-16f4-15eb-1e77-4394f977cc61
document_version_independent_id: 94035220-16f4-15eb-1e77-4394f977cc61
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-assign-apps-scripts.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-assign-apps-scripts
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-assign-apps-scripts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 176036b8-720e-9a19-d8ec-8b5c12ccb6d1
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 5 of 7 - Assign applications and PowerShell scripts to device group | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](entra-join-automatic-enrollment)
- Step 2: [Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join)
- Step 3: [Create an assigned device group](entra-join-device-group)
- Step 4: [Create a user group](entra-join-user-group)

- **Step 5: Assign applications and PowerShell scripts to device group**

- Step 6: [Create Windows Autopilot device preparation policy](entra-join-autopilot-policy)
- Step 7, option 1: [Add Windows corporate identifier to device](entra-join-corporate-identifier)
- Step 7, option 2: [Associate devices](entra-join-device-association)

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

## Assign applications and PowerShell scripts to device group

During the out-of-box experience (OOBE) experience before the end-user is signed in for the first time, Windows Autopilot device preparation allows deployment of up to:

- 25 managed applications
- 10 PowerShell scripts

The applications and PowerShell scripts specified should be the essential applications to install and the essential PowerShell scripts to run before the end-user can start using the device.

Any applications installed or PowerShell scripts that run during a Windows Autopilot device preparation deployment should be configured to install in the **System** context since the applications are installed and the PowerShell scripts ran during OOBE when no user is signed in.

For applications to install and PowerShell scripts to run successfully, they must be assigned to the device group created for Windows Autopilot device preparation in [Step 3: Create an assigned device group](entra-join-device-group).

For applications to install and PowerShell scripts to run successfully during a Windows Autopilot device preparation deployment, complete two steps:

1. They must be assigned to the device group created for Windows Autopilot device preparation in [Step 3: Create an assigned device group](entra-join-device-group). This step is covered in this article.
2. They must be specified as part of the Windows Autopilot device preparation policy. This step is covered in the next step [Step 5: Create Windows Autopilot device preparation policy](entra-join-autopilot-policy).

Note

The following steps assume that the applications or PowerShell scripts that will be deployed during Windows Autopilot device preparation deployment are already added to Intune. For more information on how to add applications and PowerShell scripts to Intune if they aren't already created, see [Add apps to Microsoft Intune](/en-us/intune/app-management/deployment/) and [Use PowerShell scripts on Windows devices in Intune](/en-us/intune/device-management/tools/management-extension-windows).

### Applications

The following types of applications are supported for use with Windows Autopilot device preparation:

- [Line-of-business (LOB)](/en-us/intune/app-management/deployment/add-lob-windows).
- [Win32](/en-us/intune/app-management/deployment/create-win32-package).
- [Microsoft Store](/en-us/intune/app-management/deployment/add-microsoft-store) - only Microsoft Store apps that support WinGet are supported.
- [Microsoft 365](/en-us/intune/app-management/deployment/add-microsoft-365-windows).
- [Enterprise App Catalog](/en-us/intune/app-management/deployment/add-enterprise-catalog-app).

In addition, Windows Autopilot device preparation supports deploying both Win32 and line-of-business (LOB) applications in the same deployment.

To assign the desired applications to the device group created for Windows Autopilot device preparation:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Apps** in the left hand pane.
3. In the **Apps | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows apps** screen, scroll through the list of applications and then select the desired application that should be installed during the Windows Autopilot device preparation deployment. Alternatively, use the **Search by name or publisher** box to search for the application, and then select it.
5. Once the application is selected, a new screen opens showing the application. Under **Manage**, select **Properties**.
6. In the **Properties** screen, next to **Assignments**, select **Edit**.
7. In the **Edit application** screen:

    1. Under the **Required** section, select **Add group**. The **Select groups** pane opens.
    2. In the **Select groups** pane:

        1. Scroll through the list of groups. Once the Windows Autopilot device preparation device security group is located, select it. Alternatively, use the **Search** box to locate the Windows Autopilot device preparation device security group and then select it.
        2. Once the Windows Autopilot device preparation device security group is selected, select **Select**.
    3. Verify that the Windows Autopilot device preparation device security group is listed under the **Required** section. Additionally, verify that **Group mode** is set to **Included**. When applicable, also verify that **Install Context** is set to **Device context**.
    4. Once everything is verified, select **Review + save**.
    5. In the **Review + save** screen, select **Save**.
8. Repeat the steps for any additional applications that need to be installed during the Windows Autopilot device preparation deployment.

### PowerShell scripts

To assign the desired PowerShell scripts to the device group created for Windows Autopilot device preparation:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, expand **Manage devices**, and then select **Scripts and remediations**.
4. In the **Devices | Scripts and remediations** screen:

    1. Select **Platform scripts**.
    2. Scroll through the list of PowerShell scripts and then select the desired PowerShell script that should run during the Windows Autopilot device preparation deployment. Alternatively, use the **Search** box to search for the PowerShell script, and then select it.
5. Once the PowerShell script is selected, a new screen opens showing the PowerShell script. Under **Manage**, select **Properties**.
6. In the **Properties** screen, next to **Assignments**, select **Edit**.
7. In the **Edit PowerShell script** screen:

    1. Under the **Included groups** section, select **Add groups**. The **Select groups to include** pane opens.
    2. In the **Select groups to include** pane:

        1. Scroll through the list of groups. Once the Windows Autopilot device preparation device security group is located, select it. Alternatively, use the **Search** box to locate the Windows Autopilot device preparation device security group and then select it.
        2. Once the Windows Autopilot device preparation device security group is selected, select **Select**.
    3. Verify that the Windows Autopilot device preparation device security group is listed under the **Included groups** section. Make sure that the Windows Autopilot device preparation device security group wasn't accidentally added under the **Excluded groups** section.
    4. Once everything is verified, select **Review + save**.
    5. In the **Review + save** screen, select **Save**.

## Next step: Create Windows Autopilot device preparation policy