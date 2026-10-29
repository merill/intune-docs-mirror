---
layout: Conceptual
title: Manually Register Devices with Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/add-devices
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
description: Learn how to manually register Windows Autopilot devices. Gather hardware hashes, and import, edit, and delete device records in the Intune admin center.
ms.date: 2026-10-20T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
- essentials-manage
locale: en-us
document_id: a158111a-5c02-d6c1-6bc5-d66d334f18f7
document_version_independent_id: a158111a-5c02-d6c1-6bc5-d66d334f18f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/add-devices.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: add-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/add-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 32da0003-2988-1f67-6d20-903835657dad
---

# Manually Register Devices with Windows Autopilot | Microsoft Learn

Within an organization, Windows Autopilot device registration requires the following actions:

1. Manually collecting the hardware identity of devices, known as *hardware hashes*.
2. Uploading the hardware hash information in a comma separated values (CSV) file.

Capturing the hardware hash for manual registration requires booting the device into Windows. For this reason, this process is primarily for testing and evaluation scenarios.

You can manually register up to 500 devices by using a CSV file uploaded through the portal. Before you proceed with more devices, check that the previous CSV file batch is successfully registered. To transfer device hashes to another tenant, see [Support tip: How to transfer Windows Autopilot devices between tenants](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-how-to-transfer-windows-autopilot-devices-between/ba-p/3920555) for additional guidance.

Device owners can only register their devices by using a hardware hash. OEMs or CSP partners provide other methods, such as PKID and tuple.

This article provides step-by-step guidance for manual registration. For more information about registration, see:

