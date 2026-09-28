---
layout: Conceptual
title: How to create Wi-Fi profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-wifi-profiles
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn how to use Wi-Fi profiles in Configuration Manager to deploy wireless network settings to users in your organization.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: faf92c87-3b14-bf6d-f3a1-20b241fe12b7
document_version_independent_id: 1a20cd03-f226-b012-43ba-8e747d4731a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/create-wifi-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/create-wifi-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/create-wifi-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: fedf11d4-47cf-0576-4a46-780418a27d0d
---

# How to create Wi-Fi profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

Use Wi-Fi profiles in Configuration Manager to deploy wireless network settings to users in your organization. By deploying these settings, you make it easier for your users to connect to Wi-Fi.

For example, you have a Wi-Fi network that you want to enable all Windows laptops to connect to. Create a Wi-Fi profile containing the settings necessary to connect to the wireless network. Then, deploy the profile to all users that have Windows laptops in your hierarchy. Users of these devices see your network in the list of wireless networks and can readily connect to this network.

You can configure Wi-Fi profiles for the following OS versions:

- Windows 8.1 32-bit or 64-bit
- Windows RT 8.1
- Windows 10 or Windows 10 Mobile

You can also use Configuration Manager to deploy wireless network settings to mobile devices using on-premises mobile device management (MDM). For more general information, see [What is on-premises MDM](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure).

When you create a Wi-Fi profile, you can include a wide range of security settings. These settings include certificates for server validation and client authentication that have been pushed using Configuration Manager certificate profiles. For more information about certificate profiles, see [Certificate profiles](introduction-to-certificate-profiles).

## Create a Wi-Fi profile

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, expand **Company Resource Access**, and select the **Wi-Fi Profiles** node.
2. On the **Home** tab, in the **Create** group, choose **Create Wi-Fi Profile**.
3. On the **General** page of the Create Wi-Fi Profile Wizard, specify the following information:

    - **Name**: Enter a unique name to identify the profile in the console.
    - **Description**: Optionally add a description to provide further information for the Wi-Fi profile.
    - **Import an existing Wi-Fi profile item from a file**: Select this option to use the settings from another Wi-Fi profile. When you select this option, the remaining pages of the wizard simplify to two pages: **Import Wi-Fi Profile** and **Supported Platforms**.

        Important

        Make sure that the Wi-Fi profile you import contains valid XML for a Wi-Fi profile. When you import the file, Configuration Manager doesn't validate the profile.
    - **Noncompliance severity for reports**: Choose one of the following severity levels that the device reports if it evaluates the Wi-Fi profile to be noncompliant. For example, if the installation of the profile fails, it's noncompliant.

        - **None**: Computers that fail this compliance rule don't report a failure severity for Configuration Manager reports.
        - **Information**
        - **Warning**
        - **Critical**
        - **Critical with event**: Computers that fail this compliance rule report a failure severity of **Critical** for Configuration Manager reports. Devices also log the noncompliant state as a Windows event in the application event log.
4. On the **Wi-Fi Profile** page of the wizard, specify the following information:

    - **Network name**: Provide the name that devices will display as the network name.

        Important

        Configuration Manager doesn't support using the apostrophe (`'`) or comma (`,`) characters in the network name.
    - **SSID**: Specify the case-sensitive ID of the wireless network.
    - **Connect automatically when this network is in range**
    - **Look for other wireless network while connected to this network**
    - **Connect when the network is not broadcasting its name (SSID)**
5. On the **Security Configuration** page, specify the following information:

    Important

    If you're creating a Wi-Fi profile for [on-premises MDM](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure), the current branch of Configuration Manager only supports the following Wi-Fi security configurations:

    - Security types: **WPA2 Enterprise** or **WPA2 Personal**
    - Encryption types: **AES** or **TKIP**
    - EAP types: **Smart Card or other certificate** or **PEAP**

    - **Security type**: Select the security protocol that the wireless network uses, or select **No authentication (Open)** if the network is unsecured.
    - **Encryption**: If the security type supports it, set the encryption method for the wireless network.
    - **EAP type**: Select the authentication protocol for the selected encryption method.

        Note

        For Windows Phone devices only: the EAP types **LEAP** and **EAP-FAST** aren't supported.

        Select **Configure** to specify properties for the selected EAP type. This option isn't available for some selected EAP types.

        Important

        The EAP type configuration window is from Windows. Make sure that you run the Configuration Manager console on a computer that supports the selected EAP type.
    - **Remember the user credentials at each logon**: Select this option to store user credentials so users don't have to enter wireless network credentials each time they sign in to Windows.
6. On the **Advanced Settings** page of the wizard, specify additional settings for the Wi-Fi profile. Advanced settings might not be available, or might vary, depending on the options that you select on the **Security Configuration** page of the wizard. For example, authentication mode, or single sign-on options.
7. On the **Proxy Settings** page, if your wireless network uses a proxy server, select the option to **Configure proxy settings for this Wi-Fi profile**. Then provide the configuration information for the proxy.
8. On the **Supported Platforms** page, select the OS versions where this Wi-Fi profile is applicable.
9. Complete the wizard.