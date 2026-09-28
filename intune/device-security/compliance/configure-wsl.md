---
layout: Conceptual
title: Compliance for Windows Subsystem for Linux - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-wsl
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-device-compliance
ms.subservice: protect
description: Evaluate WSL attributes on a host device for compliance.
ms.date: 2024-11-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: arnab
locale: en-us
document_id: 1957bf91-b714-1ff1-8c6c-8762016e271d
document_version_independent_id: 1957bf91-b714-1ff1-8c6c-8762016e271d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/configure-wsl.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/configure-wsl
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/configure-wsl.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: 710dca32-cbe1-1a0d-7ff8-92b577e01a37
---

# Compliance for Windows Subsystem for Linux - Microsoft Intune | Microsoft Learn

Create a Microsoft Intune policy that checks the compliance of devices running Windows Subsystem for Linux (WSL). Microsoft Intune incorporates the WSL compliance results into the overall compliance state of the host device so you can see the whole health of the device.

This article applies to Windows and describes how to set up compliance checks for WSL.

## Requirements

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Windows

![](../../media/icons/16/plugin.svg)**Plugins requirements**

> 
> You must install the [Intune WSL plugin](https://go.microsoft.com/fwlink/?linkid=2296896) for compliance evaluation.

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the Microsoft Intune admin center with the following role:
> 
> - Built-in [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) Microsoft Entra role
> 

The Microsoft Intune management extension must be installed on the target device. Make sure devices meet one of the following conditions so that the management extension can install:

- Assign a PowerShell script or a proactive remediation to the user or device.
- Deploy a Win32 app or Microsoft Store app to the user or device.
- Assign a custom compliance policy to the user or device.

## Before you begin

Unassign and remove existing custom compliance policies for WSL. Then review the limitations with WSL settings in compliance policies so that you know what to expect.

## Add Intune WSL plugin as a Win32 app

Create a Win32 app policy for the [Intune WSL plugin](https://github.com/microsoft/shell-intune-samples/blame/master/Linux/WSL/IntuneWSLPluginInstaller/IntuneWSLPluginInstaller.msi), and assign it to the target Microsoft Entra group.

1. Use the [Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool) to convert the Intune WSL plugin to the *.intunewin* format. For more information, see [Convert the Win32 app content](../../app-management/deployment/create-win32-package#convert-the-win32-app-content).
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Go to **Apps** &gt; **All Apps** &gt; **Add**.
4. For **App type**, scroll down to **Other**, and then select **Windows app (Win32)**.
5. Choose **Select**. The **Add app** steps appear.
6. Choose **Select app package file**.
7. Select the **Folder** button and browse your files for the app package file. Upload the Intune WSL plugin installation file with the *.intunewin* extension.
8. Select **OK** to continue.
9. Enter the following app information:

    - **Select file**: The app package file you selected in the previous step appears here. Select the file to upload a different installation package file for the Intune WSL plugin.
    - **Name**: Enter **Intune WSL Plugin**.
    - **Description**: Select **Edit Description** to enter a description for the app. For example, you can describe its purpose or how your organization plans to use it. This setting is optional but recommended.
    - **Publisher**: Enter **Microsoft Intune**.
10. Select **Next** to go to **Program**.
11. Review the settings that are prepopulated so that you're familiar with how the app behaves. Leave the settings as-is.
12. Select **Next** to go to **Requirements**.
13. Enter the requirements devices must meet to install the app.
14. Select **Next** to go to **Detection rules**.
15. Review the detection rules that are prepopulated. These rules are app-specific and detect the presence of the app. Leave the settings as-is.
16. Select **Next** to go to **Dependencies**. Leave the settings as-is.
17. Select **Next** to go to **Supersedence**. Leave the settings as-is.
18. Select **Next** to go to **Assignments**.
19. To assign the policy, add Microsoft Entra users under **Required**.
20. Select **Next** to go to **Review + create**.
21. Review the summary, and then select **Create** to save the policy.

Note

When you create a compliance policy with WSL settings, it automatically generates a read-only custom script. Editing the compliance policy also edits the associated custom script. These scripts appear in the Microsoft Intune admin center in **Devices** &gt; **Compliance** &gt; **Scripts** and are called *Built-in WSL Compliance-&lt; compliance policy id &gt;*.

## Limitations

This section describes the known limitations when using the Intune WSL plugin for compliance evaluation.

- Compliance evaluation requires the installed Linux distributions in WSL to run at least once before it works. If you install a Linux distribution by using the `--no-launch`[command for WSL](/en-us/windows/wsl/basic-commands), the compliance evaluation doesn't work.
- Compliance evaluation might not function as expected on custom Linux images or Linux images without the `etc/os-release` directory.
- Even with the Intune WSL plugin, malicious software or user actions can compromise the compliance evaluation mechanism.