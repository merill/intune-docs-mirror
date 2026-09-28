---
layout: Conceptual
title: Check for running executable files - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/check-for-running-executable-files
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Configure an app deployment to check if certain executable files are running on the client.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3fe5c806-62f0-4c82-c847-0cfa1a034644
document_version_independent_id: 116e2823-3f5b-d9b8-08ab-3777639a9366
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/check-for-running-executable-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/check-for-running-executable-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/check-for-running-executable-files.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: edf070ee-7634-6165-7a64-023ddc372a05
---

# Check for running executable files - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configure an application deployment to check if certain executable files are running on the client. Use this option to check for processes that might disrupt the installation of the application. If one of these executable files is running, the client blocks the installation of the deployment type. The user must close the running executable file before the client can install the deployment type. For deployments with a purpose of required, the client can automatically close the running executable file.

1. Open the **Properties** for the deployment type.
2. Switch to the **Install Behavior** tab, and select **Add**.
3. In the **Add Executable File** window, enter the name of the target executable file. Optionally, enter a friendly name for the application to help you identify it in the list.
4. Select **OK** to save and close the deployment type properties window.
5. When you deploy the application, select the option to **Automatically close any running executables you specified on the install behavior tab of the deployment type properties dialog box**. This option is on the **Deployment Settings** tab of the deployment properties.

Note

If you configure an application to check for running executable files, and include it in the [Install Application](../../osd/understand/task-sequence-steps#BKMK_InstallApplication) task sequence step, the task sequence will fail to install it. If you don't configure this task sequence step to continue on error, then the entire task sequence fails.

## Client behaviors and user notifications

After clients receive the deployment, the following behavior applies:

- If you deployed the application as **Available**, and a user tries to install it, the client prompts the user to close the specified running executable files before proceeding with the installation.
- If you deployed the application as **Required**, and specified to **Automatically close any running executables you specified on the install behavior tab of the deployment type properties dialog box**, then the client displays a notification. It informs the user that the specified executable files are automatically closed when the application installation deadline is reached. If the user tries to install the application before the deadline, the deployment will fail. It notifies the user that the installation couldn't complete because the specified executables are running.

    - Schedule these dialogs in the **Computer Agent** group of client settings. For more information, see [Computer agent](../../core/clients/deploy/about-client-settings#computer-agent).
    - If you don't want the user to see these messages, select the option to **Hide in Software Center and all notifications** on the **User Experience** tab of the deployment's properties. For more information, see [User Experience settings](deploy-applications#bkmk_deploy-ux).
- If you deployed the application as **Required**, and didn't specify to **Automatically close any running executables you specified on the install behavior tab of the deployment type properties dialog box**, then the installation of the app fails if one or more of the specified applications are running.