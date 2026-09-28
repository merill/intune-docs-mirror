---
layout: Conceptual
title: Configure Defender for Endpoint web protection on Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-web-protection-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: laarrizz
ms.subservice: protect
description: Use Intune policy to manage Microsoft Defender for Endpoint web protection settings on Android devices managed by Microsoft Intune.
ms.date: 2026-05-22T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: a38a016f-39c5-d03c-410b-b724f7a13e8a
document_version_independent_id: a38a016f-39c5-d03c-410b-b724f7a13e8a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-defender/configure-web-protection-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-defender/configure-web-protection-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-defender/configure-web-protection-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
platformId: 22de7c90-4b46-0846-c897-508dca7fa9d1
---

# Configure Defender for Endpoint web protection on Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

When you integrate [Microsoft Defender for Endpoint](configure-integration) with Microsoft Intune, you can use device configuration profiles to modify some Defender for Endpoint settings on Android devices.

By default, Microsoft Defender for Endpoint for Android includes and enables the Microsoft Defender for Endpoint [Web protection](/en-us/defender-endpoint/web-protection-overview) feature that can help to secure devices against web threats and protect users from phishing attacks.

While enabled by default, there are valid reasons to disable it on some Android devices. For example, you might decide to use only the Defender for Endpoint app scan feature or to prevent web protection from using your VPN while it scans for harmful URLs.

With Intune device configuration policy, you can turn off all or part of the web protection feature. The method you use and the capabilities you can disable depend on how the Android device is enrolled with Intune:

