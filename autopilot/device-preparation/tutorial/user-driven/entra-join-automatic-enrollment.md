---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 1 of 7 - Set up Windows automatic Intune enrollment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-automatic-enrollment
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
description: How to - Windows Autopilot device preparation user-driven Microsoft Entra join - Step 1 of 7 - Set up Windows automatic Intune enrollment.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 78958ae8-c534-90f1-47aa-523db2446a03
document_version_independent_id: 78958ae8-c534-90f1-47aa-523db2446a03
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-automatic-enrollment.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-automatic-enrollment
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-automatic-enrollment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 66889d39-a525-087e-e333-8a27ff9fce05
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 1 of 7 - Set up Windows automatic Intune enrollment | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- **Step 1: Set up Windows automatic Intune enrollment**

- Step 2: [Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join)
- Step 3: [Create an assigned device group](entra-join-device-group)
- Step 4: [Create a user group](entra-join-user-group)
- Step 5: [Assign applications and PowerShell scripts to device group](entra-join-assign-apps-scripts)
- Step 6: [Create Windows Autopilot device preparation policy](entra-join-autopilot-policy)
- Step 7, option 1: [Add Windows corporate identifier to device](entra-join-corporate-identifier)
- Step 7, option 2: [Associate devices](entra-join-device-association)

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

Note

If automatic Intune enrollment is already set up, skip this step and move on to [Step 2: Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join).

## Set up Windows automatic Intune enrollment

In order for Windows Autopilot device preparation to work, devices need to be able to enroll in Intune automatically. Enrolling devices in Intune automatically can be configured in the [Azure portal](https://portal.azure.com):

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Select **Microsoft Entra ID**.
3. In the **Overview** screen, under **Manage** in the left hand pane, select **Mobility (MDM and WIP)**.
4. In the **Mobility (MDM and WIP)** screen, under **Name** select **Microsoft Intune**.
5. In the **Microsoft Intune** page that opens, under **MDM user scope**, select either **All** or **Some**:

    - If **All** is selected, all users can automatically enroll their devices in Intune.
    - If **Some** is selected, only users in the groups specified in the link under **Groups** can automatically enroll their devices in Intune. To add groups:

        1. Select the link under **Groups**.
        2. In the **Select groups** window that opens, select the desired groups to add. Make sure that the groups selected are Microsoft Entra user groups that contain the desired users.
        3. Once all of the desired groups are selected, select **Select** to close the **Select groups** window.
6. In the **Microsoft Intune** screen, if any changes were made, select **Save**.

## Next step: Allow users to join devices to Microsoft Entra ID