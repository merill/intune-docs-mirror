---
layout: Conceptual
title: Windows Autopilot motherboard replacement | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/autopilot-motherboard-replacement
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
description: Understand how Windows Autopilot deployments function when the motherboard is replaced on a device.
ms.date: 2025-08-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 636874f1-de48-eeb3-ebdc-fca3d280fdc2
document_version_independent_id: 636874f1-de48-eeb3-ebdc-fca3d280fdc2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/autopilot-motherboard-replacement.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: autopilot-motherboard-replacement
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/autopilot-motherboard-replacement.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 1bb912cc-ee22-6933-cc4e-fd66dab404f4
---

# Windows Autopilot motherboard replacement | Microsoft Learn

This document offers guidance for Windows Autopilot device repair scenarios that Microsoft partners can use in motherboard replacement situations, and other servicing scenarios.

Repairing Windows Autopilot enrolled devices is complex, as it tries to balance OEM requirements with Windows Autopilot requirements. Specifically, OEM requirements include strict uniqueness across motherboards, MAC addresses, etc. Windows Autopilot requires strict uniqueness at the hardware hash level for each device to enable successful registration. The hardware hash doesn't always accommodate all the OEM hardware component requirements. These requirements are sometimes at odds, which can cause issues with some repair scenarios. The hardware hash is also known as the hardware ID.

If a motherboard is replaced on a Windows Autopilot registered device, then the following process is recommended:

1. Deregister the Windows Autopilot device from the Windows Autopilot program.
2. Replace the motherboard.
3. Capture a new Windows Autopilot device ID (4K HH) from the device.
4. Reregister the device with Windows Autopilot.
5. Reset the device.
6. Return the device.

Each of these steps is described in the following sections.

## Deregister the Windows Autopilot device from the Windows Autopilot program

Before the device arrives at the repair facility, the entity that registered the device must deregister it.

