---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 6 of 10 - Create collection in Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/create-collection
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 6 of 10 - Create collection in Configuration Manager.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 771407a3-548e-c748-fbf1-fc42ef52cc48
document_version_independent_id: 771407a3-548e-c748-fbf1-fc42ef52cc48
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/create-collection.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/create-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/create-collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 04df95d8-123a-8297-28fb-2403abc6c912
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 6 of 10 - Create collection in Configuration Manager | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)

- **Step 6: Create collection in Configuration Manager**

- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Create collection in Configuration Manager

Once the Windows Autopilot for existing devices task sequence is created, the next step is to create a collection in Configuration Manager to deploy the task sequence to the target devices.

Note

If a collection with the desired devices to target already exists, then this step can be skipped. Proceed to the step [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence).

To create the Windows Autopilot for existing devices task sequence in Configuration Manager, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Assets and Compliance** &gt; **Overview**.
3. Select **Device Collections**.
4. In the ribbon, select **Create**, and then select **Create Device Collection**. As an alternative, right-click on **Device Collections**, and then select **Create Device Collection**.
5. In the **Create Device Collection Wizard** window that appears:

    1. In the **Specify details for this collection** page, configure the following settings:

        1. Next to **Name:**, enter a desired name for the collection. For example, **Windows Autopilot for existing devices**.
        2. Next to **Comment:**, if desired, add an optional comment to further describe the collection
        3. Next to **Limiting collection:**, select the **Browse** button. In the **Select Collection** window that appears, select a desired collection to limit this collection to. To not limit this collection, select the **All Systems** collection. Once the desired collection is selected, select the **OK** button.
        4. Select the **Next &gt;** button.
    2. In the **Define membership rules for this collection** page, via the **Add Rule** drop-down menu, create a rule that includes the desired devices to run the Windows Autopilot for existing devices task sequence. For more information on creating rules for a collection to include the desired devices, see [How to create collections in Configuration Manager](/en-us/intune/configmgr/core/clients/manage/collections/create-collections). Once the appropriate rules are created that include the desired devices, select the **Next &gt;** button.
    3. In the **Confirm the settings** page, verify that everything is configured as desired, and then select the **Next &gt;** button.
    4. When the **Create Device Collection Wizard** completes with **The task "Create Device Collection Wizard" completed successfully** message, select the **Close** button.
6. With **Device Collections** still selected, select F5 on the keyboard to refresh the list of collections in the right pane. Verify that the newly created collection appears. If it doesn't appear, wait a few minutes, and then try to refresh again. Depending on the environment, it might take some time for the newly created collection to appear.
7. Once the newly created collection appears, open it by double-clicking on it. Alternatively, to open the collection, right-click on the collection and then select **Show Members**. The members of the collection appear in the right pane.
8. Verify that the listed devices are the expected devices for the collection that should receive the Windows Autopilot for existing devices task sequence.

## Next step: Deploy a Windows Autopilot task sequence to collection in Configuration Manager