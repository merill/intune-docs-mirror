---
layout: Conceptual
title: Windows Autopilot Reset | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/windows-autopilot-reset
author: iceorbital
ms.author: acabello
ms.reviewer: madakeva
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Windows Autopilot Reset takes the device back to a business-ready state, allowing the next user to sign in and get productive quickly and easily.
ms.date: 2026-10-28T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: ca1cdb90-ea7b-7178-810a-8242b88bec91
document_version_independent_id: ca1cdb90-ea7b-7178-810a-8242b88bec91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/windows-autopilot-reset.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: windows-autopilot-reset
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/windows-autopilot-reset.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 3fc857fb-18cf-578a-4da1-1988efe09795
---

# Windows Autopilot Reset | Microsoft Learn

Windows Autopilot Reset takes the device back to a business-ready state, so the next user can sign in and start working quickly and easily. Specifically, Windows Autopilot Reset:

- Removes personal files, apps, and settings.
- Reapplies a device's original settings.
- Sets the region, language, and keyboard to the original values.
- Maintains the device's identity connection to Microsoft Entra ID.
- Maintains the device's management connection to Intune.

The Windows Autopilot Reset process automatically keeps information from the existing device:

- Wi-Fi connection details.
- Provisioning packages previously applied to the device.
- A provisioning package present on a USB drive when the reset process starts.
- Microsoft Entra device membership and mobile device management (MDM) enrollment information.
- Simple Certificate Enrollment Protocol (SCEP) certificates.

Windows Autopilot Reset blocks the user from accessing the desktop until it restores this information, including reapplying any provisioning packages. For devices enrolled in an MDM service, Windows Autopilot Reset also blocks until an MDM sync is completed.

Note

Windows Autopilot Reset doesn't support Microsoft Entra hybrid joined devices or Surface Hub devices. For Microsoft Entra hybrid joined devices and Surface Hub devices, you need to perform a full device wipe. When a hybrid device goes through a full device reset, it might take up to 24 hours for it to be ready to deploy again. You can expedite the request by re-registering the device.

## Scenarios

Windows Autopilot Reset supports two scenarios:

- Local reset started by IT personnel or other administrators from the organization.
- Remote reset started remotely by IT personnel via an MDM service such as Microsoft Intune.

Each scenario has its own requirements and configuration details.

## Reset devices with local Windows Autopilot Reset

IT admins can use a local Windows Autopilot Reset to:

- Quickly remove personal files, apps, and settings.
- Reset Windows devices from the lock screen.
- Apply original settings and management enrollment, including Microsoft Entra ID and device management.

The device is then ready to use. By using a local Windows Autopilot Reset, IT admins return devices to a fully configured or known IT-approved state.

To enable local Windows Autopilot Reset in supported versions of Windows:

1. Enable the policy for the feature.
2. Trigger a reset for each device.

### Enable local Windows Autopilot Reset

To enable a local Windows Autopilot Reset, configure the **DisableAutomaticReDeploymentCredentials** policy. This policy is documented in the [CredentialProviders](/en-us/windows/client-management/mdm/policy-csp-credentialproviders) section, under **CredentialProviders/DisableAutomaticReDeploymentCredentials** configuration service provider (CSP) policy. By default, local Windows Autopilot Reset is disabled. This default ensures that a local Windows Autopilot Reset isn't triggered accidentally.

Use one of these methods to set the policy:

- MDM provider

    - When you use Intune, create a new device configuration profile with the following settings:

        - **Platform** = **Windows 10 and later**.
        - **Profile type** = **Device restrictions**.
        - **Category** = **General**.
        - **Autopilot Reset** = **Allow**. Deploy this setting to all devices where a local reset should be permitted.
    - If you use an MDM provider other than Intune, check the MDM provider's documentation on how to set this policy.
- Windows Configuration Designer

    Use [Windows Configuration Designer](/en-us/windows/configuration/provisioning-packages/provisioning-create-package) to set the **Runtime settings &gt; Policies &gt; CredentialProviders &gt; DisableAutomaticReDeploymentCredentials** setting to `0` and then create a provisioning package.
- Set up School PCs app

    The latest release of the **Set up School PCs** app supports enabling local Windows Autopilot Reset.

### Trigger local Windows Autopilot Reset

A local Windows Autopilot Reset is a two-step process:

1. Trigger the Windows Autopilot Reset.
2. Authenticate.

After you perform these two steps, the Windows Autopilot Reset runs. When the Windows Autopilot Reset finishes, the device is ready to use again.

**To trigger a local Windows Autopilot Reset:**

On the device where you want to perform the local Windows Autopilot Reset:

1. If you have a provisioning package, plug in the USB drive that contains the provisioning package.
2. From the Windows device lock screen, enter the keystroke CTRL + WIN + R.

    These keystrokes open a custom sign-in screen for the local Windows Autopilot Reset. The screen serves two purposes:

    - Confirm that the user has the right to trigger local Windows Autopilot Reset.
    - Notify the user if the process uses a provisioning package created by using Windows Configuration Designer.
3. To trigger the local Windows Autopilot Reset, sign in to the device with an account that has local admin credentials.

When you trigger the local Windows Autopilot Reset, the reset process starts. When provisioning is complete, the device is ready to use again.

Note

When local Windows Autopilot Reset is used on a device, the device's primary user and the Microsoft Entra device owner aren't updated. Admins can update them manually after the Windows Autopilot Reset completes.

## Reset devices with remote Windows Autopilot Reset

You can use an MDM service such as Microsoft Intune to start the remote Windows Autopilot reset process. Resetting in this way avoids the need for IT staff to visit each machine to start the process.

To enable a device for a remote Windows Autopilot Reset, the device must be MDM managed and joined to Microsoft Entra ID. Also, for Intune, the Intune Service Administrator role is required for remote Windows Autopilot Reset. For more information, see [Add users and grant administrative permission to Intune](/en-us/intune/fundamentals/tenant-administration/add-users).

### Triggering a remote Windows Autopilot Reset

To trigger a remote Windows Autopilot Reset by using Intune, follow these steps:

1. In the Intune admin center, go to the **Devices** tab.
2. In the **All devices** view, select the targeted reset devices and then select **More** to view device actions.
3. Select **Autopilot Reset** to start the reset task.

When the reset is complete, the device is again ready for use.

Note

When remote Windows Autopilot Reset is used on a device, the device's primary user and the Microsoft Entra device owner is removed. The next user who signs in after the reset will be set as the primary user and Microsoft Entra device owner. Shared devices will remain shared after the Windows Autopilot Reset.

## Troubleshooting

Windows Autopilot Reset requires that the [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) is correctly configured and enabled on the device. Before the Windows Autopilot Reset is started, it checks if WinRE is configured and enabled. If WinRE isn't configured and enabled, the Windows Autopilot reset fails immediately on the device and an error such as `Error code: ERROR_NOT_SUPPORTED (0x80070032)` is reported in the logs.

To make sure WinRE is enabled, use the [REAgentC.exe tool](/en-us/windows-hardware/manufacture/desktop/reagentc-command-line-options) to run the following command:

```cmd
reagentc.exe /enable
```

If Windows Autopilot Reset fails after enabling WinRE, or WinRE can't be enabled, contact [Microsoft Support](https://support.microsoft.com) for assistance.