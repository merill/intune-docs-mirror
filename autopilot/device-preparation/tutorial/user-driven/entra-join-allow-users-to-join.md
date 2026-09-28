---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 2 of 7 - Allow users to join devices to Microsoft Entra ID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-allow-users-to-join
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
description: How to - Windows Autopilot device preparation user-driven Microsoft Entra join - Step 2 of 7 - Allow users to join devices to Microsoft Entra ID.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 7da43ca3-3bb4-c2f2-6ca2-d52f0bcf4432
document_version_independent_id: 7da43ca3-3bb4-c2f2-6ca2-d52f0bcf4432
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-allow-users-to-join.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-allow-users-to-join
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-allow-users-to-join.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: df305e67-b092-a0c3-c929-163168767d79
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 2 of 7 - Allow users to join devices to Microsoft Entra ID | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](entra-join-automatic-enrollment)

- **Step 2: Allow users to join devices to Microsoft Entra ID**

- Step 3: [Create an assigned device group](entra-join-device-group)
- Step 4: [Create a user group](entra-join-user-group)
- Step 5: [Assign applications and PowerShell scripts to device group](entra-join-assign-apps-scripts)
- Step 6: [Create Windows Autopilot device preparation policy](entra-join-autopilot-policy)
- Step 7, option 1: [Add Windows corporate identifier to device](entra-join-corporate-identifier)
- Step 7, option 2: [Associate devices](entra-join-device-association)

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

Note

If users are already allowed to join devices to Microsoft Entra ID, skip this step and move on to [Step 3: Create an assigned device group](entra-join-device-group).

## Allow users to join devices to Microsoft Entra ID

In order for Windows Autopilot device preparation to work, users need to be allowed to join devices to Microsoft Entra ID. Allowing users to join devices to Microsoft Entra ID can be configured in the [Azure portal](https://portal.azure.com):

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

## Next step: Create an assigned device group