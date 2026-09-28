---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 7 of 10 - Deploy a Windows Autopilot task sequence to collection in Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/deploy-autopilot-task-sequence
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 7 of 10 - Deploy a Windows Autopilot task sequence to collection in Configuration Manager.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 8a3716e9-f8a3-24bc-790e-31704af1ff53
document_version_independent_id: 8a3716e9-f8a3-24bc-790e-31704af1ff53
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/deploy-autopilot-task-sequence.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/deploy-autopilot-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/deploy-autopilot-task-sequence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 7d220298-dd7c-5cdd-1bb1-126bae918a76
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 7 of 10 - Deploy a Windows Autopilot task sequence to collection in Configuration Manager | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)

- **Step 7: Deploy a Windows Autopilot task sequence to collection in Configuration Manager**

- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Deploy a Windows Autopilot task sequence to collection in Configuration Manager

Once the Windows Autopilot for existing devices task sequence and the collection with devices to deploy the task sequence to are created, the next step is to deploy the task sequence to the collection. To deploy the task sequence to the collection, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Operating Systems**.
3. Expand **Task Sequences** and then locate the Windows Autopilot for existing devices task sequence created in the [Create Windows Autopilot task sequence for existing devices in Configuration Manager](create-autopilot-task-sequence) step.
4. Once the Windows Autopilot for existing devices task sequence is located, select it and then on the ribbon, select **Deploy**. Alternatively, right-click on the Windows Autopilot for existing devices task sequence and select **Deploy**.
5. In the **Deploy Software Wizard** window that appears:

    1. In the **General**/**Specify general information for this deployment** page, configure the following settings:

        1. Next to **Task Sequence:**, the Windows Autopilot for existing devices task sequence should already be selected.
        2. Next to **Collection:**, select the **Browse** button. In the **Select Collection** window that appears, under **Select a collection:**, select the collection created in the step [Create collection in Configuration Manager](create-collection), and then select the **OK** button.
        3. Select the **Next &gt;** button.
    2. In the **Deployment Settings**/**Specify settings to control this deployment** page, configure the settings as desired:

        1. For **Purpose:**, normally **Available** is selected. Making the deployment available usually means that someone such as an admin or end-user has to manually trigger and start the deployment by selecting the task sequence through methods such:

            - The Configuration Manager Software Center.
            - Booting from a PXE enabled distribution point
            - Booting from task sequence bootable media.

            Warning

            The deployment can instead be set to **Required**. Setting the deployment to **Required** causes the deployment to start automatically without any end-user intervention when the deployment assignment time is reached. However, Microsoft recommends not making a deployment required due to the potential destructive behavior that a required task sequence can have. For example, a required task sequence can unexpectedly wipe devices without any user interaction if:

            - The task sequence is accidentally deployed to the wrong collection.
            - The wrong devices are added to the collection that the task sequence is deployed to.

            If using the option of **Required**, do so with extreme caution making sure the task sequence is deployed to the correct collection that contains expected devices.
        2. Under **Make available to the following:**, select where the task sequence appears and when the task sequence can run:

            - **Only Configuration Manager clients**: The task sequence appears in the Configuration Manager Software Center on existing devices that has Windows already installed and has the Configuration Manager client installed. The task sequence doesn't appear when booting from a PXE enabled distribution point or when booting from task sequence bootable media.
            - **Only media and PXE**: The task sequence appears when booting from a PXE enabled distribution point or when booting from task sequence bootable media. The task sequence doesn't appear in the Configuration Manager Software Center on existing devices that has Windows already installed and has the Configuration Manager client installed.
            - **Configuration Manager clients, media and PXE**: The task sequence appears when booting from a PXE enabled distribution point or when booting from task sequence bootable media. It also appears in the Configuration Manager Software Center on existing client devices that has the Configuration Manager client installed.

            Warning

            When the deployment is set to **Required**, the above options are the scenarios when the deployment can automatically run when the deployment assignment time is reached. For example, if the deployment is set to **Required** and **Only media and PXE**, the task sequence doesn't ever run automatically while in Windows. However, it runs automatically when the device is booted from a PXE enabled distribution point or when booted from task sequence bootable media.
        3. Select the **Next &gt;** button.
    3. In the **Scheduling**/**Specify the schedule for this deployment** page, schedule when the deployment should occur:

        1. Select the checkbox next to **Schedule when this deployment will become available:** and then select a date and time. This date and time is the date and time that the task sequence starts to appear:

            - In the Configuration Manager Software Center.
            - When booting from a PXE enabled distribution point.
            - When booting from task sequence bootable media.
        2. If the deployment is required, next to **Assignment schedule:**, select the **New** button. In the **Assignment Schedule** window that appears, configure the settings as needed. The settings selected here determine when the task sequence runs automatically without end-user intervention. Once complete. Once complete, select the **OK** button.
        3. Select the **Next &gt;** button.
    4. In the **User Experience**/**Specify the user experience for the installation of this software** page, select the options as desired, and then select the **Next &gt;** button.
    5. In the **Alerts**/**Specify Configuration Manager and Operations Manager** page, select the options as desired, and then select the **Next &gt;** button.
    6. In the **Distribution Points**/**Specify how to run the content for this program** page, select the options as desired, and then select the **Next &gt;** button.
    7. In the **Summary**/**Confirm the settings for this new deployment** page, verify that everything is configured as desired, and then select the **Next &gt;** button.
    8. When the **Deploy Software Wizard** completes with **The task "Deploy Software Wizard" completed successfully** message, select the **Close** button.
6. If there are multiple task sequences with different Windows Autopilot profiles, repeat the above steps for each task sequence.

Note

The instructions in this step don't fully go into detail all of the options available when running the **Deploy Software Wizard**. For full details on the options available, see [Deploy a task sequence](/en-us/intune/configmgr/osd/deploy-use/deploy-a-task-sequence).

## Next step: Speed up the deployment process (optional)

If the preference is to use an unmodified out-of-box Windows Autopilot task sequence created by the **Create Task Sequence Wizard** in Configuration Manager, then skip to [Step 9: Run Windows Autopilot task sequence on device](run-autopilot-task-sequence).