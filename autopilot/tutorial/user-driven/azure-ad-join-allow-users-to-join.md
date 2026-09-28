---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra join - Step 2 of 8 - Allow users to join devices to Microsoft Entra ID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/azure-ad-join-allow-users-to-join
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
description: How to - Windows Autopilot user-driven Microsoft Entra join - Step 2 of 8 - Allow users to join devices to Microsoft Entra ID.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: ce9369a5-ff56-d36e-9b6d-4d9d1fd631b2
document_version_independent_id: ce9369a5-ff56-d36e-9b6d-4d9d1fd631b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/azure-ad-join-allow-users-to-join.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/azure-ad-join-allow-users-to-join
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/azure-ad-join-allow-users-to-join.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: b14c4971-d50b-8d17-e233-57f1b2cd239d
---

# Windows Autopilot user-driven Microsoft Entra join - Step 2 of 8 - Allow users to join devices to Microsoft Entra ID | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](azure-ad-join-automatic-enrollment)

- **Step 2: Allow users to join devices to Microsoft Entra ID**

- Step 3: [Register devices as Windows Autopilot devices](azure-ad-join-register-device)
- Step 4: [Create a device group](azure-ad-join-device-group)
- Step 5: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](azure-ad-join-esp)
- Step 6: [Create and assign Windows Autopilot profile](azure-ad-join-autopilot-profile)
- Step 7: [Assign Windows Autopilot device to a user (optional)](azure-ad-join-assign-device-to-user)
- Step 8: [Deploy the device](azure-ad-join-deploy-device)

For an overview of the Windows Autopilot user-driven Microsoft Entra join workflow, see [Windows Autopilot user-driven Microsoft Entra join overview](azure-ad-join-workflow#workflow).

Note

If users are already allowed to join devices to Microsoft Entra ID, skip this step and move on to [Step 3: Register devices as Windows Autopilot devices](azure-ad-join-register-device).

## Allow users to join devices to Microsoft Entra ID

In order for Windows Autopilot to work, users need to be allowed to join devices to Microsoft Entra ID. Allowing users to join devices to Microsoft Entra ID can be configured in the [Azure portal](https://portal.azure.com):

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Select **Microsoft Entra ID**.
3. In the **Overview** screen, under **Manage** in the left hand pane, select **Devices**.
4. In the **Devices | Overview** screen, under **Manage** in the left hand pane, select **Device Settings**.
5. In the **Devices | Device settings** screen that opens, under **Users may join devices to Microsoft Entra**, select either **All** or **Selected**:

    - If **All** is selected, all users can join their devices to Microsoft Entra ID.
    - If **Some** is selected, only users specified under **Selected** can join their devices to Microsoft Entra ID. To add users:

        1. Select the link under **Selected**.
        2. In the **Members allowed to join devices** page that opens:

            1. Select **Add**.
            2. In the **Add members** window that opens:

                1. Select the desired users and/or groups to add.
                2. Once all of the desired users and groups are selected, select **Select** to close the **Add members** window.
            3. Select **OK**.

            Note

            Any selected groups must be a Microsoft Entra group that contains user objects.
6. In the **Devices | Overview** screen, if any changes were made, select **Save**.

Note

This step of allowing users to join devices to Microsoft Entra ID is only needed for the Windows Autopilot scenarios involving Microsoft Entra join. This setting doesn't apply to Windows Autopilot scenarios involving Microsoft Entra hybrid join.

## Next step: Register devices as Windows Autopilot devices