- If the **IT Admin** registered the device, they likely did so via Intune, [Microsoft 365 admin center](https://admin.microsoft.com/), or a legacy portal such as Microsoft Store for Business (MSfB). If so, they should deregister the device from Intune or the [Microsoft 365 admin center](https://admin.microsoft.com/) because devices registered in Intune don't show up in Microsoft Partner Center (MPC).
- If the **OEM or CSP partner** registered the device, they likely did so via the Microsoft Partner Center (MPC). In that case, they should deregister the device from MPC, which also removes it from the customer IT Admin's Intune account.

The below steps describe what an IT Admin would go through to deregister a device from Intune and the steps an OEM or CSP would go through to deregister a device from MPC.

To avoid problems, an OEM or CSP should register Windows Autopilot devices whenever possible. If the customer registers the devices, OEMs or CSPs can't deregister them if, for example, a customer leasing a device goes out of business before deregistering it themselves.

If a customer grants an OEM permission to register devices on their behalf using the automated consent process, an OEM can use the API to deregister devices they didn't register themselves. This deregistration only removes those devices from the Windows Autopilot program. It doesn't unenroll them from Intune or disjoin them from Microsoft Entra ID. Only the customer can unenroll the device from Intune or disjoin the device from Microsoft Entra ID.

## Deregister a device

Whenever a device permanently leaves an organization, the device should always be deregistered from Windows Autopilot. For example, the device leaves the organization for repair or because the device is at the end of its life cycle.

Below we describe the steps an admin would go through to deregister a device from Intune and Windows Autopilot.

### Delete from Intune

Before a device is deregistered from Windows Autopilot, it first has to be deleted from Intune. To delete a Windows Autopilot device from Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. Under **Device name**, find the device that needs to be deleted and then select the device. If necessary, use the **Search** box.
5. In the properties screen for the device, make a note of the serial number listed under **Serial number**.
6. After making a note of the serial number of the device, select **Delete** in the toolbar at the top of the page.
7. A warning dialog box appears to confirm the deletion of the device from Intune. Select **Yes** to confirm deleting the device.

### Deregister from Windows Autopilot using Intune

Once the device is deleted from Intune, it can then be deregistered from Windows Autopilot. This process includes required cleanup steps in Intune and Microsoft Entra ID to prevent orphaned or unrecoverable devices. To deregister a device from Windows Autopilot:

1. Make sure the device is deleted from Intune as described in the Delete from Intune section.
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. In the **Home** screen, select **Devices** in the left hand pane.
4. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
5. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
6. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Devices**.
7. In the **Windows Autopilot devices** screen that opens, under **Serial number**, find the device that needs to be deregistered by its serial number as determined in the Delete from Intune section. If necessary, use the **Search by serial number** box.
8. Select the device by selecting the checkbox next to the device.
9. Select the extended menu icon (`…`) on the far right end of the line containing the device. A menu appears with the option **Unassign user**.

    - If the **Unassign user** option is available and not greyed out, then select it. A warning dialog box appears confirming to unassign the user from the device. Select **OK** to confirm unassigning the device from the user.
    - If the **Unassign user** option isn't available and greyed out, then move on to the next step.
10. With the device still selected, select **Delete** in the toolbar at the top of the page.
11. A warning dialog box appears to confirm the deletion of the device from Windows Autopilot. Select **Yes** to confirm deleting the device.
12. The deregistration process might take some time. The process can be accelerated by selecting the **Sync** button in the toolbar at the top of the page.
13. Every few minutes select **Refresh** in the toolbar at the top of the page until the device is no longer present.

Important

- For Microsoft Entra joined devices, no additional steps are required after deregistering the device from Windows Autopilot using Intune. Avoid manually deleting the device from Microsoft Entra ID, as this can cause unexpected issues.
- For Microsoft Entra hybrid joined devices, delete the computer object from the on‑premises Active Directory Domain Services (AD DS) environment to prevent it from being resynced to Microsoft Entra ID. After this step, no additional actions are required in Intune or Windows Autopilot. Avoid manually deleting the device from Microsoft Entra ID.

For information about what to expect in Microsoft Entra ID after deregistration, see What happens to the Microsoft Entra device object after deregistration?

This process ensures that related records in Windows Autopilot, Intune, and Microsoft Entra ID are handled correctly. Skipping steps or removing records out of order can result in orphaned records or unrecoverable devices. If a device goes into an unrecoverable state, contact the appropriate [Microsoft support alias](autopilot-support) for assistance.

### What happens to the Microsoft Entra device object after deregistration?

Deregistering a device from Windows Autopilot removes the device’s registration from the Windows Autopilot deployment service. However, this action doesn’t always remove the corresponding Microsoft Entra device object.

What happens in Microsoft Entra ID depends on the device’s join and enrollment state:

- **Devices that aren’t currently enrolled in MDM:** Removing the Windows Autopilot registration can also result in the associated Microsoft Entra device object being removed.
- **Devices that are or were enrolled in MDM:** Removing the Windows Autopilot registration doesn’t automatically delete the Microsoft Entra device object. In this case, the device can remain in Microsoft Entra ID even though it’s no longer registered with Windows Autopilot.

Because this behavior varies, avoid manually deleting the device from Microsoft Entra ID unless a specific scenario requires it. The Windows Autopilot deployment process relies on the Microsoft Entra device object, and deleting it can cause enrollment failures.

### Deregister from Windows Autopilot using Microsoft 365 admin center

The device can be deregistered from Windows Autopilot in [Microsoft 365 admin center](https://admin.microsoft.com/) if using the Microsoft 365 admin center instead of Intune. To deregister a Windows Autopilot device from the Microsoft 365 admin center:

1. Sign in to to the [Microsoft 365 admin center](https://admin.microsoft.com/).
2. Navigate to **Devices** &gt; **Autopilot**.
3. Select the device to be deregistered and then select **Delete device**.

### Deregister from Windows Autopilot in Microsoft Partner Center (MPC)

To deregister a Windows Autopilot device from the Microsoft Partner Center (MPC), a Cloud Solution Partner (CSP) would:

1. Sign in to the Microsoft Partner Center (MPC).
2. Navigate to **Customer** &gt; **Devices**.
3. Select the device to be deregistered and then select **Delete device**.

    ![Screenshot of delete device](images/devices.png)

Partners deregistering a device from Windows Autopilot in Microsoft Partner Center (MPC) only deregisters the device from Windows Autopilot. It doesn't perform any of the following actions:

- Unenroll the device from the mobile device management (MDM) solution, such as Intune.
- Disjoin the device from Microsoft Entra ID.

For these reasons, the OEM or CSP should work with the customer IT administrators to have the device fully removed by following the steps in the Deregister a device section.

An OEM or CSP with integrated OEM Direct APIs can also deregister a device with the **AutopilotDeviceRegistration** API. Make sure the **TenantID** and **TenantDomain** fields are left blank.

Note

If an admin registered a device via another portal other than the Microsoft Partner Center (MPC) such as Intune or the [Microsoft 365 admin center](https://admin.microsoft.com/), the device doesn't show up in Microsoft Partner Center (MPC). For a partner to register a device in the Microsoft Partner Center (MPC), the devices first needs to be deregistered using the steps outlined in the Deregister a device section.

Because the repair facility doesn't have the user's sign-in credentials, they have to reimage the device as part of the repair process. The customer should do three things before sending the device to the facility:

1. Copy all important data off the device.
2. Let the repair facility know which version of Windows they should reinstall after the repair.
3. If applicable, let the repair facility know which version of Office they should reinstall after the repair.

## Replace the motherboard

Technicians replace the motherboard or other hardware on the broken device. A replacement Digital Product Key (DPK) is injected.

Repair and key replacement processes vary between facilities. Sometimes repair facilities receive motherboard spare parts from OEMs that have replacement DPKs already injected, but sometimes not. Sometimes repair facilities receive fully functional BIOS tools from OEMs, but sometimes not. The quality of the data in the BIOS after a motherboard replacement varies. To ensure the repaired device are still Windows Autopilot capable following its repair, check to make sure the new post-repair BIOS can successfully gather and populate the following information at a minimum:

- DiskSerialNumber.
- SmbiosSystemSerialNumber.
- SmbiosSystemManufacturer.
- SmbiosSystemProductName.
- SmbiosUuid.
- TPM EKPub.
- MacAddress.
- ProductKeyID.
- OSType.

For simplicity, and because processes vary between repair facilities, additional steps often used in a motherboard replacement are excluded, such as:

- Verify that the device is still functional.
- Disable or suspend BitLocker.
- Repair the Boot Configuration Data (BCD).
- Repair and verify the network driver operation.

## Capture a new Windows Autopilot device ID (4K HH) from the device

Repair technicians must sign in to the repaired device to capture the new device ID. If the repair technician doesn't have access to the customer's sign-in credentials, they have to reimage the device to gain access:

1. The repair technician creates a [WinPE bootable USB drive](/en-us/windows-hardware/manufacture/desktop/oem-deployment-of-windows-10-for-desktop-editions#create-a-bootable-windows-pe-winpe-partition).
2. The repair technician boots the device to WinPE.
3. The repair technician [applies a new Windows image to the device](/en-us/windows-hardware/manufacture/desktop/work-with-windows-images).

    Ideally, the same Windows version that was originally on the device should be reimaged onto the device. Some coordination is required between the repair facility and customer to capture this information at the time the device arrives for repair. Such coordination might include the customer sending the repair facility a customized image (.ppk file) via a USB stick, for example.
4. The repair technician boots the device into the new Windows image.
5. Once on the desktop, the repair technician captures the new device ID (4K HH) off the device using either the OA3 Tool or the PowerShell script.

Those repair facilities with access to the OA3 Tool (which is part of the ADK) can use the tool to capture the 4K Hardware Hash (4K HH).

Instead, the [WindowsAutopilotInfo PowerShell script](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) can be used to capture the 4K HH.

Note

Other methods in addition to Windows PowerShell are also available to capture the hardware hash. For more information, see [Collect the hardware hash](add-devices#collect-the-hardware-hash).

To use the **WindowsAutopilotInfo** PowerShell script, follow these steps:

1. Install the script from the [PowerShell Gallery](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) or from the command line.
2. Navigate to the script directory and run it on the device when the device is either in Full OS or Audit Mode. See the following example.

    ```powershell
    md c:\HWID
    Set-Location c:\HWID
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    Install-Script -Name Get-WindowsAutopilotInfo -Force
    Get-WindowsAutopilotInfo.ps1 -OutputFile AutopilotHWID.csv
    ```

    - If prompted to install the **NuGet** package, select **Yes**.
    - If after installing the script an error occurs reporting that `Get-WindowsAutopilotInfo.ps1` isn't found, verify that `C:\Program Files\WindowsPowerShell\Scripts` is present in the `PATH` variable.
    - If the `Install-Script` cmdlet fails, verify that the default PowerShell repository is registered with the following command:

    ```powershell
    Get-PSRepository
    ```

    If the default PowerShell repository isn't registered, register it with the following command:

    ```powershell
    Register-PSRepository -Default -Verbose
    ```

    Note

    The `Get-WindowsAutopilotInfo` script was updated in July of 2023 to use the Microsoft Graph PowerShell modules instead of the deprecated AzureAD Graph PowerShell modules. Make sure to use the latest version of the script. The Microsoft Graph PowerShell modules might require approval of additional permissions in Microsoft Entra ID when they're first used. For more information, see [AzureAD](/en-us/powershell/module/azuread/) and [Important: Azure AD Graph Retirement and PowerShell Module Deprecation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

The script creates a `.csv` file that contains the device information, including the complete 4K HH. Save this file so that it can be accessed later. The service facility uses this 4K HH to reregister device as described in the following sections. Be sure to use the `-OutputFile` parameter when saving the file, which ensures that file formatting is correct. Don't attempt to pipe the command output to a file manually.

Note

If the repair facility can't run the OA3 tool or PowerShell script to capture the new 4K HH, then the OEM or CSP partners must do it for them. Without some entity capturing the new 4K HH, there's no way to reregister this device as a Windows Autopilot device.

## Reregister the repaired device using the new device ID

If an OEM can't reregister the device, there are two options:

- The repair facility or CSP can reregister the device using MPC.
- The customer IT Admin should reregister the device via Intune (or MSfB).

Both ways of reregistering a device are shown in the following sections.

### Reregister from Intune

To reregister a Windows Autopilot device from Intune, an IT Admin would:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Navigate to **Devices** &gt; **Device onboarding** | **Enrollment** &gt; **Windows Autopilot** | **Devices**.
3. Select the **Import** option in the toolbar at the top to upload a CSV file containing the device ID of the device to be reregistered. The device ID was the 4K HH captured by the PowerShell script or OA3 tool described in the section Capture a new Windows Autopilot device ID (4K HH) from the device.

### Reregister from the Microsoft Partner Center (MPC)

To reregister a Windows Autopilot device from the Microsoft Partner Center MPC, an OEM or CSP would:

1. Sign in to the Microsoft Partner Center (MPC).
2. Navigate to the **Customer** &gt; **Devices** page.
3. Select **Add devices** to upload the CSV file.

When a repaired device is reregistering through MPC, the uploaded CSV file must contain the 4K HH for the device, and not just the PKID or Tuple (SerialNumber + OEMName + ModelName). If only the PKID or Tuple was used, the Windows Autopilot service would be unable to find a match in the Windows Autopilot database. No match would be found because no 4K HH info was previously submitted for this essentially "new" device and the upload fails, likely returning a **ZtdDeviceNotFound** error. For this reason, only upload the 4K HH. Don't upload the Tuple or PKID.

When including the 4K HH in the CSV file, the PKID or Tuple don't also need to be included. Those columns might be left blank, as shown in the following example:

![Screenshot of a CSV file in Excel with a hash value in the Hardware Hash column.](images/hh.png)

## Reset the device

The repair facility must reset the image back to a pre-OOBE state before returning it to the customer. This reset is needed because the device was required to be in Full OS or Audit Mode to capture the 4K HH. One way to reset the image is by using the built-in reset feature in Windows.

To use the reset feature in Windows on a device:

**Windows 10**:

1. Go to **Settings** &gt; **Update & Security** &gt; **Recovery**.
2. Select **Get started**.
3. In the **Reset this PC** window:

    1. Under **Choose an option**, select **Remove everything**.
    2. Under **How would you like to reinstall Windows?**, select either option.
    3. Under **Additional settings**, select **Next**.
    4. Under **Ready to reset this PC**, select the **Reset** button.

**Windows 11**:

1. Go to **Settings** &gt; **System** &gt; **Recovery**.
2. Under **Recovery options**, select the **Reset PC** button next to **Reset this PC**.
3. In the **Reset this PC** window:

    1. Under **Choose an option**, select **Remove everything**.
    2. Under **How would you like to reinstall Windows?**, select either option.
    3. Under **Additional settings**, select **Next**.
    4. Under **Ready to reset this PC**, select the **Reset** button.

However, the repair facility most likely doesn't have access to Windows because they lack the user credentials to sign in. In this case, they need to use other means to reimage the device, such as the Deployment Image Servicing and Management (DISM) tool:

- [OEM Deployment of Windows 11 desktop editions](/en-us/windows-hardware/manufacture/desktop/oem-deployment-of-windows-desktop-editions).
- [OEM Deployment of Windows 10 for desktop editions](/en-us/windows-hardware/manufacture/desktop/oem-deployment-of-windows-desktop-editions?view=windows-10&amp;preserve-view=true).

## Return the repaired device to the customer

The repaired device can now be returned to the customer. The device is auto-enrolled into the Windows Autopilot program on first boot-up during OOBE.

Important

If the repair facility **didn't** reimage the device, they could be sending it back in a potentially broken state. For example, there's no way to log into the device because it's dissociated from the only known user account.

A device can be **registered** for Windows Autopilot before being powered-on. However, the device isn't actually **deployed** to Windows Autopilot until it goes through OOBE. Therefore, resetting the device back to a pre-OOBE state is a required step.

## Fix pending and Attention required

If the profiles status of a device shows **Fix pending**, Windows Autopilot is in the process of attempting to register the device. If the profile status of a device shows **Fix pending** for an extended period of time and doesn't switch to **Assigned**, or if the profile status of the device switches to **Attention required**, then:

1. Manually deregister the device using the steps in the Deregister a device section.
2. Reregister the device.

For more information, see [Why is the Windows Autopilot profile not applied after a hardware change occurred on a device?](troubleshooting-faq#why-is-the-windows-autopilot-profile-not-applied-after-a-hardware-change-occurred-on-a-device-).

## Specific repair scenarios

This section covers the most common repair scenarios, and their impact on Windows Autopilot enablement.

Note

- The scenarios were tested using Intune only. No other MDMs were tested.
- In most test scenarios, the repaired and reregistered device needed to go through OOBE again for Windows Autopilot to be enabled.
- Motherboard replacement scenarios often result in lost data. Repair centers or customers should be reminded to back up data before repair.
- When a repair facility can't write device info into the BIOS of the repaired device, new processes need to be created to successfully enable Windows Autopilot.
- Repaired device should have the Product Key (DPK) pre-injected in the BIOS before capturing the new 4K HH (device ID).

For the **Supported** column in the following table:

- **Yes**: the device can be reenabled for Windows Autopilot.
- **No**: the device can't be reenabled for Windows Autopilot.

| Scenario | Supported | Microsoft Recommendation |
| --- | --- | --- |
| **Motherboard Replacement in general** | Yes | The recommended course of action for motherboard replacement scenarios is:  1. Windows Autopilot device is deregistered from the Windows Autopilot program.  2. The motherboard is replaced.  3. The device is reimaged (with BIOS info and DPK reinjected). ^1^ 4. A new Windows Autopilot device ID (4K HH) is captured off the device.  5. The repaired device is reregistered for the Windows Autopilot program using the new device ID.  6. The repaired device is reset to boot to OOBE.  7. The repaired device is shipped back to the customer. ^1^ It's not necessary to reimage the device if the repair technician has access to the customer's sign-in credentials. It's technically possible to successfully re-enable motherboard replacement and Windows Autopilot without keys or certain BIOS info (serial #, model name, etc.) However, doing so is only recommended for testing/educational purposes. |
| **Motherboard replacement when motherboard has a TPM chip enabled and only one onboard network card that also gets replaced** | Yes | 1. Deregister damaged device.  2. Replace motherboard.  3. To gain access, reimage device or sign-in using customer's credentials.  4. Write device info into BIOS.  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. |
| **Motherboard replacement when motherboard has an enabled TPM chip enabled and a second network interface that isn't replaced along with the motherboard** | No | This scenario breaks the Windows Autopilot experience. The resulting Device ID won't be stable until after TPM attestation is complete. Even then registration might give incorrect results because of ambiguity with MAC Address resolution. Therefore, this scenario isn't recommended. |
| **Motherboard replacement where the NIC card, HDD, and WLAN all remain the same after the repair** | Yes | 1. Deregister damaged device.  2. Replace motherboard with a new Replacement Digital Product Key (RDPK) preinjected in BIOS.  3. To gain access, reimage device or sign-in using customer's credentials.  4. Write old device info into BIOS (same s/n, model, etc.) ^2^ 5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. ^2^ For this and later scenarios, rewriting old device info wouldn't include the TPM 2.0 endorsement key, as the associated private key is locked to the TPM device. |
| **Motherboard replacement where the NIC card remains the same, but the HDD and WLAN are replaced** | Yes | 1. Deregister damaged device.  2. Replace motherboard (with new RDPK preinjected in BIOS).  3. Insert new HDD and WLAN.  4. Write old device info into BIOS (same s/n, model, etc.)  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. |
| **Motherboard replacement where the NIC card and WLAN remains the same, but the HDD is replaced** | Yes | 1. Deregister damaged device.  2. Replace motherboard (with new RDPK preinjected in BIOS).  3. Insert new HDD.  4. Write old device info into BIOS (same s/n, model, etc.)  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. |
| **Motherboard replacement where only the motherboard is replaced. All other parts remain same. The new motherboard was taken from a previously used device that has never been enabled for Windows Autopilot.** | Yes | 1. Deregister damaged device.  2. Replace motherboard (with new RDPK preinjected in BIOS).  3. To gain access, reimage device or sign-in using customer's credentials.  4. Write old device info into BIOS (same s/n, model, etc.)  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. |
| **Motherboard replacement where only the motherboard is replaced. All other parts remain same. The new motherboard was taken from a previously used device that has been Windows Autopilot-enabled before.** | Yes | 1. Deregister old device which motherboard is taken from.  2. Deregister damaged device that needs to be repaired.  3. Replace motherboard in repair device with motherboard from other Windows Autopilot device (with new RDPK preinjected in BIOS).  4. To gain access, reimage device or sign-in using customer's credentials.  5. Write old device info into BIOS (same s/n, model, etc.)  6. Capture new 4K HH.  7. Reregister repaired device.  8. Reset device back to OOBE.  9. Go through Windows Autopilot OOBE (customer).  10. Windows Autopilot successfully enabled.  The repaired device can also be used successfully as a normal, non-Windows Autopilot device. |
| **BIOS info excluded from motherboard replacement device** | No | Repair facility doesn't have BIOS tool to write device info into BIOS after Motherboard replacement.  1. Deregister damaged device.  2. Replace motherboard (BIOS does NOT contain device info).  3. Reimage and write DPK into image.  4. Capture new 4K HH.  5. Reregister repaired device.  6. Create Windows Autopilot profile for device.  7. Go through Windows Autopilot OOBE (customer).  8. Windows Autopilot FAILS to recognize repaired device. |
| **Motherboard replacement when there's no TPM** | Yes | Enabling Windows Autopilot devices without a TPM isn't recommended. However, it's possible to enable a Windows Autopilot device that doesn't have a TPM via user-driven mode. Pre-provision and self-deploying modes aren't supported without a TPM. When using user-driven mode:  1. Deregister damaged device.  2. Replace motherboard.  3. To gain access, reimage device or sign-in using customer's credentials.  4. Write old device info into BIOS (same s/n, model, etc.)  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reset device back to OOBE.  8. Go through Windows Autopilot OOBE (customer).  9. Windows Autopilot successfully enabled. |
| **New DPK written into image on repaired Windows Autopilot device with a new motherboard** | Yes | Repair facility replaces normal motherboard on damaged device. motherboard doesn't contain any DPK in the BIOS. Repair facility writes DPK into image after motherboard replacement.  1. Deregister damaged device.  2. Replace motherboard - BIOS does NOT contain DPK info.  3. To gain access, reimage device or sign-in using customer's credentials.  4. Write device info into BIOS (same s/n, model, etc.)  5. Capture new 4K HH.  6. Reset or reimage device to pre-OOBE and write DPK into image.  7. Reregister repaired device.  8. Go through Windows Autopilot OOBE.  9. Windows Autopilot successfully enabled. |
| **New Repair Product Key (RDPK)** | Yes | Using a motherboard with a new RDPK preinjected results in a successful Windows Autopilot refurbishment scenario.  1. Deregister damaged device.  2. Replace motherboard (with new RDPK preinjected in BIOS).  3. Reimage or rest image to pre-OOBE.  4. Write device info into BIOS.  5. Capture new 4K HH.  6. Reregister repaired device.  7. Reimage or reset image to pre-OOBE.  8. Go through Windows Autopilot OOBE.  9. Windows Autopilot successfully enabled. |
| **No Repair Product Key (RDPK) injected** | No | This scenario violates Microsoft policy and breaks the Windows Autopilot experience. |
| **Reimage damaged Windows Autopilot device that wasn't deregistered before repair** | Yes, but the device is still associated with previous tenant ID, so should only be returned to same customer. | 1. Reimage damaged device.  2. Write DPK into image.  3. Go through Windows Autopilot OOBE.  4. Windows Autopilot successfully enabled to same tenant ID as before. |
| **Disk replacement from a non-Windows Autopilot device to a Windows Autopilot device** | Yes | 1. Don't deregister damaged device before repair.  2. Replace HDD on damaged device.  3. Reimage or reset image back to OOBE.  4. Go through Windows Autopilot OOBE (customer).  5. Windows Autopilot successfully enabled (repaired device recognized as its previous self). |
| **Disk replacement from one Windows Autopilot device to another Windows Autopilot device** | Maybe | If the device from which the HDD is taken was itself previously deregistered from Windows Autopilot, then that HDD can be used in a repair device. The newly repaired device won't have the proper Windows Autopilot experience if the HDD wasn't previously deregistered from Windows Autopilot before being used in the repaired device.  Assuming the used HDD was previously deregistered (before being used in this repair):  1. Deregister damaged device.  2. Replace HDD on damaged device using an HDD from another deregistered Windows Autopilot device.  3. Reimage or rest the repaired device back to a pre-OOBE state.  4. Go through Windows Autopilot OOBE (customer).  5. Windows Autopilot successfully enabled. |
| **Non-OEM add-in network card replacement** | No | Any scenario where a network card is used other than the OEM on-board NIC breaks the Windows Autopilot experience. These scenarios include the following scenarios:  • From a non-Windows Autopilot device to a Windows Autopilot device.  • From one Windows Autopilot device to another Windows Autopilot device.  • From a Windows Autopilot device to a non-Windows Autopilot device.  These scenarios aren't recommended. |
| **Memory replacement** | Yes | Replacing the memory on a damaged device doesn't negatively affect the Windows Autopilot experience on the device. No deregistration/reregistration is needed. The repair technician simply needs to replace the memory. |
| **GPU replacement** | Yes | Replacing one or more GPUs on a damaged device doesn't negatively affect the Windows Autopilot experience on that device. No deregistration/reregistration is needed. The repair technician simply needs to replace the GPU. |

Important

When parts are scavenged from another Windows Autopilot device, Microsoft recommends to unregister the scavenged device from Windows Autopilot, scavenge it, and then **never register the scavenged device again for Windows Autopilot**. Reusing parts in this way might cause two active devices to end up with the same ID with no possibility of distinguishing between the two.

To resolve the issue when two active devices end up with the same ID, follow these steps:

1. Deregister affected devices from Microsoft Intune.
2. Collect hardware hashes directly from physical devices rather than relying on OEM-provided hash data.
3. To ensure correct association of device serial numbers, re-register the devices in Windows Autopilot using the hashes collected from the physical devices in the previous step.

The following parts can be replaced without compromising Windows Autopilot enablement or requiring special additional repair steps:

- Memory (RAM or ROM).
- Power Supply.
- Video Card.
- Card Reader.
- Sound card.
- Expansion card.
- Microphone.
- Webcam.
- Fan.
- Heat sink.
- CMOS battery.

Other repair scenarios not yet tested and verified include:

- Daughterboard replacement.
- CPU replacement.
- Wifi replacement.
- Ethernet replacement.

## FAQ

| Question | Answer |
| --- | --- |
| What to do if another customer's welcome page is displayed? | If another customer's welcome page is displayed on a replacement device or refurbished motherboard, a case needs to be raised to Microsoft to fix the device ownership. A case can be opened through the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) by selecting the Help and Support option outlined [here](/en-us/intune/get-support). If there isn't access to Microsoft Intune, a case can be submitted through Microsoft Store for Business by selecting **Manage** &gt; **Support** and selecting **Technical Support**. A case can also be submitted through the Microsoft Volume Licensing Center agreement. Instructions on how to submit a case are outlined at [Microsoft Software Assurance - Support Incident Submission](https://support.microsoft.com/topic/microsoft-software-assurance-support-incident-submission-74a9a148-9a75-ecc8-4420-14191e634d65). Title all cases **Windows Autopilot Deregistration Request** to streamline requests. |
| We have a tool that programs product information into the BIOS after the motherboard replacement. Do we still need to submit a CBR report for the device to be Windows Autopilot-capable? | No. Not if the in-house tool writes the minimum necessary information into the BIOS that the Windows Autopilot program looks for to identify the device, as described earlier in this document. |
| What if only some components are replaced rather than the full motherboard? | It's true that some limited repairs don't prevent the Windows Autopilot algorithm from successfully matching the post-repair device with the pre-repair device. However, Microsoft recommends to always go through the motherboard replacement steps described in the previous sections to ensure success. |
| How does a repair technician gain access to a broken device if they don't have the customer's sign-in credentials? | The technician has to reimage the device and use their own credentials during the repair process. |