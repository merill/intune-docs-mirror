---
layout: Conceptual
title: Prepare a Win32 App to Be Uploaded to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/create-win32-package
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Win32
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how to prepare a Win32 app to be uploaded to Microsoft Intune.
ms.date: 2026-02-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a3a034e6-8b65-d73d-631f-06b723b8438f
document_version_independent_id: a3a034e6-8b65-d73d-631f-06b723b8438f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/create-win32-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/create-win32-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/create-win32-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 170c307a-001d-c13c-edcd-b04e531571a2
---

# Prepare a Win32 App to Be Uploaded to Microsoft Intune - Microsoft Intune | Microsoft Learn

Before you can add a Win32 app to Microsoft Intune, you must prepare the app by using the [Microsoft Win32 Content Prep Tool](https://go.microsoft.com/fwlink/?linkid=2065730).

Tip

For a customized experience based on your environment, you can access the [Intune app protection for Windows guide](https://go.microsoft.com/fwlink/?linkid=2309606) in the Microsoft 365 admin center. 

## Prerequisites

To use Win32 app management, be sure you meet the following criteria:

- Use a [supported Windows version](../../fundamentals/ref-supported-platforms) (Enterprise, Pro, and Education versions).
- Devices must be registered or joined to Microsoft Entra ID and autoenrolled. The Intune management extension supports devices that are:

    - Microsoft Entra registered
    - Microsoft Entra joined
    - hybrid domain joined
    - group policy enrolled

    For Intune management extension prerequisites and version requirements, see [Intune Management Extension for Windows](../../device-management/tools/management-extension-windows#prerequisites).

    Note

    For the scenario of group policy enrollment, the user uses the local user account to Microsoft Entra join their Windows device. The user must sign in the device by using their Microsoft Entra user account and enroll in Intune. Intune management extension is installed automatically when a PowerShell script or Win32 app, Microsoft Store apps, Custom compliance policy settings, or Proactive remediations is assigned to the user or device.
- Windows application size is capped at 30 GB per app.
- Apps must support silent installation: Win32 apps deployed through Intune must be able to install without user interaction. Ensure your application installers support silent or unattended installation modes before packaging them with the Content Prep Tool.

## Convert the Win32 app content

Use the [Microsoft Win32 Content Prep Tool](https://go.microsoft.com/fwlink/?linkid=2065730) to preprocess Windows classic (Win32) apps. The tool converts application installation files into the *.intunewin* format. The tool also detects some of the attributes that Intune requires to determine the application installation state. After you use this tool on the app installer folder, you'll be able to create a Win32 app in the Microsoft Intune admin center.

Important

The [Microsoft Win32 Content Prep Tool](https://go.microsoft.com/fwlink/?linkid=2065730) zips all files and subfolders when it creates the *.intunewin* file. Be sure to keep the Microsoft Win32 Content Prep Tool separate from the installer files and folders, so that you don't include the tool or other unnecessary files and folders in your *.intunewin* file.

You can download the [Microsoft Win32 Content Prep Tool](https://go.microsoft.com/fwlink/?linkid=2065730) from GitHub as a .zip file. The zipped file contains a folder named *Microsoft-Win32-Content-Prep-Tool-master*. The folder contains the prep tool, the license, a readme, and the release notes.

### Process flow to create a .intunewin file
![Flow chart of the process to create a .intunewin file.](media/apps-win32-app-management/prepare-win32-app.png)
### Running the Microsoft Win32 Content Prep Tool

If you run `IntuneWinAppUtil.exe` from the command window without parameters, the tool guides you to enter the required parameters step by step. Or, you can add the parameters to the command based on the following available command-line parameters.

### Available command-line parameters

| **Command-line parameter** | **Description** |
| --- | --- |
| `-h` | Help |
| `-c <setup_folder>` | Folder for all setup files. All files in this folder are compressed into an *.intunewin* file. |
| `-s <setup_file>` | Setup file (such as *setup.exe* or *setup.msi*). |
| `-o <output_folder>` | Output folder for the generated *.intunewin* file. |
| `-q` | Quiet mode. |

### Example commands

| **Example command** | **Description** |
| --- | --- |
| `IntuneWinAppUtil -h` | This command shows usage information for the tool. |
| `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q` | This command generates the *.intunewin* file from the specified source folder and setup file. For the MSI setup file, this tool retrieves required information for Intune. If `-q` is specified, the command runs in quiet mode. If the output file already exists, it's overwritten. Also, if the output folder doesn't exist, it's created automatically. |

When you're generating an *.intunewin* file, put any files you need to reference into a subfolder of the setup folder. Then, use a relative path to reference the specific file you need. For example:

**Setup source folder:***c:\testapp\v1.0***License file:***c:\testapp\v1.0\licenses\license.txt*

Refer to the *license.txt* file by using the relative path *licenses\license.txt*.