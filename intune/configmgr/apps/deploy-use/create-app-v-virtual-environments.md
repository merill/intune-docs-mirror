---
layout: Conceptual
title: Create App-V virtual environments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-app-v-virtual-environments
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
description: Create virtual environments with Microsoft Application Virtualization so apps can share data with each other.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 958e52c0-de26-9135-4b51-cbf6488c26d3
document_version_independent_id: 13706fb5-26a6-3053-8a3e-414fc0193252
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/create-app-v-virtual-environments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/create-app-v-virtual-environments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/create-app-v-virtual-environments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a50656b2-c79c-31c4-b44d-08d0f7011acf
---

# Create App-V virtual environments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In a Microsoft Application Virtualization (App-V) virtual environment in Configuration Manager, deployed virtual applications can share the same file system and registry on client Windows PCs. Unlike standard virtual applications, these applications can share data with each other. Virtual environments are created or modified on client PCs when the application is installed or when clients next evaluate their installed applications. You can order these applications so that when multiple applications try to modify a file system or registry value, the application with the highest order takes priority.

Important

Do not rely on App-V virtual environments to provide security protection, such as from malware.

Use the following procedure to create an App-V virtual environment in Configuration Manager.

## Create an App-V virtual environment

1. In the Configuration Manager console, choose **Software Library** &gt; **Application Management** &gt; **App-V Virtual Environments**.
2. On the **Home** tab, in the **Create** group, choose **Create Virtual Environment**.
3. In the **Create Virtual Environment** dialog box, enter the following information:

    - **Name**. Enter a unique name for the virtual environment (maximum 128 characters).
    - **Description**. (Optional) Enter a description for the virtual environment.
4. To add a new deployment type to the virtual environment, choose **Add**. You must add at least one deployment type.
5. In the **Add Applications** dialog box, specify a **Group name** (maximum 128 characters). You'll use this name to refer to the group of applications that you add to the virtual environment.
6. Choose **Add**, select the App-V 5 applications and deployment types that you want to add to the group, and then choose **OK**.
7. In the **Add Applications** dialog box, you can select **Increase Order** or **Decrease Order** to set the application that takes priority if multiple applications attempt to modify file system or registry settings in the same virtual environment.
8. To return to the **Create Virtual Environment** dialog box, choose **OK**.
9. When you're done adding groups, choose **OK** to create the virtual environment. The new virtual environment is displayed in the **App-V Virtual Environments** node of the Configuration Manager console. You can monitor the status of your virtual environments by using the App-V Virtual Environment Status report.

    Note

    The virtual environment is added or modified on client PCs when the application is installed or when the client next evaluates installed applications.