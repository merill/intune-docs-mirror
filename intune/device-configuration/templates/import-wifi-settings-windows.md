---
layout: Conceptual
title: Import Wi-Fi settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/import-wifi-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Export Wi-Fi settings from a Windows device as an XML file using the network shell (netsh wlan) command. Then, import this file in Intune to create a Wi-Fi profile for devices running Windows 10/11 and Windows Holographic for Business.
ms.date: 2024-07-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abalwan
locale: en-us
document_id: 17603de3-e89e-5bdb-3381-2640ec432656
document_version_independent_id: 17603de3-e89e-5bdb-3381-2640ec432656
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/import-wifi-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/import-wifi-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/import-wifi-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 564e2e59-9025-6d0a-f765-f50e9620251c
---

# Import Wi-Fi settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

On Windows devices, you can export Wi-Fi settings to an XML file, and then import these settings in Intune. Using these imported settings, you can create a Wi-Fi profile, and then deploy it to your devices.

This feature applies to:

- Windows
- Windows Holographic for Business

This article shows you how to export Wi-Fi settings from a Windows device, and then import these settings in to Intune.

Note

- On Windows, you can [create a Wi-Fi profile](ref-wifi-settings-windows) directly in Intune. You don't have to import a file.
- For Windows 8.1 devices, you must export and import Wi-Fi settings to create and deploy Wi-Fi profiles.

## Before you begin

- To configure the Intune policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Export Wi-Fi settings from a Windows device

To export an existing Wi-Fi profile to an XML file readable by Intune, use `netsh wlan`. On a Windows computer that has the WiFi profile, use the following steps:

1. Create a local folder for the exported Wi-Fi profiles, such as **c:\WiFi**.
2. Open a command prompt as an administrator.
3. Run the `netsh wlan show profiles` command. Note the name of the profile you want to export.
4. Run the `netsh wlan export profile name="ContosoWiFi" folder=c:\Wifi` command. This command creates a Wi-Fi profile file named **Wi-Fi-ContosoWiFi.xml** in your target folder.

### Preshared keys and exporting

If you're exporting a Wi-Fi profile that includes a preshared key (PSK), you **must** add `key=clear` to the command. The key must be exported in plain text to successfully use the profile.

For example, enter:

```cmd
netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi
```

- Using a preshared key with Windows causes a remediation error to show in Intune. When the error happens, the Wi-Fi profile is properly assigned to the device, and the profile works as expected.
- If you export a Wi-Fi profile that includes a preshared key, be sure the file is protected. The key is in plain text. It's your responsibility to protect the key.

## Import the Wi-Fi settings into Intune

When the XML file is ready, you can import it into Intune to create a Wi-Fi profile.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 8.1 and later**.

        Even though you select Windows 8.1, this feature still applies to other Windows versions.
    - **Profile type**: Select **Wi-Fi import**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: This setting is the profile name. You must enter the same name as the `name` attribute in the Wi-Fi profile xml. If you enter a different name, the profile fails.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended. For example, enter `Imported Wi-Fi profile for Windows Holographic devices`.
6. Select **Next**.
7. In **Configuration settings**, enter the following properties:

    - **Connection name**: Enter a name for the Wi-Fi connection. This name is shown to users when they browse available Wi-Fi networks. For example, enter `ContosoWiFi`.
    - **Profile XML**: Select the browse button, and select the XML file that contains the Wi-Fi profile settings you want to import.
    - **File contents**: Shows the XML code for the XML file you selected.
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.