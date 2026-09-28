---
layout: Conceptual
title: Windows Autopilot device preparation user-driven Microsoft Entra join - Step 4 of 7 - Create a user group | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/user-driven/entra-join-user-group
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
description: How to - Windows Autopilot device preparation user-driven Microsoft Entra join - Step 4 of 7 - Create a user group.
ms.date: 2026-08-07T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 7d402c2d-5c24-f68d-c501-19a96abe6f1a
document_version_independent_id: 7d402c2d-5c24-f68d-c501-19a96abe6f1a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/user-driven/entra-join-user-group.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/user-driven/entra-join-user-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/user-driven/entra-join-user-group.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: e7f80cda-ba0a-b41b-f85b-9bed7cfecd1e
---

# Windows Autopilot device preparation user-driven Microsoft Entra join - Step 4 of 7 - Create a user group | Microsoft Learn

Windows Autopilot device preparation user-driven Microsoft Entra join steps:

- Step 1: [Set up Windows automatic Intune enrollment](entra-join-automatic-enrollment)
- Step 2: [Allow users to join devices to Microsoft Entra ID](entra-join-allow-users-to-join)
- Step 3: [Create an assigned device group](entra-join-device-group)

- **Step 4: Create a user group**

- Step 5: [Assign applications and PowerShell scripts to device group](entra-join-assign-apps-scripts)
- Step 6: [Create Windows Autopilot device preparation policy](entra-join-autopilot-policy)
- Step 7, option 1: [Add Windows corporate identifier to device](entra-join-corporate-identifier)
- Step 7, option 2: [Associate devices](entra-join-device-association)

For an overview of the Windows Autopilot device preparation user-driven Microsoft Entra join workflow, see [Windows Autopilot device preparation user-driven Microsoft Entra join overview](entra-join-workflow#workflow).

Note

The user group created in this step is specific to Windows Autopilot device preparation. Microsoft recommends creating a user group specifically for use with Windows Autopilot device preparation instead of reusing existing user groups used in other Windows Autopilot scenarios.

## Create a user group

User groups are a collection of users organized into a Microsoft Entra group. User groups can be either dynamic or assigned:

- **Dynamic groups** - Users are automatically added to the group based on rules.
- **Assigned groups** - Users are manually added to the group and are static.

Windows Autopilot device preparation uses a user group as part of the Windows Autopilot device preparation policy. The users that are members of the user group specified in the Windows Autopilot device preparation policy are the users that receive the Windows Autopilot device preparation deployment. The user group specified in the Windows Autopilot device preparation policy needs to be a security group but can be either an assigned or dynamic group.

To create a user security group for use with Windows Autopilot device preparation, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Groups** in the left hand pane.
3. In the **Groups | All groups** screen, make sure **All groups** is selected, and then select **New group**.
4. In the **New Group** screen that opens:

    1. For **Group type**, select **Security**.
    2. For **Group name**, enter a name for the user group, such as **Windows Autopilot device preparation user group**.
    3. For **Group description**, enter a description for the user group.
    4. For **Microsoft Entra roles can be assigned to the group**, select **No**.
    5. For **Membership type**:

        - Select **Assigned** to create an assigned user group.
        - Select **Dynamic User** to create a dynamic user group.
    6. For **Owners**, select the **No owners selected** link.
    7. In the **Add owners** screen that opens:

        1. Scroll through the list of objects and select owners for the user group. Alternatively, use the **Search** bar to search for and select owners of the group.
        2. Once all of the desired owners are selected, select **Select**.
    8. For assigned user groups:

        1. For **Members**, select the **No members selected** link.
        2. In the **Add members** screen that opens:

            1. Scroll through the list of objects and select members that the Windows Autopilot device preparation profiles should be deployed to. Alternatively, use the **Search** bar to search for and select members for the group. Make sure to only select users or groups that only contain users.
            2. Once all of the desired users or user groups are selected that the Windows Autopilot device preparation profiles should be deployed to, select **Select**.
    9. For dynamic user groups:

        1. For **Dynamic user members**, select the **Add dynamic query** link.
        2. In the **Dynamic membership rules** screen that opens, create a rule that encompasses the users that should be members of the user group. For more information on creating rules, see [Dynamic membership rules for groups in Microsoft Entra ID](/en-us/entra/identity/users/groups-dynamic-membership).

        Note

        The linked article is in regards to creating dynamic membership rules in Microsoft Entra ID. However, dynamic user groups in Intune are also dynamic user groups in Microsoft Entra ID, so the rule syntax is the same.
    10. Select **Create** to finish creating user group.

## Next step: Assign applications and PowerShell scripts to device group