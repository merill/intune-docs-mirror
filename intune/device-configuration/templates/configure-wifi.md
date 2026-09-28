---
layout: Conceptual
title: Create a Wi-Fi profile for devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi
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
description: See the steps to create a Wi-Fi device configuration profile in Microsoft Intune. Create profiles for Android device administrator, Android Enterprise, Android kiosk, iOS, iPadOS, macOS, Windows 10/11, and Windows Holographic for Business. Use these profiles to create a WiFi connection to use certificates, choose an EAP type, select an authentication method, enable a proxy, and more.
ms.date: 2024-07-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abalwan
locale: en-us
document_id: 61fbaf9a-2e42-75dd-f47e-b02d8de82e8e
document_version_independent_id: 61fbaf9a-2e42-75dd-f47e-b02d8de82e8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-wifi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-wifi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-wifi.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e88970a9-94c5-7e25-92bb-16a0464139bb
---

# Create a Wi-Fi profile for devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Wi-Fi is a wireless network that's used by many mobile devices to get network access. Microsoft Intune includes built-in Wi-Fi settings that can be deployed to users and devices in your organization. This group of settings is called a **profile**, and can be assigned to different users and groups. Once assigned, your users get access your organization's Wi-Fi network without configuring it themselves.

For example, you install a new Wi-Fi network named Contoso Wi-Fi. You then want to set up all iOS/iPadOS devices to connect to this network. Here's the process:

1. You create a Wi-Fi profile that includes the settings that connect to the Contoso Wi-Fi wireless network.
2. You assign the profile to a group that includes all users of iOS/iPadOS devices.
3. Users find the new Contoso Wi-Fi network in the list of wireless networks on their devices. They can then connect to the network, using the authentication method of your choosing.

This article lists the steps to create a Wi-Fi profile. It also includes links that describe the different settings for each platform.

## Before you begin

- To create a Wi-Fi profile, you need to know the settings for your Wi-Fi network, including the SSID (service set identifier), security type, and more.
- To configure the Wi-Fi policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).
- Wi-Fi profiles support the following device platforms:

    - Android device administrator
    - Android Enterprise and kiosk
    - Android (AOSP)
    - iOS/iPadOS
    - macOS
    - Windows
    - Windows Holographic for Business

    For specific versions, go to [Supported operating systems and browsers in Intune](../../fundamentals/ref-supported-platforms).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select the platform of your devices. Your options:

        - **Android device administrator**
        - **Android (AOSP)**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows 10 and later**
        - **Windows 8.1 and later**
    - **Profile type**: Select **Wi-Fi**. Or, select **Templates** &gt; **Wi-Fi**.

        Tip

        - For **Android Enterprise** devices running as a dedicated device (kiosk), select **Fully Managed, Dedicated, and Corporate-Owned Work Profile** &gt; **Wi-Fi**.
        - For **Windows 8.1 and newer**, you can choose **Wi-Fi import**. This option lets you import Wi-Fi settings as an XML file that you previously exported from a different device.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **WiFi profile for entire company**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Select your platform for detailed settings:

    - [Android](ref-wifi-settings-android-enterprise), including dedicated devices
    - [iOS/iPadOS](ref-wifi-settings-apple)
    - [macOS](ref-wifi-settings-apple)
    - [Windows](ref-wifi-settings-windows)
    - [Windows 8.1 and newer](import-wifi-settings-windows), including Windows Holographic for Business
    - [Android device administrator](ref-wifi-settings-android)
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

Tip

If you use certificate based authentication for your Wi-Fi profile, deploy the Wi-Fi profile, certificate profile, and trusted root profile to the same groups. This step makes sure that each device can recognize the legitimacy of your certificate authority. For more information, go to [How to configure certificates with Microsoft Intune](../../fundamentals/certificates/overview).