---
layout: Conceptual
title: Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 9 of 11 - Assign Windows Autopilot device to a user | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-assign-device-to-user
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
description: How to - Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join with pre-provisioning - Step 9 of 11 - Assign Windows Autopilot device to a user.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 3f1f1be3-8185-e3d5-e751-84e644b3ce46
document_version_independent_id: 3f1f1be3-8185-e3d5-e751-84e644b3ce46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-assign-device-to-user.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-assign-device-to-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-assign-device-to-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: d349983a-2d75-f8dc-2e4c-77c126894b9d
---

# Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 9 of 11 - Assign Windows Autopilot device to a user | Microsoft Learn

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)

- **Step 9: Assign Windows Autopilot device to a user (optional)**

- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

For an overview of the Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join workflow, see [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

## Assign Windows Autopilot device to a user (optional)

A device that is registered as a Windows Autopilot device can also be assigned to a user. If a Windows Autopilot device is assigned to a user, then any user policies and application installs assigned to that user is applied to the device during the Windows Autopilot process.

Tip

For testing purposes, especially for hybrid Microsoft Entra scenarios, it might be better to first test a Windows Autopilot deployment before assigning the device to a user. Not assigning a user limits the scope of applications, policies, and configurations processed during the Windows Autopilot process.

Tip

For Configuration Manager admins, assigning a user to a device is similar to user device affinity in Configuration Manager.

To assign a Windows Autopilot device to a user, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen that opens, locate the device to assign a user to.
7. Once the desired device is located, select the box to the left of the device, making sure that there's check mark in the box, and then select **Assign user** in the toolbar at the top of page.
8. In the **Select user** window that opens, find and select a user for the device, and then select **Select** to close the window. If necessary, use the **Search** box to find the desired user.

    Note

    The selected user must be an Azure user licensed to use Intune.
9. In the Windows Autopilot device's property window that automatically opens on the right hand side, under **User friendly name**, verify the default value. If the value is empty or a different friendly name is desired, enter the desired friendly name for the user under **User friendly name**, and then select **Save** to close the property window.
10. The user assignment can be verified by selecting the Windows Autopilot device in the **Windows Autopilot devices** screen. Once the Windows Autopilot device is selected, it highlights and the Windows Autopilot device's property window automatically opens on the right hand side. The assigned user is listed under **User** and **User friendly name**.

## Assigning Windows Autopilot device to a user via hardware hash CSV file

A user can be manually assigned to a Windows Autopilot device in the Windows Autopilot device's properties. However, a user can also be assigned to the Windows Autopilot device when the device was initially imported into Windows Autopilot as a Windows Autopilot device. Assigning a user when the device is imported as a Windows Autopilot device can be done by editing the hardware hash CSV file and adding the **Assigned User** column after the **Hardware Hash** column. The user's User Principal Name (UPN) should then be added as a value under the **Assigned User** column.

Important

Use a plain-text editor such as **Notepad** to edit the CSV file. Don't use Microsoft Excel. Editing the CSV file in Excel doesn't generate a proper usable file for importing into Intune.

For more information on editing the CSV file to add an assigned user to the Windows Autopilot device, see [Manually register devices with Windows Autopilot: Ensure that the CSV file meets requirements](../../add-devices#ensure-that-the-csv-file-meets-requirements).

## Next step: Technician flow