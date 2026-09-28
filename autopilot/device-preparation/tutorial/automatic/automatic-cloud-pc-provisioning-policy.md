---
layout: Conceptual
title: Windows Autopilot device preparation in automatic mode for Windows 365 - Step 5 of 6 - Create a Cloud PC provisioning policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/tutorial/automatic/automatic-cloud-pc-provisioning-policy
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
description: How to - Windows Autopilot device preparation in automatic mode for Windows 365 - Step 5 of 6 - Create a Cloud PC provisioning policy.
ms.date: 2025-06-11T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 52dc3f5f-b355-c615-d9b7-80e82bd82e63
document_version_independent_id: 52dc3f5f-b355-c615-d9b7-80e82bd82e63
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/tutorial/automatic/automatic-cloud-pc-provisioning-policy.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/tutorial/automatic/automatic-cloud-pc-provisioning-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/tutorial/automatic/automatic-cloud-pc-provisioning-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/72cb4d1c-66f7-4281-99d5-e04a64d084fc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d9ebaec0-4879-449e-9781-0afdce99fe0a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: e631c6f5-9bfc-7abe-27d4-2f2a22105615
---

# Windows Autopilot device preparation in automatic mode for Windows 365 - Step 5 of 6 - Create a Cloud PC provisioning policy | Microsoft Learn

Windows Autopilot device preparation in automatic mode for Windows 365 steps:

- Step 1: [Set up Windows automatic Intune enrollment](automatic-automatic-enrollment)
- Step 2: [Create an assigned device group](automatic-device-group)
- Step 3: [Assign applications and PowerShell scripts to device group](automatic-assign-apps-scripts)
- Step 4: [Create Windows Autopilot device preparation policy](automatic-autopilot-policy)

- **Step 5: Create a Cloud PC provisioning policy**

- Step 6: [Monitor the deployment](automatic-monitor)

For an overview of the Windows Autopilot device preparation in automatic mode for Windows 365 workflow, see [Windows Autopilot device preparation in automatic mode for Windows 365 overview](automatic-workflow#workflow).

## Create a Cloud PC provisioning policy for use with Windows Autopilot device preparation in automatic mode for Windows 365

To create a Cloud PC provisioning policy for use with Windows Autopilot device preparation in automatic mode for Windows 365, follow these steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **Device onboarding**, select **Windows 365**.
4. At the top of the **Devices | Windows 365** screen, select **Provisioning policies**, and then select **Create policy**.
5. In the **Create a provisioning policy** screen:

    1. In the **General** page:

        1. In the **Name** text box, enter a name for the Windows 365 Cloud PC policy.
        2. In the **Description** text box, if desired, enter a description for the Windows 365 Cloud PC policy.
        3. Next to **Experience**, select **Access a full Cloud PC desktop**.
        4. Next to **License type**, select **Frontline**.
        5. Next to **Frontline type**, select **Shared**.
        6. Under the **Join type details** section:

            1. Next to **Join type**, make sure **Microsoft Entra Join** is selected.
            2. Next to **Network**, make sure **Microsoft hosted network** is selected.
            3. Next to **Geography** and **Region**, make sure the appropriate geography and region settings are set as desired using the drop-down menus.
            4. If desired, select the option **Use Microsoft Entra single sign-on** to enable it. This option allows the use of a single prompt to authenticate users for Windows 365 and their Cloud PC.
        7. Once all settings are properly configured in the **General** page, select **Next**.
    2. In the **Image** page, make sure a [supported version of Windows](../../requirements#windows-365-cloud-pcs) is selected.

        - To change to a different version of Windows, select the **Change** or **Change selected image** link, select a [supported version of Windows](../../requirements#windows-365-cloud-pcs) from the **Select an image** pane, and then select **Select**.

            Tip

            The Windows images in the image gallery are updated with the latest updates already installed.
        - To use a custom image, use the drop-down menu to select **Custom image**, select a custom image with a [supported version of Windows](../../requirements#windows-365-cloud-pcs) from the **Select an image** pane, and then select **Select**. For more information on custom images, see [Device images overview](/en-us/windows-365/enterprise/device-images).

        Once the desired Windows image is selected, select **Next**.
    3. In the **Configuration** page:

        1. Next to **Language & Region** under **Windows Settings**, select the desired language and region setting using the drop-down menu.
        2. If unique names for Cloud PCs are desired, select **Apply device name template** under **Cloud PC naming**, and then follow the instructions to create a name template.
        3. Under **Windows Autopilot**:

            1. Next to **Autopilot Device preparation policy**, use the drop-down menu to select the automatic Windows Autopilot device preparation policy created in [Step 4: Create Windows Autopilot device preparation policy](automatic-autopilot-policy).
            2. Next to **Minutes allowed before device preparation fails**, enter a value between 10 - 360 minutes that allows adequate time to install the apps and scripts defined in the Windows Autopilot device preparation policy. For example, enter **60** for 60 minutes. The recommended minimum value should be no lower than 30. If the apps and scripts aren't finished installing by the time specified, the device preparation fails.
            3. To prevent users from connecting to the Cloud PC if the deployment fails or times out, select the option **Prevent users from connection to Cloud PC upon installation failure or timeout**. When this option is checked, deployments that fail are marked as **Failed**. For more information, see the next step [Step 6: Monitor the deployment - View status of the deployment](automatic-monitor#view-status-of-the-deployment).

            To allow users to connect to the Cloud PC even when the deployment fails or times out, leave the option **Prevent users from connection to Cloud PC upon installation failure or timeout** unchecked. When this option is unchecked, deployments that fail are marked as **Provisioned with warnings**. For more information, see the next step [Step 6: Monitor the deployment - View status of the deployment](automatic-monitor#view-status-of-the-deployment).
        4. Once all settings are properly configured in the **Configuration** page, select **Next**.
    4. In the **Scope tags** page, select **Next**.

        Note

        **Scope tags** are optional. For this tutorial, scope tags are being skipped and left at the default scope tag. However if a custom scope tag needs to be specified, do so at this page. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags).
    5. In the **Assignments** page:

        1. Select **Add groups**. The **Select groups to include** pane opens. In the **Select groups to include** pane:

            1. In the **Search** text box, enter the name of the user group the policy will be assigned to.
            2. Once the device group is found, select it under **Name**.
            3. Select the **Select** button.
        2. Next to the selected device group, select the **Select one** link under **Cloud PC size**. The **Select Cloud PC size** pane opens. In the **Select Cloud PC size** pane:

            1. In the **Available Cloud PCs** drop down menu under the **Cloud PC size** section, select the desired Cloud PC configuration. For more information, see [Cloud PC size recommendations](/en-us/windows-365/enterprise/cloud-pc-size-recommendations).
            2. Under the **Assignment** section:

                1. In the **Name** text box, enter a name for the assignment.
                2. In the **Remaining Cloud PCs** text box, enter the desired number between 0 - 900 of Cloud PCs that should be provisioned. The number of available Cloud PC licenses is displayed next **Remaining Cloud PCs** and it decrements based on the number entered in the **Remaining Cloud PCs** text box.
            3. Once everything is configured as desired in the **Select Cloud PC size** pane, select **Select**.
        3. Once all settings are properly configured in the **Assignments** page, select **Next**.
    6. In the **Review + create** page, review all settings to make sure they're all correct. Once everything is verified, select **Create** to finish creating the Cloud PC provisioning policy.

## Next step: Monitor the deployment