---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra hybrid join - Step 5 of 10 - Create a device group | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-device-group
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
description: How to - Windows Autopilot user-driven Microsoft Entra hybrid join - Step 5 of 10 - Create a device group.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: a95d4bbc-e7d9-0fa0-31f9-dbfb48d8e54d
document_version_independent_id: a95d4bbc-e7d9-0fa0-31f9-dbfb48d8e54d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/hybrid-azure-ad-join-device-group.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/hybrid-azure-ad-join-device-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/hybrid-azure-ad-join-device-group.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 6fcc1de0-1a0e-81f6-db93-302c43a7534d
---

# Windows Autopilot user-driven Microsoft Entra hybrid join - Step 5 of 10 - Create a device group | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)

- **Step 5: Create a device group**

- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Deploy the device](hybrid-azure-ad-join-deploy-device)

For an overview of the Windows Autopilot user-driven Microsoft Entra hybrid join workflow, see [Windows Autopilot user-driven Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If device groups from are already created, skip this step and move on to [Step 6: Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp). However, if deploying multiple and/or different Windows Autopilot scenarios to different devices, separate device groups are required for each Windows Autopilot scenario.

## Create a device group

Device groups are a collection of devices organized into a Microsoft Entra group. Device groups are used in Windows Autopilot to target devices for specific configurations such as what policies to apply to a device and what applications to install on the device. They're also used by Windows Autopilot to target Enrollment Status Page (ESP) configurations, Windows Autopilot profile configurations, and domain join profiles to devices.

Device groups can be either dynamic or assigned:

- **Dynamic groups** - Devices are automatically added to the group based on rules
- **Assigned groups** - Devices are manually added to the group and are static

When an admin configures Windows Autopilot in an enterprise environment, dynamic groups are primarily used since a large number of devices are normally involved. Adding the devices in automatically using rules makes management of the group a lot easier. Adding a large amount of device in manually via an assigned group would be impractical. However, if there's only a few devices, for example for testing purposes, an assigned group can be used instead.

To create a dynamic device group for use with Windows Autopilot, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Groups** in the left hand pane.
3. In the **Groups | All groups** screen, make sure **All groups** is selected, and then select **New group**.
4. In the **New Group** screen that opens:

    1. For **Group type**, select **Security**.
    2. For **Group name**, enter a name for the device group.
    3. For **Group description**, enter a description for the device group.
    4. For **Microsoft Entra roles can be assigned to the group**, select **No**.
    5. For **Membership type**, select **Dynamic Device**. Setting the **Membership type** option to **Dynamic Device** changes the option **Members** to **Dynamic device members**.
    6. For **Owners**, select the **No owners selected** link.
    7. In the **Add owners** screen that opens:

        1. Scroll through the list of objects and select owners for the user group. Alternatively, use the **Search** bar to search for and select owners of the group.
        2. Once all of the desired owners are selected, select **Select**.
    8. For **Dynamic device members**, select **Add dynamic query**. The **Dynamic membership rules** screen opens.
    9. In the **Dynamic membership rules** screen:

        1. Make sure that **Configure Rules** is selected at the top.
        2. Select **Add expression**. Rules and expressions can be added that defines what devices are added to the device group.

            Rules can be entered in the rule builder via the drop-down boxes. Alternatively, the rule syntax can be entered directly via the **Edit** option in the **Rule syntax** section.

            The most common type of dynamic device group when using Windows Autopilot is a device group that contains all Windows Autopilot devices. A dynamic device group that contains all Windows Autopilot devices has the following syntax:

            `(device.devicePhysicalIDs -any (_ -startsWith "[ZTDid]"))`

            To enter in this rule:

            1. Select the **Edit** option in the **Rule syntax** section.
            2. Paste in the following rule in the **Edit rule syntax** screen under **Rule syntax**:

                `(device.devicePhysicalIDs -any (_ -startsWith "[ZTDid]"))`
            3. Once the rule is pasted in, select **OK**.
        3. Once the desired rule is entered, select **Save** on the toolbar to close the **Dynamic membership rules** window.

            For more information on creating rules for dynamic groups, see [Dynamic membership rules for groups in Microsoft Entra ID](/en-us/azure/active-directory/enterprise-users/groups-dynamic-membership).
    10. Select **Create** to finish creating the dynamic device group.

Note

The above steps are creating a dynamic group in Microsoft Entra that is used by Intune and Windows Autopilot solutions. Although the groups can be accessed in the Intune portal, they're Microsoft Entra groups.

Tip

For Configuration Manager admins, device groups are similar to device based collections. Dynamic device groups are similar to query based device collections while assigned device groups are similar to direct membership device collections.

## Next step: Configure and assign the Enrollment Status Page (ESP)