---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 2 of 10 - Install required modules to obtain Windows Autopilot profiles from Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/install-modules
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 2 of 10 - Install required modules to obtain Windows Autopilot profiles from Intune.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 830afd44-8c14-ea7e-bddf-fe05402759c5
document_version_independent_id: 830afd44-8c14-ea7e-bddf-fe05402759c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/install-modules.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/install-modules
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/install-modules.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 1726bfc3-603b-a801-269c-2ad8c76e2951
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 2 of 10 - Install required modules to obtain Windows Autopilot profiles from Intune | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)

- **Step 2: Install required modules to obtain Windows Autopilot profiles from Intune**

- Step 3: [Create JSON file for Windows Autopilot profiles](create-json-file)
- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Install required modules to obtain Windows Autopilot profiles from Intune

Note

The PowerShell code snippets in this section were updated in July of 2023 to use the Microsoft Graph PowerShell modules instead of the deprecated AzureAD Graph PowerShell modules. The Microsoft Graph PowerShell modules might require approval of additional permissions in Microsoft Entra ID when they're first used. The code snippets were also updated to force using an updated version of the WindowsAutoPilot module. For more information, see [AzureAD](/en-us/powershell/module/azuread/) and [Important: Azure AD Graph Retirement and PowerShell Module Deprecation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

After making sure there's a valid Windows Autopilot profile, the next step is to download the existing Windows Autopilot profiles from Intune as JSON files. The JSON files contain all of the information regarding the Intune tenant and the Windows Autopilot profile. After the JSON files are downloaded from Intune, Configuration Manager packages that contain the JSON files are created. The Configuration Manager packages are then used to install the JSON file on the device during the Windows Autopilot deployment for existing devices task sequence.

The JSON file is installed on the device to the offline Windows installation during the WinPE portion of the Configuration Manager task sequence. The JSON file makes the Windows Autopilot profile available to the Windows out-of-box experience (OOBE) so that it can run the Windows Autopilot deployment when Windows is started for the first time. The JSON file eliminates the need for Windows OOBE to have to first download the Windows Autopilot profile from Intune.

Note

Windows OOBE still checks to see if there are any Windows Autopilot profiles assigned to the device even if a JSON file is present. If the device is a Windows Autopilot device and there's a Windows Autopilot profile assigned to the device, the Windows Autopilot profile is downloaded from Intune and used instead of the JSON file.

Before the Windows Autopilot profiles are downloaded from Intune as JSON files, certain modules need to be installed on the device where the Windows Autopilot profile will be downloaded. These modules are required to obtain the Windows Autopilot profile from Intune. For this tutorial and to simplify the process, installation of these modules is performed on the Configuration Manager site server. However, any device with access to Intune can be used.

To install the necessary modules to download the Windows Autopilot profiles as a JSON file, follow these steps:

1. Sign in to the Configuration Manager site server or other device that can access Intune.
2. On the device, open a PowerShell window as an administrator by right-clicking on the **Start** menu and selecting **Windows PowerShell (Admin)**/**Windows Terminal (Admin)** and then selecting **Yes** at the **User Account Control** (UAC) prompt.
3. Copy the following commands by selecting **Copy** at the top right corner of the below **PowerShell** code block:

    ```powershell
    Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force
    Install-Module -Name WindowsAutopilotIntune -MinimumVersion 5.4.0 -Force
    Install-Module -Name Microsoft.Graph.Groups -Force
    Install-Module -Name Microsoft.Graph.Authentication -Force
    Install-Module Microsoft.Graph.Identity.DirectoryManagement -Force
    
    Import-Module -Name WindowsAutopilotIntune -MinimumVersion 5.4
    Import-Module -Name Microsoft.Graph.Groups
    Import-Module -Name Microsoft.Graph.Authentication
    Import-Module -Name Microsoft.Graph.Identity.DirectoryManagement
    ```
4. Paste the commands into the elevated PowerShell window and then select **Enter** on the keyboard to run the commands. **Enter** might need to be selected a second time to run the last command in the code block. Once all the commands run successfully, the required modules are installed.

### Verify that Windows Autopilot profiles from Intune can be viewed

Once the required modules are installed, the following steps can be taken to verify that Windows Autopilot profiles from Intune can be viewed:

Note

The following steps don't export the Windows Autopilot profiles as a JSON file. It only verifies that the Windows Autopilot profiles can be viewed.

1. Copy the following command by selecting **Copy** at the top right corner of the below **PowerShell** code block:

    ```powershell
    Connect-MgGraph -Scopes "Device.ReadWrite.All", "DeviceManagementManagedDevices.ReadWrite.All", "DeviceManagementServiceConfig.ReadWrite.All", "Domain.ReadWrite.All", "Group.ReadWrite.All", "GroupMember.ReadWrite.All", "User.Read"
    ```
2. Paste the command into the elevated PowerShell window and then select **Enter** on the keyboard to run the command.
3. A **Sign in to your account** window appears. Sign in with a Microsoft Entra account that has access to Intune and the Windows Autopilot profiles.
4. Copy the following command by selecting **Copy** at the top right corner of the below **PowerShell** code block:

    ```powershell
    Get-AutopilotProfile | ConvertTo-AutopilotConfigurationJSON
    ```
5. Paste the command into the elevated PowerShell window and then select **Enter** on the keyboard to run the command.
6. All Windows Autopilot profiles available in Intune are displayed in the PowerShell window in JSON format. Each individual Windows Autopilot profile is encapsulated within braces (`{}`).

## Next step: Create JSON file for Windows Autopilot profiles