---
layout: Conceptual
title: Understand Microsoft Intune Management Extension - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/tools/management-extension-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- Windows
- FocusArea_Apps_Win32
ms.subservice: apps
description: Understand Microsoft Intune management extension for Windows.
ms.date: 2026-09-24T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: bryanke
locale: en-us
document_id: 3a8259eb-b8f1-1e3d-4468-9b398e41f55f
document_version_independent_id: 3a8259eb-b8f1-1e3d-4468-9b398e41f55f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/tools/management-extension-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/tools/management-extension-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/tools/management-extension-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/5cf46315-b33f-4e99-8224-a1592697eff9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/715d24c3-3683-4219-82c5-1e3c813fb7fc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 58fe8f12-f34f-ad60-3058-dd0496462555
---

# Understand Microsoft Intune Management Extension - Microsoft Intune | Microsoft Learn

The Intune Management Extension (IME) is an installer agent that enhances Windows device management (MDM). It supplements the standard Windows MDM feature by enabling advanced device management capabilities.

Note

For details about PowerShell scripts, see [Use PowerShell scripts on Windows devices in Intune](run-powershell-scripts-windows).

This feature applies to:

- [Supported Windows versions](../../fundamentals/ref-supported-platforms) (excluding Windows Home and Windows devices running in S mode).

Note

After the Intune management extension prerequisites are met, the extension installs automatically when you assign any of the following to the user or device:

- A PowerShell script
- A Win32 app
- A Microsoft Store app
- A custom compliance policy setting
- A proactive remediation

