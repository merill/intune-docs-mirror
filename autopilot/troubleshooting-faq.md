---
layout: FAQ
title: Windows Autopilot troubleshooting FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/troubleshooting-faq
summary: >
  <p><strong>Applies to:</strong></p>

  <ul>

  <li><a href="/windows/release-health/supported-versions-windows-client#windows-11-supported-versions">Windows 11</a>.</li>

  <li><a href="/windows/release-health/supported-versions-windows-client#windows-10-supported-versions">Windows 10</a>.</li>

  </ul>

  <p>This article provides troubleshooting for common Windows Autopilot issues.</p>
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
description: Troubleshooting of common Windows Autopilot issues
ms.date: 2025-04-21T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: faq
locale: en-us
document_id: 73a41849-c3fc-342c-1cb6-38acd9ecb2da
document_version_independent_id: 73a41849-c3fc-342c-1cb6-38acd9ecb2da
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/troubleshooting-faq.yml
site_name: Docs
depot_name: MSDN.autopilot
page_type: faq
toc_rel: toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: troubleshooting-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/troubleshooting-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8726e7ef-3eda-f125-7004-264490b77276
---

# Windows Autopilot troubleshooting FAQ | Microsoft Learn

**Applies to:**

- [Windows 11](/en-us/windows/release-health/supported-versions-windows-client#windows-11-supported-versions).
- [Windows 10](/en-us/windows/release-health/supported-versions-windows-client#windows-10-supported-versions).

This article provides troubleshooting for common Windows Autopilot issues.

## Troubleshooting Windows Autopilot overview

### What concepts should be understood when troubleshooting Windows Autopilot?

Windows Autopilot is designed to simplify all parts of the Windows device lifecycle, but there are always situations where issues might arise. When troubleshooting an issue, it's helpful to understand:

- The Windows Autopilot process flow.
- How Windows Autopilot device profiles are downloaded.
- Key activities to perform during troubleshooting.

### What is the Windows Autopilot process flow?

Whether performing user-driven or self-deploying device deployments, the troubleshooting process is about the same. It's useful to understand the flow for a specific device:

1. A network connection is established. The connection can be a wireless (Wi-fi) or wired (Ethernet) connection.
2. The Windows Autopilot profile is downloaded. When a wired connection is used, or a wireless connection is established, the profile downloads from the Windows Autopilot deployment service as soon as the network connection is in place.
3. User authentication occurs. During a user-driven deployment, the user enters their Microsoft Entra credentials, which is then validated.
4. Microsoft Entra join occurs. For user-driven deployments, the device is joined to Microsoft Entra ID using the specified user credentials. For self-deploying scenarios, the device is joined without specifying any user credentials.
5. Automatic mobile device management (MDM) enrollment occurs. As part of the Microsoft Entra join process, the device enrolls in the MDM service configured in Microsoft Entra ID (for example, Microsoft Intune).
6. Settings are applied. If the [enrollment status page](enrollment-status) is configured, most settings are applied while the enrollment status page is displayed. If not configured or available, settings will be applied after the user is signed in.

### How are Windows Autopilot device profiles downloaded?

When an Internet-connected Windows device boots up, it attempts to connect to the Windows Autopilot service and download a Windows Autopilot profile. The Windows Autopilot profile is downloaded as soon as possible, and again after each reboot.

Note

At this stage, it's important that a Windows Autopilot profile exists in the tenant so that a blank profile isn't cached locally on the device. If necessary, a new Windows Autopilot profile can be retrieved by rebooting the device.

If a computer needs to be rebooted during the Windows out-of-box experience (OOBE) to retrieve a new Windows Autopilot profile:

1. Select Shift-F10 to open a command prompt window.
2. In the command prompt window, enter one of the following two commands:

    - `shutdown.exe /r /t 0` to **restart** immediately.
    - `shutdown.exe /s /t 0` to **shut down** immediately.

For more information, see [Windows Setup Command-Line Options](/en-us/windows-hardware/manufacture/desktop/windows-setup-command-line-options).

### What are the key activities to perform when troubleshooting Windows Autopilot?

The key troubleshooting activities to perform are:

- Review configuration: Are Microsoft Entra ID and Microsoft Intune or a non-Microsoft mobile device management (MDM) service configured as specified in [Windows Autopilot configuration requirements](requirements?tabs=configuration)?
- Check network connectivity: Can the device access the services described in [Windows Autopilot networking requirements](requirements?tabs=networking)?
- Windows out-of-box experience (OOBE) behavior: Are the expected OOBE screens displayed? Is the Microsoft Entra credentials page customized with organization-specific details as expected?
- Microsoft Entra join issues: Is the device able to join Microsoft Entra ID?
- MDM enrollment issues: Is the device able to enroll in Microsoft Intune or non-Microsoft MDM service?
- Review logs that are automatically collected upon Windows Autopilot failure. For more information, see [Collect diagnostics from a Windows device](/en-us/intune/device-management/actions/collect-diagnostics).

### How can additional detailed troubleshooting information be enabled?

On [Windows 11](/en-us/windows/release-health/supported-versions-windows-client#windows-11-supported-versions), the Windows Autopilot diagnostic page can be opened to view additional detailed troubleshooting information about the Windows Autopilot provisioning process. To enable the Windows Autopilot diagnostics page:

1. Go to the [ESP profile](/en-us/intune/intune-service/enrollment/windows-enrollment-status) where the Windows Autopilot diagnostics page needs to be enabled.
2. Make sure that **Show app and profile configuration progress** is selected to **Yes**.
3. Make sure that **Turn on log collection and diagnostics page for end users** is selected to **Yes**.

To access any diagnostic information once the diagnostic page is enabled, select the **View Diagnostics** button or enter the keystroke CTRL + SHIFT + D. The diagnostics page is currently supported under the following conditions:

- Windows 11.
- Windows Autopilot user-driven mode.
- When signing in with a Work or School account. Personal Microsoft accounts aren't supported.

Note

- By default diagnostics are automatically collected upon a Windows Autopilot failure. For more information, see [Collect diagnostics from a Windows device](/en-us/intune/device-management/actions/collect-diagnostics).
- For diagnostics to be able to upload successfully from the client, make sure that the URL `lgmsapeweu.blob.core.windows.net` isn't blocked on the network.

### Where does Windows Autopilot log to?

Windows Autopilot logs entries into the event log. The log entries can be used to see details related to the Windows Autopilot profile settings and OOBE flow. These entries can be viewed using Event Viewer. Review the information in Event Viewer at **Application and Services Logs** -&gt; **Microsoft** -&gt; **Windows** -&gt; **ModernDeployment-Diagnostics-Provider** -&gt; **Autopilot**.

### What do the different Event IDs mean in the Windows Autopilot event log entries in Event Viewer?

The following events might be recorded, depending on the scenario and profile configuration:

| **Event ID** | **Type** | **Message** | **Description** |
| --- | --- | --- | --- |
| **100** | Warning | **Autopilot policy [name] not found.** | This error is typically a temporary problem, while the device is waiting for a Windows Autopilot profile to be downloaded. |
| **101** | Info | **AutopilotGetPolicyDwordByName succeeded: policy name = [setting name]; policy value = [value].** | This message shows Windows Autopilot retrieving and processing numeric OOBE settings. |
| **103** | Info | **AutopilotGetPolicyStringByName succeeded: policy name = [name]; value = [value].** | This message shows Windows Autopilot retrieving and processing OOBE setting strings such as the Microsoft Entra tenant name. |
| **109** | Info | **AutopilotGetOobeSettingsOverride succeeded: OOBE setting [setting name]; state = [state].** | This message shows Windows Autopilot retrieving and processing state-related OOBE settings. |
| **111** | Info | **AutopilotRetrieveSettings succeeded.** | This message means that the settings stored in the Windows Autopilot profile that control the OOBE behavior were retrieved successfully. |
| **153** | Info | **AutopilotManager reported the state changed from [original state] to [new state].** | Usually, this message says **ProfileState\_Unknown to ProfileState\_Available**. This case indicates that a profile was available and downloaded for the device and that the device is ready to deploy using Windows Autopilot. |
| **160** | Info | **AutopilotRetrieveSettings beginning acquisition.** | This message shows that Windows Autopilot is getting ready to download the needed Windows Autopilot profile settings. |
| **161** | Info | **AutopilotManager retrieve settings succeeded.** | The Windows Autopilot profile was successfully downloaded. |
| **163** | Info | **AutopilotManager determined download isn't required and the device is already provisioned. Clean or reset the device to change this.** | This message indicates that a Windows Autopilot profile is present on the device. The **Sysprep /Generalize** process typically removes a Windows Autopilot profile. |
| **164** | Info | **AutopilotManager determined Internet is available to attempt policy download.** |  |
| **171** | Error | **AutopilotManager failed to set TPM identity confirmed. HRESULT=[error code].** | This message indicates an issue performing TPM attestation, needed to complete the self-deploying mode process. |
| **172** | Error | **AutopilotManager failed to set Autopilot profile as available. HRESULT=[error code].** | This error is typically related to event ID 171. |
| **807** | Error | **ZtdDeviceIsNotRegistered** | Validate that the device's hardware hash is properly uploaded to Intune and that the device is assigned to a deployment profile. |
| **809** | Error | **ZtdDeviceHasNoAssignedProfile - Assigned profile does not exist.** | The Windows Autopilot profile assigned to the device was deleted without first getting cleaned up. Assign a different Windows Autopilot profile to the device and then attempt to re-enroll the device. |
| **815** | Error | **ZtdDeviceHasNoAssignedProfile - No profile assigned to the device, and no default profile found in the tenant.** | A Windows Autopilot profile wasn't found assigned to the device. Validate that a Windows Autopilot profile is assigned to the device. |
| **908** | Error | **SerialNumberMismatch** **ProductKeyIdMismatch** | There's a mismatch between the serial number or product key recorded in Windows Autopilot and the physical hardware that is preventing enrollment. Reregister the device and then attempt to re-enroll the device. |

### Where are the Windows Autopilot profile settings received from the Windows Autopilot deployment service stored?

Windows Autopilot profile settings received from the Windows Autopilot deployment service are stored in the device's registry. This information can be found in the registry at the following registry key:

`HKLM\SOFTWARE\Microsoft\Provisioning\Diagnostics\Autopilot`

Available registry entries include:

| **Value** | **Description** |
| --- | --- |
| **AadTenantId** | The GUID of the Microsoft Entra tenant the user signed into. The user receives an error if this entry doesn't match the tenant that was used to register the device. |
| **CloudAssignedTenantDomain** | The Microsoft Entra tenant the device is registered with, for example, `contosomn.onmicrosoft.com`. If the device isn't registered with Windows Autopilot, this value is blank. |
| **CloudAssignedTenantId** | The GUID of the Microsoft Entra tenant the device registered with. The GUID corresponds to the tenant domain from the CloudAssignedTenantDomain registry value. If the device isn't registered with Windows Autopilot, this value is blank. |
| **IsAutopilotDisabled** | If set to 1, this registry value indicates that the device isn't registered with Windows Autopilot. This state could also indicate that the Windows Autopilot profile couldn't be downloaded because of network connectivity or firewall issues, or network timeouts. |
| **TenantMatched** | This entry is set to 1 if the user's tenant ID matches the tenant ID that the device was registered with. If this registry value is 0, the user would be shown an error and forced to start over. |
| **CloudAssignedOobeConfig** | A bitmap that shows which Windows Autopilot settings were configured. Values include: **SkipCortanaOptIn** = 1, **OobeUserNotLocalAdmin** = 2, **SkipExpressSettings** = 4, **SkipOemRegistration** = 8, **SkipEula** = 16 |

### Can ETW tracing be used with Windows Autopilot?

ETW tracing can be used to get detailed information from Windows Autopilot and related components. The ETW trace files can be viewed using the Windows Performance Analyzer or similar tools. For more information, see [Troubleshooting Windows Autopilot](/en-us/archive/blogs/mniehaus/troubleshooting-windows-autopilot-level-300400).

### Why is the Intune Connector for Active Directory not logging in Event Viewer even though logging is enabled?

The Intune Connector for Active Directory originally logged in the **Event Viewer** directly under **Applications and Services Logs** in a log called **ODJ Connector Service**. However, logging for the Intune Connector for Active Directory has since moved to the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. If the **ODJ Connector Service** log at the original location is empty or not updating, check the new path location instead.

## Troubleshooting Windows Autopilot device import and enrollment

### Why is error code "0x80180014" occurring when trying to re-enroll a previously enrolled device?

Error code **0x80180014** can occur under either of the following scenarios:

1. Microsoft Intune changed the Windows Autopilot self-deployment mode and pre-provisioning mode experience. To reuse a device, the device record created by Intune must be deleted.

    This change impacts all Windows Autopilot deployments that use the self-deployment or pre-provisioning mode. This change impacts devices when they devices are reused, reset, or when redeploying a profile.

    To resolve and fix the issue in this scenario and redeploy the device using Windows Autopilot, follow these steps:

    1. Sign into the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, select **Devices** in the left hand pane.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Enrollment** screen, under **Windows Autopilot**, select **Devices**.
    6. Select the device that is experiencing the error, and then in the toolbar select **Unblock device**.
    7. Redeploy the Windows Autopilot deployment profile.

        Note

        A success message might not display after selecting **Unblock device**, but the device is ready to be used again.
2. Windows MDM enrollment is disabled in the Intune tenant.

    To resolve and fix the issue in this scenario and redeploy the device using Windows Autopilot, follow these steps:

    1. Sign into the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, select **Devices** in the left hand pane.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Enrollment** screen, under **Enrollment options**, select **Device platform restriction**.
    6. In the **Enrollment restrictions** screen, under **Device type restrictions**, select **All Users** under the **Name** column.
    7. In the **All Users** screen that opens, under **Manage**, select **Properties**.
    8. In the **Properties** screen that opens, next to **Platform settings**, select the **Edit** link.
    9. In the **Edit restriction** screen that opens:
    10. Locate **Windows (MDM)** under the **Type** column.
    11. Make sure that **Windows (MDM)** is set to **Allow** under the **Platform** column.
    12. If **Windows (MDM)** is set to **Block**, change it to **Allow**.
    13. Select **Review + save**, and then either **Save** if a setting was changed, or **Cancel** if not settings were changed.
    14. Repeat the above steps for any additional restrictions that might exist in the **Enrollment restrictions** screen other than **All Users**. Only restrictions for the **Windows** platform need to be verified.

    Note

    When multiple restrictions exist, restrictions might exist that only allow certain groups MDM enrollment. Some of the restrictions blocking MDM enrollment might be valid based on what group the restrictions are assigned to. When experiencing this problem, verify that the device isn't a member of one of the groups where there's MDM enrollment is blocked. Alternatively, if applicable change the MDM enrollment setting for that restriction to **Allow**.

In both of these scenarios, in addition to error **0x80180014** occurring, the Event Tracing for Windows (ETW) logs might also show the following mobile device management (MDM) error:

`MDM Enroll: Server Returned Fault/Code/Subcode/Value=(DeviceNotSupported) Fault/Reason/Text=(Enrollment blocked for AP device by SDM One Time Limit Check)`

### When trying to import a CSV file with a device hardware hash, why does nothing happen when selecting Import?

This issue usually occurs because the device hash in the CSV file is incorrectly formatted. The issue can be confirmed by running a network trace while the issue occurs. Most likely the device hash in the CSV file is incorrectly formatted if an error **400** occurs in the network trace. The message body of the **400** error message shows:

`Cannot convert the literal '[DEVICEHASH]' to the expected type 'Edm.Binary'`

Anything that corrupts the collected hash can cause this error. One possibility is that the hash itself fails to be decoded, even if the hash is valid.

The device hash is Base64. At the device level, it's encoded as unpadded Base64, but Windows Autopilot expects padded Base64. Usually, the payload doesn't require padding and the process works. Sometimes, however, the payload doesn't line up cleanly and padding is necessary. In this case, the **400** error message occurs. PowerShell's Base64 decoder also expects padded Base64, so this decoder can be used to validate that the hash is properly padded.

The "A" characters at the end of the hash are effectively empty data. Each character in Base64 is 6 bits. A in Base64 is 6 bits equal to 0. Deleting or adding **A**s at the end doesn't change the actual payload data.

To resolve and fix this issue, the hash needs to be modified. The new value then needs to be tested until PowerShell succeeds in decoding the hash. The result is mostly illegible, which is fine as long as the error **Invalid length for a Base-64 char array or string** isn't displayed.

To test the base64, use the following PowerShell:

```powershell
[System.Text.Encoding]::ascii.getstring( [System.Convert]::FromBase64String("DEVICE HASH"))
```

As an example:

```powershell
[System.Text.Encoding]::ascii.getstring( [System.Convert]::FromBase64String("Q29udG9zbwAAA"))
```

This particular example isn't a device hash, but it's a misaligned unpadded Base64 so it's good for testing.

Now for the padding rules. The padding character is "=". The padding character can only be at the end of the hash, and there can only be a maximum of two padding characters. Here's the basic logic.

- Does decoding the hash fail?
    - Yes: Are the last two characters "="?
        - Yes: Replace both "=" with a single "A" character, then try again
        - No: Add another "=" character at the end, then try again
- No: That hash is valid

Looping the logic on the previous example hash, we get the following permutations:

- Q29udG9zbwAAA
- Q29udG9zbwAAA=
- Q29udG9zbwAAA==
- Q29udG9zbwAAAA
- Q29udG9zbwAAAA=
- **Q29udG9zbwAAAA==** - This result has valid padding.

Replace the collected hash with this new padded hash then try to import again.

### Why is the Windows Autopilot profile not applied after a hardware change occurred on a device?

The Windows Autopilot profile isn't applied if the following conditions are met:

- A hardware change occurs on a device.
- The device is reimaged to a Windows version before one of the following versions:

    - Windows 11, version 21H2 with [KB5017383](https://support.microsoft.com/topic/september-20-2022-kb5017383-os-build-22000-1042-preview-62753265-68e9-45d2-adcb-f996bf3ad393).
    - [Windows 10, versions 22H2](/en-us/windows/release-health/supported-versions-windows-client#windows-10-supported-versions).

This behavior is expected.

The message **Fix pending** or **Attention required** might also be displayed in the **Windows Autopilot devices** page for the device. These messages indicate that a hardware change occurred on the device. When the link for the **Fix pending** status is selected, the following message appears:

`We've detected a hardware change on this device. We're trying to automatically register the new hardware. You don't need to do anything now; the status will be updated at the next check in with the result.`

To resolve and fix this issue, deregister and re-register the device. For more information including how to deregister a device, see the following articles:

- [Deregister a device](registration-overview#deregister-a-device).
- [Return of key functionality for Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/return-of-key-functionality-for-windows-autopilot-sign-in-and/ba-p/3583130).
- [Windows Autopilot motherboard replacement scenario guidance](autopilot-motherboard-replacement).

### Why is the join type for a device showing as "Microsoft Entra registered" instead of "Microsoft Entra joined"?

This issue occurs if the device was previously registered in Microsoft Entra ID before it was joined to Microsoft Entra ID. The device possibly registered in Microsoft Entra ID via something like a [Workplace join](/en-us/entra/identity/devices/concept-device-registration). If the Microsoft Entra ID registered device isn't deleted from Microsoft Entra ID before the device is joined to Microsoft Entra ID, then the previous trust type is retained in the record. Joining an existing Microsoft Entra registered device to Microsoft Entra ID results in the Windows Autopilot device showing as **Microsoft Entra registered** instead of **Microsoft Entra joined**.

To resolve and fix this issue, before registering an existing Microsoft Entra ID registered device as a Windows Autopilot device, the following existing device objects for the device should be deleted:

- Microsoft Intune.
- Microsoft Entra ID.
- Windows Autopilot.

After all device objects are deleted, re-register the device as a Windows Autopilot device and then re-enroll the device. For more information on properly deleting all of the device objects, see [Deregister a device](registration-overview#deregister-a-device).

### Why is enrollment in Microsoft Intune or a non-Microsoft MDM solution failing with an error code "80180018"?

To troubleshoot enrollment issues in Microsoft Intune such as the error code **80180018** in the **Something went wrong** error page, see [Troubleshooting Windows device enrollment errors in Intune](/en-us/troubleshoot/mem/intune/device-enrollment/troubleshoot-windows-enrollment-errors). Common issues can include:

- Incorrect or missing licenses assigned to the user.
- Too many devices enrolled for the user.

### Why does Windows Autopilot Reset fail immediately with an error?

See [Windows Autopilot Reset: Troubleshooting](windows-autopilot-reset#troubleshooting) for more help if Windows Autopilot Reset fails immediately with the error:

`Ran into trouble. Please sign in with an administrator account to see why and reset manually.`

### Why are Windows Autopilot Hybrid deployments failing during ESP with error code "0x80070774"?

Error **0x80070774** might occur if there's a domain mismatch between where the Intune Connector for Active Directory is installed and where device configurations are targeted. For example, the Intune Connector for Active Directory is installed on one Active Directory domain but devices are configured for another. To resolve this issue, configure the Intune Connector for Active Directory in the matching domain.

## Troubleshooting Windows OOBE issues during Windows Autopilot

### Why is the Windows out-of-box experience (OOBE) not running as expected during Windows Autopilot?

It's useful to check if the device received a Windows Autopilot profile. If the device did receive a Windows Autopilot profile, verify that the settings in the profile are correct.

### What is the cause of the error message "Can't connect to the URL of your organization's MDM terms of use."?

This error message usually indicates an issue with licensing. The complete error message reads:

`Something went wrong`

`Can't connect to the URL of your organization's MDM terms of use. Try again, or contact your system administrator with the problem information from this page.`

Verify that the user who is signing into the device has a valid Intune, EMS, or Microsoft 365 license.

## Troubleshooting Microsoft Entra join issues

### What is the most common issue joining a device to Microsoft Entra ID?

The most common issue joining a device to Microsoft Entra ID is related to Microsoft Entra permissions. Make sure that the correct configuration is in place to allow users to join devices to Microsoft Entra ID. For more information, see [Configuration requirements](requirements?tabs=configuration).

### What happens if a user attempts to join more devices to Microsoft Entra ID then allowed?

Errors occur if a user exceeds the allowed number of devices they can join. This default limit is 50 devices but can be configured in Microsoft Entra ID. For more information, see [Understand Intune and Microsoft Entra device limit restrictions](/en-us/intune/intune-service/enrollment/device-limit-intune-azure).

### Why did deleting a device's object in Microsoft Entra ID cause the device to not be able to join Microsoft Entra ID any longer?

A Microsoft Entra device is created upon import. It's important this object isn't deleted. The object acts as Windows Autopilot's anchor in Microsoft Entra ID for group membership and targeting, including the profile. Deleting it might lead to Microsoft Entra join errors. If this object is deleted, the issue can be fixed by deleting and reimporting the device as a Windows Autopilot device. Deleting and reimporting the device as a Windows Autopilot device recreates the associated object in Microsoft Entra ID.

## Troubleshooting policy conflicts with Windows Autopilot

### Why is the web sign-in option missing at the Windows sign-in screen after Windows Autopilot pre-provisioning completes?

The [Device password policies](/en-us/intune/device-security/security-baselines/ref-windows-mdm-settings#device-lock) in the Security Baseline causes issues after pre-provisioning. To resolve, change the password settings in Security Baseline to **Not Configured** or assign the baseline to a user group.

### Can policies conflict with Windows Autopilot working correctly?

There are a significant number of policy settings available for Windows, including:

- Native mobile device management (MDM) policies.
- Group policy (ADMX-backed) settings.

Some policy settings can cause issues in some Windows Autopilot scenarios. These issues can arise because of how the policies change Windows behavior. If any of these issues are discovered, remove the policy in question to resolve the issue.

### What are some of the known policies that conflict with Windows Autopilot?

The following policies are known to cause issues with Windows Autopilot. Make sure to configure the policies appropriately so that they don't conflict with Windows Autopilot:

| **Policy** | **More information** |
| --- | --- |
| **Disallow changing of language/region/keyboard** | This group policy object (GPO) isn't supported during the out-of-box experience (OOBE) flow as it impacts the autologon experience. If this policy needs to be set for users, select to hide these pages in the Windows Autopilot profile to prevent users from making changes. |
| **[AppLocker CSP](/en-us/windows/client-management/mdm/applocker-csp)** | The AppLocker configuration service provider (CSP) isn't supported in the Enrollment Status Page as it triggers a reboot when a policy is applied or a deletion occurs. |
| **Device restriction/[Password Policy](/en-us/windows/client-management/mdm/devicelock-csp)** | The out-of-box experience (OOBE) or user desktop autologon can fail when a device reboots during the device Enrollment Status Page (ESP). This failure can occur when certain [DeviceLock policies](/en-us/windows/client-management/mdm/policy-csp-devicelock) are applied to a device. Such policies can include:<br>- Minimum password length and password complexity<br>- Any similar group policy settings (including any that disable autologon)<br><br>This possible failure is especially true for kiosk scenarios where passwords are automatically generated. |
| **Windows Security Baseline/[Administrator elevation prompt behavior](/en-us/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)Windows Security Baseline/[Require admin approval mode for administrators](/en-us/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)Windows Security Baseline / [Enable virtualization based security](/en-us/windows/client-management/mdm/policy-csp-deviceguard)** | These policies require a reboot, as a result more prompts might appear when modifying user account control (UAC) settings during the OOBE using the device Enrollment Status Page (ESP). Increased prompts are more likely if the device reboots after policies are applied. To work around this issue, the policies can be targeted to users instead of devices so that they apply later in the process. |
| **Device restrictions/Cloud and Storage/[Microsoft Account sign-in assistant](/en-us/intune/device-configuration/templates/ref-device-restrictions-windows#cloud-and-storage)** | Setting this policy to "disabled" turns off the Microsoft Sign-in Assistant service (wlidsvc). Windows Autopilot requires this service to get the Windows Autopilot profile. |
| **Registry keys that affect Windows Autopilot if a device setting requires a reboot during device ESP** | **Registry key**:If the [AutoAdminLogon](/en-us/troubleshoot/windows-server/user-profiles-and-logon/turn-on-automatic-logon) registry key is set to `0` (disabled), this breaks Windows Autopilot.**Registry path**:`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Automatic logon` |
| **[MDM wins over Group Policy](/en-us/windows/client-management/mdm/policy-csp-controlpolicyconflict)** | This policy allows control of which policy is used when both the MDM policy and its equivalent Group Policy (GP) are set on the device. |
| **Group Policy Objects (GPOs) that affect Windows Autopilot for [pre-provisioned deployment](pre-provision)** | Windows Autopilot pre-provisioning doesn't work when any of the four GPO policy settings listed here are enabled.**GPO path**: Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options**Policies**:[Interactive logon: Message title for users attempting to log on](/en-us/windows/security/threat-protection/security-policy-settings/interactive-logon-message-title-for-users-attempting-to-log-on)[Interactive logon: Message text for users attempting to log on](/en-us/windows/security/threat-protection/security-policy-settings/interactive-logon-message-text-for-users-attempting-to-log-on)[Interactive logon: Require Windows Hello for Business or smart card](/en-us/windows/security/threat-protection/security-policy-settings/interactive-logon-require-smart-card)[User Account Control: Behavior of the elevation prompt for administrators in Admin Approval Mode - Prompt for credentials on the secure desktop](/en-us/windows/security/threat-protection/security-policy-settings/user-account-control-behavior-of-the-elevation-prompt-for-administrators-in-admin-approval-mode) |
| **[PreferredAadTenantDomainName](/en-us/windows/client-management/mdm/policy-csp-authentication#preferredaadtenantdomainname)** | When this policy is enabled, it adds the preferred domain to **DefaultUser0**, which causes autologon to fail. |

## Troubleshooting application install issues during Windows Autopilot

### Why is the error message "Another installation is in progress, please try again later" occurring during the ESP of a Windows Autopilot deployment?

The Enrollment Status Page (ESP) used by Windows Autopilot doesn't support mixing of line-of-business (LOB) and Win32 applications. Both LOB and Win32 applications use **TrustedInstaller** which doesn't allow simultaneous installations. If both an LOB and Win32 application attempt to install at the same time, the following error message occurs during ESP:

`Another installation is in progress, please try again later.`

For more information, see [Set up the Enrollment Status Page - Device setup: Apps](/en-us/intune/intune-service/enrollment/windows-enrollment-status#device-setup-apps).

If mixing LOB and Win32 apps is required, consider using [Windows Autopilot device preparation](device-preparation/overview), which doesn't use ESP so therefore supports mixing of LOB and Win32 apps.

### During the ESP of a Windows Autopilot deployment, why does the Microsoft 365 Click-to-Run version of Office fail to install the Teams Machine-Wide Installer, or cause other Win32 app MSI based installs to fail?

The [Teams Machine-Wide Installer](/en-us/microsoftteams/msi-deployment) component of the Microsoft 365 Click-to-Run version of Office includes an MSI installation. ESP doesn't track the Teams Machine-Wide Installer MSI install. Because ESP doesn't track the Teams Machine-Wide Installer MSI install, it can cause a conflict when other Win32 app MSI based installs attempt to install during ESP. MSIs install via **TrustedInstaller** which doesn't allow simultaneous installations. This conflict can cause either the Teams Machine-Wide Installer to fail or other MSI based installs to fail during ESP. For more information, see [Set up the Enrollment Status Page - Device setup: Apps](/en-us/intune/intune-service/enrollment/windows-enrollment-status#device-setup-apps).

This issue might be random and might not always occur. The issue occurs due to a timing issue between the **Teams Machine-Wide Installer** MSI install and other Win32 app MSI installs.

To work around the issue or avoid the error, use one of the following solutions:

1. Don't install **Teams** as part of the Microsoft 365 Click-to-Run install of Office. Instead, deploy **Teams** as a Win32 app after the Windows Autopilot deployment completes.
2. Don't install the Microsoft 365 Click-to-Run version of Office during ESP. Instead, deploy the Microsoft 365 Click-to-Run install of Office after the Windows Autopilot deployment completes.
3. Use a custom PowerShell script for Intune Management Extension (IME) that checks if **TrustedInstaller** is currently installing another MSI. If it is, then wait for the current MSI to finish installing before launching a new MSI install.
4. For Windows 11 deployments, use [Windows Autopilot device preparation](device-preparation/overview). Windows Autopilot device preparation doesn't use ESP so therefore supports mixing of LOB and Win32 apps.
5. Continue on error for ESP failures. If the problem occurs with this option enabled, some applications including **Teams** might not install. However, ESP continues and doesn't fail.

## Troubleshooting the Intune Connector for Active Directory

### Why is the Intune Connector for Active Directory not logging in Event Viewer even though logging is enabled?

The Intune Connector for Active Directory originally logged in the **Event Viewer** directly under **Applications and Services Logs** in a log called **ODJ Connector Service**. However, logging for the Intune Connector for Active Directory has since moved to the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. If the **ODJ Connector Service** log at the original location is empty or not updating, check the new path location instead.

### Why does uninstalling the Intune Connector for Active Directory through the Settings app not fully remove the application?

The Intune Connector for Active Directory needs to be uninstalled using both the Settings app and the Intune Connector for Active Directory installed executable **ODJConnectorBoostrapper.exe**. When uninstalling the Intune Connector for Active Directory, run **ODJConnectorBoostrapper.exe** and select the **Uninstall** option. The **ODJConnectorBoostrapper.exe** installer version needs to match the version of the connector that's being uninstalled.

### Why is the error "The MSA account couldn't be granted permission to create computer objects in the following OUs" occurring when installing the Intune Connector for Active Directory?

This error might occur for several different type of failures including:

- The administrator installing and configuring the Intune Connector for Active Directory doesn't have the required permissions as outlined in the [Intune Connector for Active Directory Requirements](windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).
- The organization unit (OU) specified in the Intune Connector for Active Directory `ODJConnectorEnrollmentWiazard.exe.config` XML configuration file doesn't exist.

For detailed information on the error and what caused it, see the `ODJConnectorUI.log` normally located in the following folder:

`C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard`

Follow the steps to [Increase the computer account limit in the Organizational Unit](tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit?tabs=updated-connector) if the following error appears in the `ODJConnectorUI.log`:

**`System.AggregateException: One or more errors occurred. ---> System.DirectoryServices.DirectoryServicesCOMException: A constraint violation occurred.`**

For more information, see [Install the Intune Connector for Active Directory on the server](windows-autopilot-hybrid?tabs=updated-connector#install-the-intune-connector-for-active-directory-on-the-server).

### Why is the error "Cannot start service ODJConnectorSvc on computer '.'" occurring when setting up the Intune Connector for Active Directory?

This error might occur for several reasons including:

- The domain has more than one domain controller with a replication latency policy. The MSA was created in one of the domain controllers but the search happened against another domain controller. Wait until replication has completed in accordance with your policy or manually sync. Once the replication is complete, then open the connector and choose **Configure MSA**.
- A group policy is configured that doesn't allow services to be started as a non-privileged account. Make sure the MSA account has **Log on as a service** privileges granted. For example, see this instance with Operations Manager to [Enable service logon](/en-us/system-center/scom/enable-service-logon#enable-service-log-on-permission-for-run-as-accounts).

### Why is the error "Microsoft Edge can't read and write to its data directory" occurring?

This error indicates that the user needs read/write permissions to the listed directory. For more information on how to grant these permissions, see [Manage user data folders](/en-us/microsoft-edge/webview2/concepts/user-data-folder?tabs=win32).

### Why did enrollments start failing when using the Intune Connector for Active Directory?

Make sure that the Intune Connector for Active Directory is updated to version **6.2501.2000.5** or later and that the legacy version isn't still being used. For more information, see [Intune Connector for Active Directory Requirements](windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).

### Why are the errors "Navigation to the webpage was canceled" or "Can't connect securely to this page" occurring while setting up theIntune Connector for Active Directory?

This error might occur for several different type of issues including:

- The server where the administrator is installing and configuring the Intune Connector for Active Directory doesn't have the required internet access or required Intune URLs aren't allowed. For more information, see the following articles:

    - [Windows Autopilot requirements - Windows Autopilot Deployment Service](requirements?tabs=networking#windows-autopilot-deployment-service).
    - [Intune core service](/en-us/intune/fundamentals/endpoints#endpoints).
    - [Windows Autopilot dependencies](/en-us/intune/fundamentals/endpoints#windows-autopilot-dependencies).
- Server is sending network request via TLS 1.0 or 1.1 because PKCS Cryptography is disabled. To resolve the issue, on the server hosting the Intune Connector for Active Directory, delete the registry key value specified in the following command by running the command from an elevated command prompt:

    `reg.exe delete "HKLM\System\CurrentControlSet\Control\SecurityProviders\SCHANNEL\KeyExchangeAlgorithms\PKCS" /v Enabled /f`

### Why are Windows Autopilot Hybrid deployments failing during ESP with error code "0x80070774"?

Error **0x80070774** might occur if there's a domain mismatch between where the Intune Connector for Active Directory is installed and where device configurations are targeted. For example, the Intune Connector for Active Directory is installed on one Active Directory domain but devices are configured for another. To resolve this issue, configure the Intune Connector for Active Directory in the matching domain.