- [Windows Autopilot registration overview](registration-overview)
- [Manual registration overview](manual-registration)
- [Windows Autopilot for HoloLens 2](/en-us/hololens/hololens2-autopilot#2-register-devices-in-windows-autopilot)

## Requirements

- [Intune subscription](/en-us/intune/fundamentals/licensing)
- [Windows automatic enrollment enabled](/en-us/intune/intune-service/enrollment/windows-enroll#enable-windows-automatic-enrollment)
- [Microsoft Entra ID P1 or P2 subscription](/en-us/azure/active-directory/active-directory-get-started-premium)

## Required permissions

Device enrollment requires *Intune Administrator* or *Policy and Profile Manager* permissions. You can also create a custom Windows Autopilot device manager role by using [role-based access control (RBAC)](/en-us/intune/fundamentals/role-based-access-control/overview). Windows Autopilot device management only requires that you enable all permissions under **Enrollment programs**, except for the four token management options.

Note

In both Intune Administrator and role-based access control methods, the administrative user also needs consent to use the Microsoft Intune PowerShell and Microsoft Graph PowerShell enterprise applications.

## Collect the hardware hash

Use the following methods to collect a hardware hash from existing devices:

- Use Microsoft Configuration Manager.
- Use Windows PowerShell.
- During the out-of-box experience (OOBE), use the Diagnostics Page (Windows 11 only).
- Directly on the device, use the [Access work or school](ms-settings:workplace) pane in the Settings app.

Note

If OOBE is restarted too many times, it can enter a recovery mode and fail to run the Windows Autopilot configuration. This scenario can be identified if OOBE displays multiple configuration options on the same page, including language, region, and keyboard layout. The normal OOBE process displays each of these configuration options on a separate page. The following registry key value tracks the count of OOBE retries:

`HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\UserOOBE`

To ensure that OOBE didn't restart too many times, change this registry key value to `1`.

### Configuration Manager

Microsoft Configuration Manager automatically collects the hardware hashes for existing Windows devices. For more information, see [Gather information from Configuration Manager for Windows Autopilot](/en-us/configmgr/comanage/how-to-prepare-win10#windows-autopilot). You can extract the hash information from Configuration Manager into a CSV file.

### PowerShell

You can access the hardware hash for an existing device through Windows Management Instrumentation (WMI). Use the PowerShell script [Get-WindowsAutopilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) to get a device's hardware hash and serial number. The serial number helps you quickly identify which device the hardware hash belongs to.

To use the `Get-WindowsAutopilotInfo.ps1` script, download it and then run it on a device by using either of the following methods:

- Save the hardware hash locally on a device as a CSV file. The `Get-WindowsAutopilotInfo.ps1` script saves the hardware hash locally on the device as a CSV file. Use this method on devices that already went through Windows Setup and OOBE.
- Directly upload the hardware hash to a mobile device management (MDM) service such as Intune. The `Get-WindowsAutopilotInfo.ps1` script directly uploads the hardware hash to the MDM service. This method is normally used on devices that are undergoing Windows Setup and OOBE.

Note

The `Get-WindowsAutopilotInfo` script used in this section was updated in July 2023 to use the Microsoft Graph PowerShell modules instead of the deprecated AzureAD Graph PowerShell modules. Ensure you use the latest version of the script. The Microsoft Graph PowerShell modules might require approval of additional permissions in Microsoft Entra ID when you first use the modules. For more information, see [AzureAD](/en-us/powershell/module/azuread/) and [Important: Azure AD Graph Retirement and PowerShell Module Deprecation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

#### Save the hardware hash locally on a device as a CSV file

Save the hardware hash locally on a device as a CSV file for devices that already went through Windows Setup and OOBE. To capture and save the hardware hash locally on a device:

1. Sign in to the device.
2. On the device, open an elevated Windows PowerShell prompt.
3. Run the following commands from the elevated Windows PowerShell prompt:

    ```powershell
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    New-Item -Type Directory -Path "C:\HWID"
    Set-Location -Path "C:\HWID"
    $env:Path += ";C:\Program Files\WindowsPowerShell\Scripts"
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
    Install-Script -Name Get-WindowsAutopilotInfo
    Get-WindowsAutopilotInfo -OutputFile AutopilotHWID.csv
    ```

    Note

    On first run, the `Get-WindowsAutopilotInfo.ps1` script prompts to approve the required app registration permissions.

The commands save the hardware hash locally on the device in the directory `C:\HWID` with the filename `AutopilotHWID.csv`. You can then use the CSV file to import the device into an MDM service such as Intune.

Instead of running the PowerShell commands directly on devices, you can run them remotely on devices as long as the remote device meets the following requirements:

- WMI permissions are in place.
- WMI is accessible through Windows Firewall on the remote device.

#### Directly upload the hardware hash to an MDM service

Directly uploading the hardware hash to an MDM service, such as Microsoft Intune, can be done on any device. It's especially useful for a device currently undergoing Windows Setup and OOBE. To directly upload the hardware hash for a device:

1. On a device that is:

    - Currently undergoing Windows Setup and OOBE:

        1. At the sign-in prompt after OOBE starts, open a command prompt window by using Shift+F10.
        2. In the Command Prompt window that opens, start PowerShell by running the following command:

            ```cmd
            powershell.exe
            ```
    - Already undergone Windows Setup and OOBE:

        1. Sign in to the device.
        2. Open an elevated Windows PowerShell prompt.
2. At the `PS` PowerShell command prompt, run the following PowerShell commands:

    ```powershell
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
     Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
     Install-Script -Name Get-WindowsAutopilotInfo -Force
     Get-WindowsAutopilotInfo -Online
    ```

    If prompted, agree to install **NuGet** from the **PSGallery**.
3. When the last command of `Get-WindowsAutopilotInfo -Online` runs, a Microsoft Entra ID sign-on prompt is displayed. Sign in with an account that is at least an Intune Administrator.

    Note

    On first run, the `Get-WindowsAutopilotInfo.ps1` script prompts to approve the required app registration permissions.
4. After the sign-in is successful, the device hash uploads automatically.
5. Verify that the hardware hash uploaded successfully and the device is showing as a registered Windows Autopilot device. See Verify the hardware hash uploaded.
6. For devices undergoing Windows Setup and OOBE, restart the device. The device should pick up the Windows Autopilot profile and OOBE should run through the Windows Autopilot provisioning process.

    Note

    If the device isn't picking up the Windows Autopilot profile after restarting the device, a reset might be necessary. For more information, see [Reset your PC](https://support.microsoft.com/windows/0ef73740-b927-549b-b7c9-e6f2b48d275e#bkmk_reset_steps).

#### Verify the hardware hash uploaded

To confirm the hardware hash for the device was uploaded into Intune and that the device shows as a Windows Autopilot device:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen, in the toolbar, select **Sync**.
7. Wait for the sync to finish. The sync might take several minutes.
8. After the sync completes and the device appears in the device list in the **Windows Autopilot devices** screen in Intune, the device is ready for a Windows Autopilot deployment as long as a Windows Autopilot profile is assigned to the device.

Note

Microsoft recommends registering devices through Microsoft Intune by using a 4K hardware hash only for testing or other limited scenarios for the following reasons:

- Availability of free and inexpensive accounts in Intune that lack robust vetting.
- 4K hardware hashes contain sensitive information that only device owners should maintain.

In most cases, instead use the Microsoft Partner Center for Windows Autopilot device registration.

For more information about running the `Get-WindowsAutopilotInfo.ps1` script, see the script's help by running the following command at PowerShell command prompt:

```powershell
Get-Help Get-WindowsAutopilotInfo
```

### Diagnostics page hash export

To export a hardware hash by using the [Windows Autopilot Diagnostics Page](whats-new#windows-autopilot-diagnostics-page), the device must be running Windows 11.

Windows Autopilot Diagnostics are available in OOBE.

During OOBE, select CTRL + SHIFT + D to open the Diagnostics Page. From this page, you can export logs to an external drive. The logs include a CSV file with the hardware hash.

### Desktop hash export

Sign in to the device where you want to export the hardware hash. After you sign in to the device, open the **Accounts** &gt; **Access work or school** pane in the **Settings** app by selecting the following link:

Or

1. Right-click on the **Start** menu and select **Run**.
2. In the **Run** window, next to **Open:**, enter:

    ```console
    ms-settings:workplace
    ```

    and then select **OK**.

Or

1. Right-click on the **Start** menu and select **Settings**.
2. In **Settings**, in the left pane, select **Accounts**.
3. In the **Accounts** page, select **Access work or school**.

After you open the **Access work or school** pane in the **Settings** app, export the log files:

- Windows 11: In the **Export your management log files** section, select **Export**.
- Windows 10: Select the **Export your management log files** link.

The logs include a CSV file with the hardware hash. The process exports log files to the `C:\Users\Public\Documents\MDMDiagnostics` directory.

For more information, see [Collect MDM logs](/en-us/windows/client-management/mdm-collect-logs).

## Ensure that the CSV file meets requirements

The hardware hashes CSV file should include the following device information:

| Item | Required | Optional |
| --- | --- | --- |
| **Serial number** | ✅ | ❌ |
| **Windows product ID** | Partners uploadinginto Intune. | Admins uploadingdirectly into Intune. |
| **Hardware hash** | ✅ | ❌ |
| **Group tag** | ❌ | ✅ |
| **Assigned user** | ❌ | ✅ |

Use the following methods to collect the required serial number and hardware hash for an individual device CSV file:

- The `Get-WindowsAutopilotInfo` script documented in the Save the hardware hash locally on a device as a CSV file section.
- The Desktop hash export documented in the Desktop hash export section.

You can use the information from individual device CSV files to create a CSV file with multiple devices to import multiple devices at once into an MDM service such as Intune.

The multiple devices CSV file can have up to 500 rows of devices. The header and line format must have the following format:

```csv
Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User
<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>
```

Keep these requirements in mind for the CSV file:

- Don't include extra columns.
- Don't include quotation marks.
- Use only ANSI-format text files. Don't use Unicode.
- Headers are case-sensitive.

Important

Use a plain-text editor such as Notepad to edit this CSV file. Don't use Microsoft Excel. Editing and saving the CSV file by using Microsoft Excel doesn't generate a usable file for importing to Intune.

When you upload a CSV file to assign a user, ensure you assign a valid User Principal Name (UPN). If you upload an invalid UPN or incorrect username, the device might be inaccessible until you remove the invalid assignment.

During upload of a CSV file, Microsoft only validates that the domain name in the `Assigned User` column is valid. Microsoft doesn't validate individual UPNs to ensure that an existing or correct user is being assigned.

## Add devices

After you capture the hardware hashes in a CSV file, Windows Autopilot devices can be added by importing the file. To import the file by using Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen, in the toolbar, select **Import**.
7. In the **Add Autopilot devices** screen:

    1. Go to the CSV file that lists the devices you want to add.
    2. Select **Import** to start importing the device information. Importing can take several minutes.
8. After the import finishes, in the **Windows Autopilot devices** screen, select **Sync** in the toolbar.

    A message says that the synchronization is in progress. The process might take a few minutes to complete, depending on how many devices are being synchronized.
9. Select **Refresh** in the toolbar until the new devices appear.

## Edit Windows Autopilot device attributes

After you upload a Windows Autopilot device, you can edit certain attributes of the device:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In the **Windows Autopilot devices** screen, select the device that you want to edit.
7. In the pane on the right of the screen, edit the following items:

    - Device name
    - Group tag
    - Username, if a user is assigned
8. Select **Save**.

Note

Configure device names for all devices, but Hybrid Microsoft Entra deployments ignore them. The device name still comes from the domain join profile for Hybrid Microsoft Entra devices.

## Delete Windows Autopilot devices

You can delete Windows Autopilot devices that aren't enrolled in Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
6. In **Windows Autopilot devices**, select the devices to delete, and then select **Delete** in the toolbar. The deletion process can take a few minutes to complete.

To completely remove a device from a tenant, you need to delete the device records in Intune, Microsoft Entra ID, and Windows Autopilot. You can perform these deletions from Intune, but you need to follow this order. For more information, see [Deregister a device](registration-overview#deregister-a-device).

## Troubleshooting registration failures

1. **StorageError**: This error is a generic error that can occur for various reasons. Most of the time, you can't determine the exact cause of the error until you investigate further. If you encounter this error, try again later. If the issue persists, contact support.
2. **ZtdDeviceAssignedToAnotherTenant**: This error occurs when the uploaded hardware hash matches a device that's already registered to a different tenant. If this error occurs, search for the serial number corresponding to the duplicate in the CSV file. Then, search for the serial number in the **Windows Autopilot devices** pane in Intune. If the device is already registered, don't import it again.
3. **ZtdDeviceAlreadyAssigned**: This error occurs when the uploaded hardware hash matches a device that's already registered to the tenant. If this error occurs, search for the serial number corresponding to the duplicate in the CSV file. Then, search for the serial number in the **Windows Autopilot devices** pane in Intune. If the device is already registered, don't import it again. If the device isn't registered, you can import it again.
4. **ZtdDeviceDuplicated**: This error occurs when there are duplicate hardware hashes in the CSV file. Only one of the duplicates is processed, and the others result in this error. If this error occurs, look for the other duplicates of the same device to see what the actual result was. If you find a duplicate that was successfully processed, you can remove the duplicate row from the CSV file.
5. **InvalidZtdHardwareHash**: This error occurs when one or more fields in the hardware hash are invalid or empty. You need to include both the manufacturer and serial number information. If you don't include them, you can't register the device for Windows Autopilot. To check the serial number and manufacturer information, open a PowerShell prompt and run the following command:

    ```powershell
    Get-CimInstance Win32_BaseBoard | Select-Object Manufacturer, SerialNumber
    ```