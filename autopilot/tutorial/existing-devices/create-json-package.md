---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 4 of 10 - Create and distribute package for JSON file in Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/create-json-package
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 4 of 10 - Create and distribute package for JSON file in Configuration Manager.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: e255706f-b477-4976-0800-dbed39ebd8b2
document_version_independent_id: e255706f-b477-4976-0800-dbed39ebd8b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/create-json-package.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/create-json-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/create-json-package.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: e6cdbf8d-ee24-2135-7d7c-dae91b2dda48
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 4 of 10 - Create and distribute package for JSON file in Configuration Manager | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)
- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)

- **Step 4: Create and distribute package for JSON file in Configuration Manager**

- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Create packages for JSON files in Configuration Manager

Once the JSON files are created for the Windows Autopilot profiles, a package needs to be created in Configuration Manager that contains the contents of the JSON files.

Important

The JSON files used by Windows Autopilot deployment for existing devices only support [Windows Autopilot user-driven Microsoft Entra join](../user-driven/azure-ad-join-workflow) and [Windows Autopilot user-driven Microsoft Entra hybrid join](../user-driven/hybrid-azure-ad-join-workflow) Windows Autopilot profiles. When creating the packages for JSON files in Configuration Manager, make sure the JSON files are only for user-driven Microsoft Entra join and user-driven Microsoft Entra hybrid join Windows Autopilot profiles.

To create a package containing the JSON file in Configuration Manager, follow these steps:

1. Copy the folders containing the JSON files created in the [Create JSON file for Windows Autopilot profiles](create-json-file) step to a new empty folder in the organization's UNC network path. The UNC network path should be the path that contains package sources for Configuration Manager packages.
2. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
3. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Application Management**.
4. Select **Packages** and then on the ribbon, select **Create Package**. Alternatively, right-click **Packages** and select **Create Package**.
5. The **Create Package and Program Wizard** window appears:

    1. In the **Specify information about this package** page, enter the following details for the package:

        1. Next to **Name**, enter an identifiable name for the Windows Autopilot scenario that the JSON file is for.
        2. Next to **Description**, enter a description for the Windows Autopilot scenario that the JSON file is for.
        3. Select the checkbox **This package contains source files**, and then select **Browse** next to **Source folder:**.
        4. The **Set Source Folder** window appears. In the **Set Source Folder** window:

            1. Select **Browse** and navigate to the folder containing the individual **`AutopilotConfigurationFile.json`** JSON file from the UNC path in Step 1.
            2. Once in the folder containing the **`AutopilotConfigurationFile.json`** JSON file, select **Select Folder**.
            3. Confirm the path under **Source folder** is correct, and then select **OK**.

                Important

                If multiple Windows Autopilot profiles were copied to a UNC network path, make sure to select the folder that contains the individual **`AutopilotConfigurationFile.json`** JSON file and not the parent folder that contains all of the different Windows Autopilot profiles. Each Windows Autopilot JSON file requires an individual package in Configuration Manager.
    2. Select the **Next &gt;** button.
    3. In the **Choose the program type that you want to create** page, select the **Do not create a program** option, and then select the **Next &gt;** button.
    4. In the **Confirm the settings** page, verify all settings are correct, and then select the **Next &gt;** button.
    5. When the **Create Package and Program Wizard** completes with **The task "Create Package and Program Wizard" completed successfully** message, select the **Close** button.
6. If there are multiple Windows Autopilot JSON files, repeat the above steps for any additional supported Windows profile JSON files that were exported as part of the [Create JSON file for Windows Autopilot profiles](create-json-file) step. Make sure that each package has a unique identifiable name.

## Distribute packages for JSON files in Configuration Manager

Once the package containing the Windows Autopilot profile JSON file is created, the package needs to be distributed to Configuration Manager distribution points. To distribute the package containing the Windows Autopilot profile JSON file in Configuration Manager, follow these steps:

1. On a device where the Configuration Manager console is installed, such as a Configuration Manager site server, open the Configuration Manager console.
2. In the left hand pane of the Configuration Manager console, navigate to **Software Library** &gt; **Overview** &gt; **Application Management**.
3. Expand **Packages** and locate the Windows Autopilot profile JSON packages created in the section Create packages for JSON files in Configuration Manager.
4. Select the Windows Autopilot profile JSON package and in the ribbon select **Distribute Content**. As an alternative, right-click the Windows Autopilot profile JSON package and select **Distribute Content**.
5. The **Distribute Content Wizard** appears:

    1. In the **Review selected content** page, verify the correct package is selected and then select the **Next &gt;** button.
    2. In the **Specify the content destination** page, select **Add**, and then select either **Distribution Point** or **Distribution Point Group**.

        - The **Add Distribution Points** or **Add Distribution Point Groups** window appears. Select the desired distribution points or distribution point groups to distribute the package to and then select **OK**.
    3. Select the **Next &gt;** button.
    4. In the **Confirm the settings** page, verify all settings are correct, and then select the **Next &gt;** button.
    5. When the **Distribute Content Wizard** completes with **The task "Distribute Content Wizard" completed successfully** message, select the **Close** button.
6. With the package still selected under **Packages**, in the lower pane of the Configuration Manager console under **Related Objects**, select **Content Status**.
7. Monitor the distribution of the package until it successfully distributes to all distribution points. For details of the distribution status to each distribution point, under **Completion Statistics** in the lower pane of the Configuration Manager console, select the **View Status** option.
8. If there are multiple Windows Autopilot JSON file packages, repeat the above steps for any additional Windows Autopilot profile JSON file packages created in the section Create packages for JSON files in Configuration Manager.

## Next step: Create Windows Autopilot task sequence in Configuration Manager