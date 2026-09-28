---
layout: Conceptual
title: Setup downloader tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/setup-downloader
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
description: Use the standalone tool to download current versions of key installation files for setup.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 259a975e-42ef-fd14-c283-39dcf2bdb82c
document_version_independent_id: b0878117-7032-d943-abfb-a36030ad58a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/setup-downloader.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/setup-downloader
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/setup-downloader.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: e75efda0-5ba3-1177-e13e-f4e4c5a5fe4e
---

# Setup downloader tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you run Configuration Manager setup to install or upgrade a site, you can use the setup downloader standalone tool to download updated setup files. Run the tool from the version of Configuration Manager that you want to install. Use updated setup files to make sure your site installation uses current versions of key installation files.

When you use setup downloader, you specify a folder to contain the files. The account you use to run the tool must have **Full Control** permissions to the download folder. When you run setup to install or upgrade a site, you can specify this local copy of files you previously downloaded. This behavior prevents setup from connecting to Microsoft when you start the site install or upgrade. You can use the same local copy of setup files for other site installations or upgrades of the same version.

Note

Microsoft ODBC Driver for SQL Server should be installed before invoking download through either the user interface or a command prompt. For more information, see [Download ODBC Driver for SQL Server](/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server) in the SQL Server documentation.

The setup downloader tool downloads the following types of files:

- Required prerequisite redistributable files
- Language packs
- The latest product updates for setup

You have two options to run setup downloader:

- Run the application with the user interface
- Run the application at a command prompt for additional command-line options

If your organization restricts network communication with the internet using a firewall or proxy device, you need to allow the tool to access internet endpoints. The device where you'll run the tool requires internet access the same as the service connection point. For more information, see [Internet access requirements](../../../plan-design/network/internet-endpoints#updates-and-servicing).

## Run setup downloader with the user interface

1. On a computer that has internet access, browse to the installation media for the version of Configuration Manager that you want to install.
2. In the **SMSSETUP\BIN\X64** subfolder, run **Setupdl.exe**.
3. Specify the path for the folder to store the updated installation files, and then select **Download**. Setup downloader verifies the files that are currently in the download folder. It downloads only files that are missing or that are newer than existing files. It creates subfolders for downloaded languages, and other required components.
4. To review the download results, see **C:\ConfigMgrSetup.log**.

## Run setup downloader from a command prompt

1. Open a command prompt, and change directory to the installation media for the version of Configuration Manager that you want to install.
2. Change directory to the **SMSSETUP\BIN\X64** subfolder, and run **Setupdl.exe** with the necessary options.
3. To review the download results, see **C:\ConfigMgrSetup.log**.

### Command-line options

You can use the following command-line options with **Setupdl.exe**:

- `/VERIFY`: Verify the files in the download folder, which include language files. For the list of outdated files, review **C:\ConfigMgrSetup.log**. When you use this option, it doesn't download any files.
- `/VERIFYLANG`: Only verify the language files in the download folder. For the list of outdated language files, review **C:\ConfigMgrSetup.log**.
- `/LANG`: Download only the language files to the download folder.
- `/NOUI`: Start setup downloader without the user interface. When you use this option, the **download path** is required.
- **Download path**: To automatically start the verification or download process, specify the path to the download folder. When you use the `/NOUI` option, the download path is required. If you don't specify a download path, setup downloader prompts you to specify the path. If the folder doesn't exist, setup downloader creates it.

### Example commands

#### Example 1

Setup downloader verifies the files in the specified download folder, and then downloads files.

`setupdl.exe C:\Download`

#### Example 2

Setup downloader only verifies the files in the specified download folder.

`setupdl.exe /VERIFY C:\Download`

#### Example 3

Setup downloader verifies the files in the specified download folder, and then downloads files. The tool doesn't show any user interface.

`setupdl.exe /NOUI C:\Download`

#### Example 4

Setup downloader verifies the language files in the specified download folder, and then downloads only the language files.

`setupdl.exe /LANG C:\Download`

## Copy setup downloader files to another computer

1. In Windows Explorer, go to either one of the following locations:

    - **&lt;Configuration Manager installation media&gt;\SMSSETUP\BIN\X64**
    - **&lt;Configuration Manager installation path&gt;\BIN\X64**
2. Copy the following files to the same destination folder on the other computer:

    - **setupdl.exe**
    - **.\&lt;language&gt;\setupdlres.dll**

        Note

        This file is in the subfolder for the install language. For instance, English is in the `00000409` subfolder.

    The destination folders on your device should look like the following example:

    - `C:\ConfigManInstall\setupdl.exe`
    - `C:\ConfigManInstall\00000409\setupdlres.dll`
3. Run the setup downloader from the destination computer. Use either the user interface or the command prompt.