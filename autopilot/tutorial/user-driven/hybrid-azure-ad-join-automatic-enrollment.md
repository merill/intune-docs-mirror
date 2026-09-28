---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra hybrid join - Step 1 of 10 - Set up Windows automatic Intune enrollment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-automatic-enrollment
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
description: How to - Windows Autopilot user-driven Microsoft Entra hybrid join - Step 1 of 10 - Set up Windows automatic Intune enrollment.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 4e1b3f0d-f238-3d75-86bb-c31d52944af9
document_version_independent_id: 4e1b3f0d-f238-3d75-86bb-c31d52944af9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/hybrid-azure-ad-join-automatic-enrollment.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/hybrid-azure-ad-join-automatic-enrollment
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/hybrid-azure-ad-join-automatic-enrollment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d68ba977-7144-4515-88d0-749aba141b67
---

# Windows Autopilot user-driven Microsoft Entra hybrid join - Step 1 of 10 - Set up Windows automatic Intune enrollment | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra hybrid join steps:

- **Step 1: Set up Windows automatic Intune enrollment**

- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Deploy the device](hybrid-azure-ad-join-deploy-device)

For an overview of the Windows Autopilot user-driven Microsoft Entra hybrid join workflow, see [Windows Autopilot user-driven Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If automatic Intune enrollment is already set up, skip this step and move on to [Step 2: Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector).

## Set up Windows automatic Intune enrollment

In order for Windows Autopilot to work, devices need to be able to enroll in Intune automatically. Enrolling devices in Intune automatically can be configured in the [Azure portal](https://portal.azure.com):

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

## Next step: Install the Intune Connector for Active Directory