- **Android Enterprise personally owned work profile**. Use an app configuration profile and the configuration designer to disable web protection. This method and enrollment type support disabling all web protection capabilities but don't support disabling only the use of VPNs. For general information about app configuration policies, see [Use the configuration designer](../../app-management/configuration/configure-managed-android#use-the-configuration-designer).
- **Android Enterprise fully managed**. Use an app configuration profile and the [configuration designer](../../app-management/configuration/configure-managed-android#use-the-configuration-designer) to disable the entire web protection feature or to disable only the use of VPNs.
- **Android device administrator** (deprecated). Use custom OMA-URI settings to disable web protection. For details, see Disable web protection for Android device administrator.

Web protection uses a local loopback VPN to intercept and evaluate web traffic. This VPN doesn't route traffic outside the device. The following browsers are known to work with the Defender loopback VPN:

- Chrome
- Microsoft Edge
- Firefox
- Opera
- Samsung Internet
- Brave
- DuckDuckGo

A smaller set of browsers (Chrome, Edge, Opera, Samsung Internet) also support web protection through the Android accessibility service when the loopback VPN isn't in use.

Note

This list might not be exhaustive. For the latest information about web protection capabilities on Android, see [Configure web protection](/en-us/defender-endpoint/android-configure#configure-web-protection) in the Defender for Endpoint documentation.

Important

Work profile scenarios (Android Enterprise personally owned devices using a work profile and Android Enterprise corporate owned work profile) do not support the accessibility service.

To configure web protection on devices, use the following procedures to create and deploy the applicable configuration.

## Disable web protection for the Android Enterprise personally owned work profile

Note

You can't disable web protection for the Android Enterprise personally owned work profile if you've configured the [Auto Setup of Always-on VPN](deploy-android#set-up-always-on-vpn) device configuration policy on the enrolled devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Managed apps** &gt; **Configuration** &gt; **Create**, and then select **Managed devices**.
3. In **Basics**, enter these details:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, **Android app configuration for Microsoft Defender for Endpoint web protection**.
    - **Description**: Enter a description for the profile. This setting is optional but recommended.
    - **Platform**: Select **Android Enterprise**.
    - **Profile Type**: Select **Personally-Owned Work Profile Only**.
    - **Targeted app**: Select **Select app**.
4. In **Associated app**, find and select **Defender for Endpoint**, and then select **OK** &gt; **Next**.
5. In **Settings**, in **Configuration settings format**, select **Use configuration designer**, and then select **Add**.
6. Find and select configuration keys **Anti-Phishing** and **VPN**, and then select **OK** to return to the **Settings** page.
7. For the **Configuration values** of both configuration keys (**Anti-Phishing** and **VPN**), enter **0** to disable web protection and enter **1** to enable web protection. By default, web protection is enabled.

    Note

    The values for **Anti-Phishing** and **VPN** must match. Set both to **0** to disable or both to **1** to enable. If the values don't match, both features are automatically disabled.

    Select **Next** to continue.
8. In **Assignments**, specify the groups that receive the profile. For more information on assigning profiles, see [Assign user and device profiles](../../device-configuration/assign-device-profile).
9. In **Review + create**, when you're done, select **Create**. The new profile is displayed in the list when you select the policy type for the profile you created.

## Disable web protection for Android Enterprise fully managed

1. Complete the same configuration steps described previously with the following difference: for **Profile Type**, select **Fully Managed, Dedicated, and Corporate-Owned Work Profile Only**.

    - To disable web protection, enter **0** for both **Anti-Phishing** and **VPN**. To enable web protection, enter **1** for both values. By default, web protection is enabled.
    - To disable only the use of VPN by web protection, enter these configuration values:

        - **0** for **VPN**
        - **1** for **Anti-Phishing**

    Note

    For the **corporate-owned work profile** enrollment scenario, the values for **VPN** and **Anti-Phishing** must match. Set both to **0** to disable or both to **1** to enable. If the values don't match, both features are automatically disabled.

    For the **corporate-owned fully managed** (no work profile) enrollment scenario, **VPN** and **Anti-Phishing** can be set independently. Each feature works on its own.

    Note

    You can't disable VPN for Android Enterprise fully managed devices if you've configured the Auto Setup of Always-on VPN device configuration policy on the enrolled devices.

    Select **Next** to continue.
2. In **Assignments**, specify the groups that receive the profile. For more information on assigning profiles, see [Assign user and device profiles](../../device-configuration/assign-device-profile).
3. In **Review + create**, when you're done, select **Create**. The new profile is displayed in the list when you select the policy type for the profile you created.

## Disable web protection for Android device administrator

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; On the *Policies* tab, select **+ Create**.
3. Enter these settings:

    - **Platform**: Select **Android device administrator**.
    - **Profile**: Select **Custom**.

    Select **Create**.
4. In **Basics**, enter these details:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, **Android custom profile for Defender for Endpoint web protection**.
    - **Description**: Enter a description for the profile. This setting is optional but recommended.
5. In **Configuration settings**, select **Add**.

    Specify settings for the configuration you want to deploy:

    - **Disable web protection**:

        - **Name**: Enter a unique name for this OMA-URI setting so you can find it easily. For example, **Disable Defender for Endpoint web protection**.
        - **Description**: (Optional) Enter a description that provides an overview of the setting and any other important details.
        - **OMA-URI**: Enter `./Vendor/MSFT/DefenderATP/AntiPhishing`
        - **Data type**: Select **Integer** in the drop-down list.
        - **Value**: To disable web protection, set *Value* to **0**. To enable web protection, enter **1**, which is the default.
    - **Disable only the use of VPN by web protection**:

        - **Name**: Enter a unique name for this OMA-URI setting so you can find it easily. For example, **Disable Microsoft Defender for Endpoint web protection VPN**.
        - **Description**: (Optional) Enter a description that provides an overview of the setting and any other important details.
        - **OMA-URI**: Enter `./Vendor/MSFT/DefenderATP/Vpn`
        - **Data type**: Select **Integer** in the drop-down list.
        - **Value**: To disable the VPN-based scan, set *Value* to **0**. To enable the VPN-based scan, enter **1**, which is the default.

    Select **Add** to save the OMA-URI settings configuration, and then select **Next** to continue.
6. In **Assignments**, specify the groups that receive the profile. For more information on assigning profiles, see [Assign user and device profiles](../../device-configuration/assign-device-profile).
7. In **Review + create**, when you're done, select **Create**. The new profile is displayed in the list when you select the policy type for the profile you created.