For more information, see Intune Management Extension [prerequisites](management-extension-windows#prerequisites).

## Prerequisites

Important

Devices must run Intune Management Extension version **1.58.103.0** or later. Devices on earlier versions don't receive configurations or updates that depend on the Intune Management Extension, including Win32 app deployments, PowerShell scripts, remediations, and platform scripts. The Intune Management Extension updates automatically, so most managed devices should already have a compatible version. Verify that your devices can sync with Intune to receive updates.

The Intune management extension has the following prerequisites. When the prerequisites are met, the Intune management extension installs automatically when a PowerShell script or Win32 app is assigned to the user or device.

- Devices running a [supported Windows version](../../fundamentals/ref-supported-platforms). The Intune management extension doesn't support Windows in S mode because S mode doesn't allow running nonstore apps.
- Devices joined to Microsoft Entra ID, including:

    - Microsoft Entra hybrid joined: Devices joined to Microsoft Entra ID and on-premises Active Directory (AD). See [Plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan) for guidance.
    - Microsoft Entra registered/Workplace joined (WPJ): Devices [registered](/en-us/azure/active-directory/user-help/user-help-register-device-on-network) in Microsoft Entra ID. For more information, see [Workplace Join as a seamless second factor authentication](/en-us/windows-server/identity/ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications#BKMK_DRS). These are Bring Your Own Device (BYOD) devices with a work or school account added via **Settings** &gt; **Accounts** &gt; **Access work or school**.
- Devices enrolled in Intune, including:

    - Devices enrolled using group policy (GPO). For more information, see [Enroll a Windows device automatically using Group Policy](/en-us/windows/client-management/enroll-a-windows-10-device-automatically-using-group-policy).
    - Devices manually enrolled in Intune, which occurs when:

        - [Automatic enrollment to Intune](../../device-enrollment/windows/quickstart-automatic-mdm) is enabled in Microsoft Entra ID. Users sign in to devices using a local user account and manually join the device to Microsoft Entra ID. Then, they sign in to the device using their Microsoft Entra account.

        OR

        - Users sign in to the device using their Microsoft Entra account and then enroll in Intune.
    - Co-managed devices using Configuration Manager and Intune. When installing Win32 apps, set the **Apps** workload to **Pilot Intune** or **Intune**. PowerShell scripts run even if the **Apps** workload is set to **Configuration Manager**. The Intune management extension deploys to a device when you target a PowerShell script to the device. The device must be Microsoft Entra ID or Microsoft Entra hybrid joined and running a [supported Windows version](../../fundamentals/ref-supported-platforms). See the following articles for guidance:

        - [What is co-management](/en-us/configmgr/comanage/overview)
        - [Client apps workload](/en-us/configmgr/comanage/workloads#client-apps)
        - [How to switch Configuration Manager workloads to Intune](/en-us/configmgr/comanage/how-to-switch-workloads)
- For devices behind firewalls and proxy servers, enable communication for Intune. For more information, see [Network requirements for PowerShell scripts and Win32 apps](../../fundamentals/endpoints).

Note

For details about using Windows virtual machines, see [Using Windows virtual machines with Microsoft Intune](../../solutions/windows-virtual-machines).

## Understand Intune management extension agent installation

For devices meeting the prerequisites, the Intune management extension installs automatically when certain features are assigned to a user or device. Installation occurs when the following features are assigned:

- [PowerShell scripts](run-powershell-scripts-windows)
- [Remediations](deploy-remediations)
- [Discovery scripts for custom compliance](../../device-security/compliance/create-custom-script)
- [Win32 apps](../../app-management/deployment/add-win32)
- [Endpoint analytics](../../endpoint-analytics/)
- [Remote Help](../../remote-help/)
- [Managed Installers in Intune](../../device-configuration/endpoint-security/manage-app-control)
- [Update Windows BIOS using configuration MDM policy](../../device-configuration/templates/configure-bios-windows)

Note

For details about how the IME is rolled out and updated, see [Service information for Microsoft Intune release updates](../../fundamentals/servicing-information).

The agent installs at `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs` when applicable and doesn't appear in the start menu on Windows devices. The agent appears as **IntuneManagementExtension** under **Services** in **Task Manager** when running on Windows devices.

### Intune management extension functionality

- The IME silently authenticates with Intune services before checking in to receive assigned installations for the Windows device.
- The IME checks for new or updated installations with Intune services every 8 hours. This check-in process is independent of the MDM check-in.
- After the Windows [enrollment status page (ESP)](../../device-enrollment/windows/setup-status-page) or [Windows Autopilot device preparation](/en-us/autopilot/device-preparation/overview) finishes, the IME immediately checks for new Windows app assignments. This behavior reduces the delay before required Win32 apps that weren't installed during provisioning begin to install.
- The IME might periodically perform health checks to validate connectivity to Intune services.

### Manually initiate an Intune management IME check-in from a Windows device

On a Windows device with the IME installed, open **Company Portal**, select **Settings** &gt; **Sync**. This initiates an MDM check-in and an IME check-in.

Alternatively, open **Task Manager**, find the service **IntuneManagementExtension**, right-click, and select **Restart**. The `IntuneManagementExtension` service restarts immediately, initiating a check-in with Intune.

Note

The **Sync** actions from either the **Settings** app or **Devices** in Microsoft Intune admin center initiate an MDM check-in as well as an IME check-in. After selecting Sync, Intune initiates an on-demand synchronization across multiple workloads to help ensure the device reflects the latest admin intent as quickly as possible. This process includes, but isn't limited to:

- Configuration policy processing
- App detection and deployment state updates
- Script and remediation processing
- Other device management signals required to align device state with current assignments

You can track the progress of the sync action by selecting the **Device sync status** tab in the device overview pane.

### Intune management extension removal

The IME is removed from the device under the following conditions:

- PowerShell scripts are no longer assigned to the device.
- The Windows device is no longer managed.
- The IME is in an irrecoverable state for over 24 hours (device-awake time).

## Common issues and resolutions

### Issue: Intune management extension doesn't download

**Possible resolutions**:

- The device isn't joined to Microsoft Entra ID. Make sure the devices meet the prerequisites in this article.
- No PowerShell scripts or Win32 apps are assigned to the groups the user or device belongs to.
- The device can't check in with the Intune service. For example, there's no internet access or no access to Windows Push Notification Services (WNS).
- The device is in S mode. The Intune management extension doesn't support devices running in S mode.
- Ensure the configuration file located at `C:\Program Files (x86)\Microsoft Intune Management Extension\Microsoft.Management.Services.IntuneWindowsAgent.exe.config` has not been corrupted or manually altered.
- Confirm whether the app was installed using a method outside of Intune’s automatic installation (e.g., script, manual install, or repackaging). The only supported mechanism is automatic installation as devices sync with the Intune service.
- On Windows devices, if the proxy is configured only at the user level (and not machine-wide), make sure a user is signed in to the device. Alternatively, use `bitsadmin /util /setieproxy` to manually configure the proxy for the BITS (Background Intelligent Transfer Service). For more information, see [bitsadmin util and setieproxy](/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-setieproxy).

To check if the device is automatically enrolled:

1. Go to **Settings** &gt; **Accounts** &gt; **Access work or school**.
2. Select the joined account &gt; **Info**.
3. Under **Advanced Diagnostic Report**, select **Create Report**.
4. Open the `MDMDiagReport` in a web browser.
5. Search for the **MDMDeviceWithAAD** property. If the property exists, the device is automatically enrolled. If this property doesn't exist, the device isn't automatically enrolled.

[Enable Windows automatic enrollment](../../device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment) includes the steps to configure automatic enrollment in Intune.

### Issue: Microsoft Intune Windows Agent app gets automatically disabled

Microsoft Intune Windows Agent is a Microsoft Entra ID app. The IME agent uses the Microsoft Intune Windows Agent app to authenticate against the gateway to get other apps, scripts, and other critical payloads. This application isn't linked to any subscription-based lifecycle flow.

Under some conditions, the Microsoft Intune Windows Agent app can fail subscription validity checks and get continuously disabled, even when the admin re-enables the app. When disabled, the IME agent can't retrieve tokens against the Microsoft Intune Windows Agent application and user targetted payloads stop working.

**Possible resolution**:

Delete the service principal from your organization tenant using Microsoft Graph API, preferably through Graph Explorer:

1. Sign in to [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) using an organization admin account that can delete service principals, like the **[Application Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)** role. Make sure the top-right corner shows your tenant name, not "sample tenant".

    For a list of Microsoft Entra built-in roles, and what they can do, see [Microsoft Entra built-in roles](/en-us/entra/identity/role-based-access-control/permissions-reference).
2. Select **API Explorer** &gt; `servicePrincipals` &gt; `{servicePrincipal-id}` &gt; `DELETE`.
3. In the Graph URL syntax, replace `{servicePrincipal-id}` with the ID of the service principal.
4. Select **Run Query** to execute the deletion.

Note

These steps should be completed by someone who is familiar with Graph Explorer. To learn more about Graph Explorer, see [Use Graph Explorer to try Microsoft Graph APIs](/en-us/graph/graph-explorer/graph-explorer-overview).

## Intune management extension logs

IME logs on the client machine are typically in `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Use [CMTrace.exe](/en-us/configmgr/core/support/cmtrace) to view these log files.

![Screenshot showing Intune Management Extension log files in CMTrace.](media/management-extension-windows/image.png)

Also, use the log file *AppWorkload.log* to troubleshoot and analyze Win32 app management events on the client. This log file contains all logging information related to app deployment activities conducted by the IME.

### IME log files

| Log file | Description |
| --- | --- |
| IntuneManagementExtension.log | The main log file. It contains all the IME check-ins, policy requests, policy processing, and reporting activities. |
| AgentExecutor.log | Tracks PowerShell script executions (deployed by Intune). |
| AppActionProcessor.log | Tracks detection and applicability check actions for assigned apps. |
| AppWorkload.log | Helps troubleshoot and analyze Win32 app deployment activities. |
| ClientCertCheck.log | Tracks device client certificate checks. |
| ClientHealth.log | Tracks the health of the Intune management extension. |
| DeviceHealthMonitoring.log | Tracks the health of hardware readiness, device inventory, and other data collectors. |
| HealthScripts.log | Tracks the health of remediations that run on a regular schedule. |
| NotificationInfra.log | Tracks notifications sent through the Microsoft real-time communication channel. |
| Sensor.log | Tracks the health of the Endpoint analytics data collector, including boot performance, app reliability, and more. |
| Win32AppInventory.log | Tracks the health of the app inventory collector. |