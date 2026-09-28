---
layout: Conceptual
title: Deploy Windows Update Packages in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/deploy-win32-update-package
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
description: Learn how to deploy a Windows update package (.msu file) in Intune.
ms.date: 2026-04-14T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: 
locale: en-us
document_id: 24fbf150-14e9-cf93-ee62-9b5f49fdd6a0
document_version_independent_id: 24fbf150-14e9-cf93-ee62-9b5f49fdd6a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/deploy-win32-update-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/deploy-win32-update-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/deploy-win32-update-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: aba376cb-3783-26a7-920f-478aad40328d
---

# Deploy Windows Update Packages in Intune - Microsoft Intune | Microsoft Learn

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

You can deploy a Windows update package (*.msu* file) to Windows devices managed by Intune by using the [Intune Win32 app management](win32) capabilities.

Note

Deploying updates as Win32 apps isn't the recommended approach as described in this article. Use Windows Update policies instead, including [Update rings](../../device-updates/windows/manage-update-rings), [Feature updates](../../device-updates/windows/manage-feature-updates), and [Quality updates](../../device-updates/windows/configure-expedite-policy). The Win32 app method can provide more granular control when needed but requires more manual effort.

The following steps help you deploy a Windows update package to Intune.

## Step 1: Prepare the update package as Win32 app content

1. Download the Windows update package by searching on [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/).
2. Use the [Microsoft Win32 Content Prep Tool](https://go.microsoft.com/fwlink/?linkid=2065730) to convert the *.msu* file into the *.intunewin* format. This tool guides you to input the required parameters in a step-by-step process if you don't specify the parameters in the command-line. For more information about the Microsoft Win32 Content Prep Tool, see [Convert the Win32 app content](create-win32-package#convert-the-win32-app-content).

## Step 2: Create the Win32 app

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, select the **Windows** platform, and then select **Windows app (Win32)**.
4. Choose **Select**, locate the **Add app** pane, and then select **Select app package file**.
5. In the **App package file** pane, select the *.intunewin* file, and then select **OK**.
6. On the **App information** page, add the details for your app.
7. On the **Program** page, specify the following installation and removal commands for the app:

    **Install command:**

    `wusa.exe <full path of the .msu file> /quiet /norestart -Wait`

    For example, if the *windows10.0-kb5031356-x64\_65d5bbc39ccb461472d9854f1a370fe018b79fcc.msu* file is in the current folder, type the following command in **Install command**:

    `wusa.exe .\windows10.0-kb5031356-x64_65d5bbc39ccb461472d9854f1a370fe018b79fcc.msu /quiet /norestart -Wait`

    **Uninstall command:**

    `dism /online /remove-package /PackageName:<package name> /Quiet /NoRestart`

    For example, if the Package\_for\_RollupFix~31bf3856ad364e35~amd64~~19041.3570.1.0 is the package name for the Windows update package, type the following command in **Uninstall command**. About how to check the package name to be used in Uninstall command, see [Uninstalling Windows updates on managed devices using Intune](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/uninstalling-windows-updates-on-managed-devices-using-intune/ba-p/3778267).

    `dism /online /remove-package /PackageName:Package_for_RollupFix~31bf3856ad364e35~amd64~~19041.3570.1.0 /Quiet /NoRestart`

    The following image provides an example of the **Program** page:

    ![Example of editing commands.](media/deploy-win32-update-package/apps-win32-deploy-update-package-01.png)

    Use the `/quiet` switch to run *Wusa.exe* in quiet mode without user interaction. Use the `/norestart` switch to prevent *Wusa.exe* from restarting the computer. For more information about *Wusa.exe*, see [Description of the Windows Update Standalone Installer in Windows](https://support.microsoft.com/help/934307).

    The `-Wait` option is used to make sure that the app installation returns after *Wusa.exe* exits.
8. On the **Requirements** page, specify the [requirements](add-win32#step-3-requirements) that devices must meet before the app is installed.

    **Minimum operating system**: Select the minimum operating system that is required to apply the update.

    To specify more requirements, such as build number and Update Build Revision (UBR), select **Add** to display the **Add a Requirement rule** pane.

    For example, to install the app on only devices that are running Windows 10, version 1903, build 18362, UBR less than 329, select **Registry** as the **Requirement type**, and then specify the following rules:

    - **Key path**: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`
    - **Value name**: CurrentBuildNumber
    - **Registry key requirement**: String comparison
    - **Operator**: Equals
    - **Value**: 18362
    - **Associated with a 32-bit app on 64-bit clients**: No

    ![Screenshot of build 18362 example.](media/deploy-win32-update-package/apps-win32-deploy-update-package-02.png)

    - **Key path**: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion`
    - **Value name**: UBR
    - **Registry key requirement**: Integer comparison
    - **Operator**: Less than
    - **Value**: 329
    - **Associated with a 32-bit app on 64-bit clients**: No

    ![Screenshot of UBR less than 329 example.](media/deploy-win32-update-package/apps-win32-deploy-update-package-03.png)
9. On the **Detection rules** page, select **Use a custom detection script** as the **Rules format**.

    **Example:**

    ![Screenshot of Detection rules example.](media/deploy-win32-update-package/apps-win32-deploy-update-package-04.png)

    **Sample script file (DetectKB.ps1)**:

    ```powershell
    $sysinfo = systeminfo.exe
    $result = $sysinfo -match KB<KB number>
    
    if ($result)
     {
        Write-Output "Found KB<KB number>"
        exit 0
     }
     else
     {
        exit 1
     }
    ```
10. Specify [assignments](add-win32#step-7-assignments) for the app.
11. Review your settings, and then select **Create** to add the app to Intune.

## Step 3: Deploy the app

[Assign the app](assign-groups) to groups.