---
layout: Conceptual
title: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 3 of 10 - Create JSON file for Windows Autopilot profiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/existing-devices/create-json-file
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
description: Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 3 of 10 - Create JSON file for Windows Autopilot profiles.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 3e53867b-75ea-4ee7-f975-cdf30e2cdc42
document_version_independent_id: 3e53867b-75ea-4ee7-f975-cdf30e2cdc42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/existing-devices/create-json-file.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/existing-devices/create-json-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/existing-devices/create-json-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 20635494-7407-7137-3821-838dcdea620f
---

# Windows Autopilot deployment for existing devices in Intune and Configuration Manager - Step 3 of 10 - Create JSON file for Windows Autopilot profiles | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra join steps:

- Step 1: [Set up a Windows Autopilot profile](setup-autopilot-profile)
- Step 2: [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules)

- **Step 3: Create JSON file for Windows Autopilot profiles**

- Step 4: [Create and distribute package for JSON file in Configuration Manager](create-json-package)
- Step 5: [Create Windows Autopilot task sequence in Configuration Manager](create-autopilot-task-sequence)
- Step 6: [Create collection in Configuration Manager](create-collection)
- Step 7: [Deploy a Windows Autopilot task sequence to collection in Configuration Manager](deploy-autopilot-task-sequence)
- Step 8: [Speed up the deployment process (optional)](speed-up-deployment)
- Step 9: [Run Windows Autopilot task sequence on device](run-autopilot-task-sequence)
- Step 10: [Register device for Windows Autopilot](register-device)

For an overview of the Windows Autopilot deployment for existing devices workflow, see [Windows Autopilot deployment for existing devices in Intune and Configuration Manager](existing-devices-workflow#workflow).

## Create JSON file for Windows Autopilot profiles

Note

The PowerShell code snippets in this section were updated in July of 2023 to use the Microsoft Graph PowerShell modules instead of the deprecated AzureAD Graph PowerShell modules. The Microsoft Graph PowerShell modules might require approval of additional permissions in Microsoft Entra ID when they're first used. For more information, see [AzureAD](/en-us/powershell/module/azuread/) and [Important: Azure AD Graph Retirement and PowerShell Module Deprecation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

Once the proper modules are installed to allow exporting of Windows Autopilot profiles from Intune, the next step is to export the Windows Autopilot profiles as JSON files. The JSON files are used to create a package in Configuration Manager.

To export the Windows Autopilot profiles as JSON files, follow these steps:

1. Sign in to the Configuration Manager site server or other device where the required modules were installed in the [Install required modules to obtain Windows Autopilot profiles from Intune](install-modules) step.
2. On the device, open a PowerShell window as an administrator by right-clicking on the **Start** menu and selecting **Windows PowerShell (Admin)**/**Windows Terminal (Admin)** and then selecting **Yes** at the **User Account Control** (UAC) prompt.
3. Copy the following commands by selecting **Copy** at the top right corner of the below **PowerShell** code block:

    ```powershell
    Connect-MgGraph -Scopes "Device.ReadWrite.All", "DeviceManagementManagedDevices.ReadWrite.All", "DeviceManagementServiceConfig.ReadWrite.All", "Domain.ReadWrite.All", "Group.ReadWrite.All", "GroupMember.ReadWrite.All", "User.Read"
    $AutopilotProfile = Get-AutopilotProfile
    $targetDirectory = "C:\Autopilot"
    $AutopilotProfile | ForEach-Object {
        New-Item -ItemType Directory -Path "$targetDirectory\$($_.displayName)"
        $_ | ConvertTo-AutopilotConfigurationJSON | Set-Content -Encoding Ascii "$targetDirectory\$($_.displayName)\AutopilotConfigurationFile.json"
    }
    ```
4. Paste the commands into the elevated PowerShell window and then select **Enter** on the keyboard to run the commands. If the elevated PowerShell command window isn't already signed in to Intune, a **Sign in to your account** window appears. Sign in with a Microsoft Entra account that has access to Intune and the Windows Autopilot profiles.
5. Once signed in to Intune, **Enter** might need to be selected a second time to run the last command in the code block.
6. Once all the commands run successfully, the Windows Autopilot profiles appears in a subfolder under the folder specified by the `$targetDirectory` variable. By default, the `$targetDirectory` variable is `C:\AutoPilot`, but it can be changed to another location if desired. The subfolder has the name of the Windows Autopilot profile from Intune. If there are multiple Windows Autopilot profiles, each profile has its own subfolder. In each folder, there's a JSON file named **`AutopilotConfigurationFile.json`**.

Note

The above script exports all Windows Autopilot profiles from Intune. In addition to supported user-driven Windows Autopilot profiles, it also downloads unsupported pre-provisioning Windows Autopilot profiles and self-deploying Windows Autopilot profiles if they exist in the environment.

## Next step: Create and distribute package for JSON file in Configuration Manager