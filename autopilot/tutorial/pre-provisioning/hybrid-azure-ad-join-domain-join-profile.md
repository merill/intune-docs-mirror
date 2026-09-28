---
layout: Conceptual
title: Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 8 of 11 - Create and assign a domain join profile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-domain-join-profile
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
description: How to - Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 8 of 11 - Create and assign a domain join profile.
ms.date: 2025-04-01T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 8e4622bc-4f7d-bb5f-867e-e9bec0bf495f
document_version_independent_id: 8e4622bc-4f7d-bb5f-867e-e9bec0bf495f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-domain-join-profile.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-domain-join-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-domain-join-profile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 46a22f9d-98c1-3967-22c4-4974f670a60c
---

# Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 8 of 11 - Create and assign a domain join profile | Microsoft Learn

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)
- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)

- **Step 8: Configure and assign domain join profile**

- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

For an overview of the Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join workflow, see [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If a domain join profile is already created with the desired settings and assignments, move on to the Next step: Assign Windows Autopilot device to a user (optional) section.

## Create and assign a domain join profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left pane.
3. In the **Devices | Overview** screen, expand **Manage devices**, and then select **Configuration**.
4. In the **Devices | Configuration** screen:

    1. At the top, make sure **Policies** is selected.
    2. Select the **Create** drop down menu and then select **New Policy**.
5. In the **Create a profile** window that opens:

    1. Under **Platform**, select **Windows 10 and later**.
    2. Under **Profile type**, select **Templates**.
    3. When the templates appear, under **Template name**, select **Domain join**. If **Domain join** isn't visible, scroll through the **Template name** list until **Domain join** is visible or search for **Domain join** in the **Search by profile name** box.
    4. Select **Create** to close the **Create a profile** window.
6. The **Domain Join** screen opens. In the **Basics** page:

    1. Next to **Name**, enter a name for the domain join profile.
    2. Next to **Description**, enter a description for the domain join profile.
    3. Select **Next**.
7. In the **Configuration settings** page:

    1. Next to **computer name prefix**, enter a prefix for computer names. This field is required. This prefix is used on all computer names. The rest of the computer name after the prefix is randomly generated up to 15 characters.

        Note

        This field doesn't support the **%SERIAL%** or **%RAND:x%** variables that can be used with the **Apply device name template** in the Microsoft Entra join scenario.
    2. Next to **Domain name**, enter the FQDN of the domain that devices should join. This field is required. Make sure to specify the FQDN of the domain and not the NETBIOS name of the domain. For example, enter in **contoso.com** and not just **CONTOSO**.
    3. Next to **Organizational unit**, enter the full path to the Organizational Unit (OU) in the domain that the computer accounts should be created in. For example, **OU=OU-Name,DC=contoso,DC=com**. This field is optional. If the OU isn't specified, the computer accounts are created in the **Computer** container.

        Note

        The OU specified in this step should be the same OU that permissions were set for and computer account limits increased in the step **Increase the computer account limit in the Organizational Unit (OU)**. Make sure that the step **Increase the computer account limit in the Organizational Unit (OU)** is followed for the OU specified in this field. Skipping the step that sets permissions correctly on the OU results in computers failing to join the domain.

        Important

        If computers are joining the **Computers** container, leave this field blank. Don't specify the **Computers** container in this field via **CN=Computers,DC=contoso,DC=com**. The **Computers** container is a container and not an OU. When no OU is specified in this field and the field is left blank, devices automatically join the **Computers** container. If the **Computers** container is specified, it causes domain joins to fail.
    4. Once the settings in the **Configuration settings** page are complete, select **Next**.
8. In the **Assignments** page:

    1. Under **Included groups**, select **Add all devices**.

        Note

        - Microsoft recommends selecting and assigning to **Add all devices** instead of selecting and assigning to the device group created in the **Create device group** step. Assigning to all devices ensures that the domain join profile works when using:

            - [Windows Autopilot deployment for existing devices](../existing-devices/existing-devices-workflow) scenario.
            - A Windows Autopilot deployment that utilizes Microsoft Entra hybrid join and runs after the Windows Autopilot deployment for existing devices deployment.
        - Make sure to add the correct device groups under **Included groups** and not under **Excluded groups**. Accidentally adding the desired device groups under **Excluded groups** results in those devices being excluded and they don't receive the configuration profile.
    2. Under **Included groups** &gt; **Groups**, ensure that **All devices** is selected, and then select **Next**.
9. In the **Applicability Rules** page, select **Next**. For this tutorial, applicability rules are being skipped. However if applicability rules are needed, do so at this screen. For more information about scope tags, see [Applicability rules](/en-us/intune/device-configuration/create-device-profile#applicability-rules).
10. In the **Review + Create** page, review and verify that all of the settings are set as desired, and then select **Create** to create the domain join profile.

## Next step: Assign Windows Autopilot device to a user (optional)

If a user isn't being assigned to the device, then skip to [Step 10: Technician flow](hybrid-azure-ad-join-technician-flow).