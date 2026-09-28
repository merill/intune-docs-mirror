---
layout: Conceptual
title: Troubleshoot Win32 Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/troubleshoot-win32
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
description: Learn about the most common methods to troubleshoot Win32 app issues with Microsoft Intune.
ms.date: 2025-10-02T00:00:00.0000000Z
ms.topic: troubleshooting
locale: en-us
document_id: 3002fbbf-2acd-7cc8-5bbf-d47cbbada396
document_version_independent_id: 3002fbbf-2acd-7cc8-5bbf-d47cbbada396
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/troubleshoot-win32.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/troubleshoot-win32
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/troubleshoot-win32.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 77f0b495-2d46-9671-9187-b9df609949de
---

# Troubleshoot Win32 Apps in Microsoft Intune - Microsoft Intune | Microsoft Learn

When you're troubleshooting Win32 apps used in Microsoft Intune, you can use a number of methods. This article provides troubleshooting details and information to help you solve Win32 app problems. For more information, see [Win32 app installation troubleshooting](/en-us/troubleshoot/mem/intune/troubleshoot-app-install#win32-app-installation-troubleshooting) resources.

Note

This app management capability supports 32-bit Windows, 64-bit Windows, and ARM64 operating system architectures for Windows applications.

Important

When you're deploying Win32 apps, consider using the [Intune Management Extension](../../device-management/tools/management-extension-windows) approach exclusively, particularly when you have a multiple-file Win32 app installer. If you mix the installation of Win32 apps and line-of-business (LOB) apps during Windows Autopilot enrollment, the app installation might fail. However, mixing of Win32 and line-of-business apps during Windows Autopilot device preparation is supported. The Intune management extension is installed automatically when a PowerShell script or Win32 app is assigned to the user or device.

For the scenario when a Win32 app is deployed and assigned based on user targeting, if the Win32 app requires device admin privileges or any other permissions that the standard user of the device does not have, the app will fail to install.

## App troubleshooting details

You can view installation issues, such as when the app was created, modified, targeted, and delivered to a device. The [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) provides these and other details on the **Troubleshoot + support** pane. For more information, see [App troubleshooting details](/en-us/troubleshoot/mem/intune/troubleshoot-app-install#app-troubleshooting-details).

## Troubleshooting app issues by using logs

Viewing the details of logs can help you determine the cause of the issues that you're seeing and help resolve them. You can choose to view the [logs displayed in Intune](troubleshoot-win32#logs-displayed-in-intune), or view the [logs displayed through CMTrace](troubleshoot-win32#logs-displayed-through-cmtrace).

### Logs displayed in Intune

When an installation issue occurs with a Win32 app, you can choose the **Collect logs** option in the **Installation details** pane for the app in Intune. For more details, see [Win32 app installation troubleshooting](/en-us/troubleshoot/mem/intune/troubleshoot-app-install#win32-app-installation-troubleshooting).

### Logs displayed through CMTrace

Agent logs on the client machine are commonly in *C:\ProgramData\Microsoft\IntuneManagementExtension\Logs*. You can use *CMTrace.exe* to view these log files. For more information, see [CMTrace](/en-us/configmgr/core/support/cmtrace).

![User's image](media/troubleshoot-win32/image.png)

| Log File | Description |
| --- | --- |
| IntuneManagementExtension.log | Main client log. Contains agent check in, policy request, policy processing and reporting activities |
| AgentExecutor.log | Tracks PowerShell script execution details |
| ClientHealth.log | Tracks SideCar agent client heath activities |
| \_IntuneManagementExtension.log | Saved copy of IntuneManagementExtension.log after log rolls over |
| AppActionProcessor.log | Tracks the Application Action Processor. This includes information about detection and applicability checks |
| AppWorkload.log | Main app workload log. This includes apps check-ins, app installs, app applicability and app detection logging |
| HealthScripts.log | Tracks Remediation script execution details. All workloads that leverage Remediation scripts would find logging for their features here, including custom compliance scripts, managed installer, hardware configuration, and on-demand proactive remediations. |

Important

To allow proper installation and execution of LOB Win32 apps, antimalware settings should exclude the following directories from being scanned:

**On x64 client machines**:*C:\Program Files (x86)\Microsoft Intune Management Extension\Content* *C:\windows\IMECache*

**On x86 client machines**:*C:\Program Files\Microsoft Intune Management Extension\Content* *C:\windows\IMECache*

For more information, see [Virus scanning recommendations for enterprise computers that are running currently supported versions of Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers).

## Detecting the Win32 app file version by using PowerShell

If you have difficulty detecting the Win32 app file version, consider using or modifying the following PowerShell command:

```PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}
```

In the preceding PowerShell command, replace the `<path to binary file>` string with the path to your Win32 app file. An example path would be similar to the following:

`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Also, replace the `<file version of successfully detected file>` string with the file version that you need to detect. An example file version string would be similar to the following:

`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

If you need to get the version information of your Win32 app, you can use the following PowerShell command:

```PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

In the preceding PowerShell command, replace `<path to binary file>` with your file path.

## Additional troubleshooting areas to consider

- Check targeting to make sure the agent is installed on the device. A Win32 app targeted to a group or a PowerShell Script targeted to a group will create an agent installation policy for a security group.
- Check the OS version: Use a [supported Windows version](../../fundamentals/ref-supported-platforms).
- Check the Windows SKU. Windows S, or Windows versions running with S-mode enabled, doesn't support MSI installation.

For more information about troubleshooting Win32 apps, see [Win32 app installation troubleshooting](/en-us/troubleshoot/mem/intune/troubleshoot-app-install#win32-app-installation-troubleshooting). For information about app types on ARM64 devices, see [App types supported on ARM64 devices](/en-us/troubleshoot/mem/intune/troubleshoot-app-install#app-types-supported-on-arm64-devices).