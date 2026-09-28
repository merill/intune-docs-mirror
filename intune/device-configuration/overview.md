---
layout: Conceptual
title: Device features and settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/overview
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
description: Overview of the different Microsoft Intune device profiles. Get info on GPO, features, restrictions, email, wifi, VPN, education, certificates, upgrade Windows 10/11, BitLocker and Microsoft Defender, and custom device configuration settings in the Microsoft Intune admin center. Use these profiles to manage and protect data and devices in your company.
ms.date: 2026-09-14T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: mikedano
locale: en-us
document_id: ecb200ed-5b1e-98a7-6995-6bae8a81d9bc
document_version_independent_id: ecb200ed-5b1e-98a7-6995-6bae8a81d9bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 077e06bb-75cf-bd19-5c17-bd40789497da
---

# Device features and settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune includes settings and features you can enable or disable on different devices within your organization. These settings and features are added to **configuration profiles**.

When you configure device features using configuration profile, you can help your end users be productive on their devices faster.

You can create profiles for different devices and different platforms, including Android, iOS/iPadOS, macOS, and Windows. There are some configuration settings that are unique to each platform. It's also common to have many device profiles for each platform, ranging from antivirus settings to custom settings.

When the profiles are ready, you use Intune to apply or "assign" the profile to user groups or device groups.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

As part of your mobile device management (MDM) solution, use these configuration profiles to complete different tasks. Some profile examples include:

- Allow or prevent access to bluetooth on the device.
- Create a WiFi or VPN profile that gives different devices access to your corporate network.
- Manage software updates, including when they're installed.
- Run an Android device as dedicated kiosk device that can run one app, or run many apps.
- On iOS/iPadOS and macOS devices, allow users to use AirPrint printers in your organization.

Tip

If you manage on-premises devices using Microsoft Configuration Manager, then you can use co-management to cloud attach your on-premises devices. With co-management, you manage Windows client devices with Configuration Manager and Microsoft Intune.

You can create the device profiles and policies you need in Intune based on policies you currently have in Configuration Manager. For more information about co-management, go [Understand co-management using Microsoft Configuration Manager](../configmgr/comanage/overview). For related information, see [Prepare Intune for co-management](/en-us/configmgr/core/get-started/capabilities-in-technical-preview-1709#prepare-intune-for-co-management).

## Use templates or the settings catalog

In Intune, for most platforms, when you create a device configuration profile, you have two policy types: **Templates** or the **[Settings Catalog](settings-catalog/)**.

The settings catalog lists all the settings you can configure, and all in one place. Templates include a logical grouping of settings that configure a feature or concept, like email, kiosk devices, and device firmware.

Intune has many templates that include groups of settings that focus on different parts of device management, including accessing resources (VPN, Wi-Fi), security (antivirus, firewall, certificates).

You can create a baseline of profiles that all devices must have, or you can configure specific features based on your organization needs and levels of security. For more information, go to [Levels of protection and configuration in Microsoft Intune](../fundamentals/protection-configuration-levels).

This article gives an overview of the different types of profiles you can create. Use these profiles to allow or prevent some features on the devices.

## Handle custom and imported device profile settings

Some device profile settings can include credentials, passwords, pre-shared keys (PSKs), or other sensitive organizational information as configuration values.

The following profile types include properties that can store custom configuration data:

| Device configuration profile type | Microsoft Graph entity | Property | Sensitive data at risk (examples) |
| --- | --- | --- | --- |
| Windows 8.1 and later Wi-Fi import profile | `windows81WifiImportConfiguration` | `payload` | `wlan_psk` |
| Windows 10 and later VPN profile | `windows10VpnConfiguration` | `customXml`, `eapXml` | `eap_password` |
| iOS/iPadOS custom profile | `iosCustomConfiguration` | `payload` | `ios_password`, `ios_psk` |
| macOS custom profile | `macOSCustomConfiguration` | `payload` | `macos_imap`, `macos_smtp` |
| macOS preference file | `macOSCustomAppConfiguration` | `configurationXml` | `password` |

Important

Users and applications with permission to read device configuration profiles can retrieve values stored in custom configuration properties. TLS protects the data during transmission, but it doesn't prevent authorized users or applications from accessing these values. Encoding, such as Base64, also doesn't protect sensitive data because the values can be decoded to reveal the original content.

### Access to profile values

Administrators and applications with read access to Intune device configuration profiles can retrieve values stored in affected properties through Microsoft Graph. This access includes:

- Administrators assigned permissions such as `DeviceManagementConfiguration.Read.All`
- Applications (Microsoft Entra applications or service principals) granted read permissions to Intune device configurations
- Users assigned built-in roles such as **Intune Read Only Operator**

These users and applications can retrieve profile data by using Microsoft Graph endpoints such as:

```http
GET /beta/deviceManagement/deviceConfigurations/{id}
```

### Best practices

- Don't store passwords, pre-shared keys, shared secrets, or other sensitive credentials in custom configuration profile properties unless no alternative exists.
- If storing sensitive credentials is unavoidable, require explicit risk acceptance and restrict read access to only the authorized users and applications that need it.
- Assume that any value entered into affected properties is accessible to any administrator or application with permission to read device configuration profiles.
- Review and restrict access so that only authorized users and applications can read Intune device configuration data.
- Regularly review and audit access to Intune configuration data, including both user role assignments and application permissions, to ensure only authorized users and applications can access device configuration profiles.
- Consider alternative authentication methods that don't require embedding secrets directly in configuration profiles.

## Certificates

You use [certificates in Intune](../fundamentals/certificates/overview) to authenticate your users so they can access applications and corporate resources through VPN, Wi-Fi, or email profiles. When you use certificates to authenticate these connections, your end users don't need to enter usernames and passwords.

Certificates are also used for signing and encrypting email using S/MIME. Common types of certificates used in Intune include trusted root certificates, Simple Certificate Enrollment Protocol (SCEP) certificates, and Public Key Cryptography Standards (PKCS) certificates.

This feature supports:

- Android device administrator
- Android (AOSP)
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows

## Custom profile

[Custom settings](templates/configure-custom-settings) let administrators assign device settings that aren't built in to Intune. On Android devices, you can enter OMA-URI values. For iOS/iPadOS devices, you can import a configuration file you created in the Apple Configurator.

This feature supports:

- Android device administrator
- iOS/iPadOS
- macOS
- Windows

## Delivery optimization

[Delivery optimization](templates/configure-delivery-optimization-windows) provides a better experience to delivery software updates.

Use these settings to control how software updates are downloaded to devices in your organization. For example, you can let users get their own updates, or get updates using the delivery optimization cloud services in a device profile.

This feature supports:

- Windows

## Derived credential

If your organization uses smart cards for authentication, signing, or encryption, then you can use [derived credentials](../device-security/certificates/derived-credentials). In Intune, you can configure and deploy a certificate that's derived from a user's smart card. Derived credentials are commonly used for Wi-Fi & VPN connections, app & email authentication, or S/MIME signing & encryption.

Intune [supports several derived credential issuers](../device-security/certificates/derived-credentials#supported-issuers). Each platform also has their own set of settings.

This feature supports:

- Android Enterprise
- iOS/iPadOS

## Device features

[Device features](templates/configure-device-features-apple) controls features on iOS/iPadOS and macOS devices, such as AirPrint, notifications, and lock screen messages.

This feature supports:

- iOS/iPadOS
- macOS

## BIOS configuration and DFCI

With [BIOS configuration](templates/configure-bios-windows), administrators can password-protect access to the BIOS and create a configuration file using an OEM tool with the BIOS settings they want. Then, they add this configuration file to the Intune policy.

[Device firmware configuration interface](templates/configure-dfci-windows) (DFCI) allows administrators to enable or disable UEFI (BIOS) settings using Intune. Use these settings to enhance security at the firmware-level, which is typically more resilient to malicious attacks.

This feature supports:

- Windows

## Device restrictions

[Device restrictions](templates/configure-device-restrictions) controls security, hardware, data sharing, and more settings on the devices. For example, create a device restriction profile that prevents iOS/iPadOS device users from using the device camera.

There are also settings that manage access to app stores, restrict users from viewing corporate documents in unmanaged apps, require a password to unlock the device, or require devices to use only specific Wi-Fi networks.

This feature supports:

- Android device administrator
- Android (AOSP)
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows

## Domain join

[Domain join](templates/configure-domain-join-windows) configures on-premises Active Directory domain information. This information is deployed to Microsoft Entra hybrid joined devices when provisioned using Windows Autopilot and Intune. This profile tells devices which domain and OU to join.

This feature supports:

- Windows

## Edition upgrade and mode switch

[Windows edition upgrades](templates/configure-edition-upgrade-windows) automatically upgrades devices that run some versions of Windows client to a newer edition.

This feature supports:

- Windows

## Education

[Education settings - Windows](templates/configure-education-settings) configure options for the [Windows Take a Test app](/en-us/education/windows/take-tests-in-windows-10). When you configure these options, no other apps can run on the device until the test is complete.

[Education settings - iOS/iPadOS](../solutions/education/ref-classroom-settings-ios-shared) uses the iOS/iPadOS Classroom app to guide learning, and control student devices in the classroom. You can configure iPad devices so many students can share a single device.

## Email

[Email settings](templates/configure-email) creates, assigns, and monitors Exchange ActiveSync email settings on the devices. Email profiles help with consistency, reduce support calls, and let end-users access company email on their personal devices, without any required setup on their part.

This feature supports:

- Android device administrator
- Android Enterprise
- iOS/iPadOS
- Windows

## Endpoint protection

Important

This template is deprecated in the August 2024 service release (2408). Existing policies continue to work. But, you can't create new policies using this template.

Instead, use the settings catalog to create new policies that configure the FileVault, Firewall, and System Policy Control (Gatekeeper) payloads. To learn more, go to [macOS settings catalog](settings-catalog/).

[Endpoint protection](endpoint-security/configure-endpoint-protection) configures BitLocker and Microsoft Defender settings for Windows client devices. On macOS devices, you can also configure the firewall, gateway, and other resources.

To onboard Microsoft Defender for Endpoint with Microsoft Intune, see [Configure endpoints using Mobile Device Management (MDM) tools](/en-us/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm).

This feature supports:

- macOS
- Windows

## eSIM cellular

[eSIM cellular profiles](templates/enable-esim) lets administrators configure cellular data plans on your managed devices for internet and data access. After getting activation codes from your mobile operator, use Intune to import these activation codes, and then assign to your eSIM capable devices.

This feature supports:

- Windows

## Extensions

Important

This template is deprecated in the August 2024 service release (2408). Existing policies continue to work. But, you can't create new policies using this template.

Instead, use the settings catalog to create new policies that configure the System Extensions payload. To learn more, go to [macOS settings catalog](settings-catalog/).

[macOS system extensions and kernel extensions](templates/configure-kernel-extensions-macos) allows administrators to add features or programs that extend the native capabilities of the operating system. Configure these settings to trust all extensions from a specific developer or partner, or allow specific extensions.

This feature supports:

- macOS

## Kiosk

[Kiosk settings](templates/configure-kiosk) profile configures a device to run one app, or run many apps. You can also customize other features on your kiosk, including a start menu and a web browser.

This feature supports:

- Windows

    Windows 11 supports single app kiosk only.

Kiosk settings also available as device restrictions for [Android](templates/ref-device-restrictions-android#kiosk), [Android Enterprise](templates/ref-device-restrictions-android-enterprise) (Device experience), and [iOS/iPadOS](templates/ref-device-restrictions-apple).

## MX profile (Zebra)

[Mobility extensions (MX)](templates/configure-zebra-mx-android) expand on the built-in Intune settings to customize or add more settings specific to Zebra devices. Zebra devices are commonly used on factory floors, and retail environments. If you have hundreds or thousands of Zebra devices, you can use Intune to configure and manage these devices.

This feature supports:

- Android device administrator

## Microsoft Defender for Endpoint

[Microsoft Defender for Endpoint](../device-security/microsoft-defender/overview) integrates with Intune to monitor and help protect devices. You set risk levels, and determine what happens if devices exceed that level. When combined with Conditional Access, you can help prevent malicious activity in your organization.

This feature supports:

- Windows

## Network boundary

[Network boundary](templates/create-network-boundary-windows) creates a list of sites that your organization trusts. This feature is used with Microsoft Defender Application Guard and Microsoft Edge to help protect your devices.

This feature supports:

- Windows

## OEMConfig

On Android Enterprise devices, [OEMConfig](templates/configure-oemconfig-android) is a standard. It allows OEMs (original equipment manufacturers) and EMMs (enterprise mobility management) to build and support OEM-specific features in a standardized way.

With OEMConfig, an OEM creates a schema that defines OEM-specific management features, and embeds it in an app uploaded to Google Play. Intune reads the schema from the app, and allows Intune administrators to configure the settings in the schema.

This feature supports:

- Android Enterprise (OEMConfig)

## Preference file

[Preference files](templates/configure-preference-file-macos) on macOS devices include information about apps. For example, you can use preference files to control web browser settings, customize apps, and more.

This feature supports:

- macOS

Tip

macOS settings are continually being added to the [settings catalog](settings-catalog/). Some of these settings can replace preference files. For more information, go to [Tasks you can complete using the Settings Catalog in Intune](settings-catalog/common-tasks).

## Settings catalog and Group Policy analytics

The [settings catalog](settings-catalog/) lists all the available settings you can configure, and all in one place. It's not template, or a logical grouping of settings. The settings catalog is similar to configuring on-premises Group Policy Objects (GPOs), but is cloud native.

On Windows, there are thousands of settings available, including many settings not found in the templates. When you want a complete list of all the settings, use the settings catalog to create your policy. If you want to use a logical grouping of settings, then continue to use the templates.

[Tasks you can complete using the Intune settings catalog](settings-catalog/common-tasks) is a good resource.

This feature supports:

- iOS/iPadOS
- macOS
- Android Enterprise
- Android (AOSP)
- Windows

[Group Policy analytics](import-group-policy-analytics) analyzes your on-premises GPOs. It's a tool that helps you determine how your GPOs translate in the cloud. The output shows any deprecated settings and the settings that are available (or not available) to MDM providers, including Microsoft Intune.

This feature supports:

- Windows

## Shared multi-user device

[Windows](templates/ref-shared-device-settings-windows) and [Windows Holographic for Business](templates/ref-shared-device-settings-windows-holographic) includes settings to manage devices with multiple users. These devices are known as shared devices, or shared PCs. When a user signs in to the device, you choose if the user can change the sleep options, or save files on the device. In another example, to save space, you can create a profile that deletes inactive credentials from Windows HoloLens devices.

These shared multi-user device settings allow administrators to control some of the device features, and manage these shared devices using Intune.

This feature supports:

- Windows
- Windows Holographic for Business

## Shell scripts

On Linux devices, you can [add existing Bash scripts](overview) to customize settings and features on these devices. This concept is similar to creating a custom device configuration profile, and deploying the policy to your devices. With Linux, you're using existing Bash scripts to configure features and settings that aren't built into Intune.

On macOS devices, you can [add existing shell scripts](../device-management/tools/run-shell-scripts-macos), and then deploy these scripts to your macOS devices.

On Windows devices, you can use the Intune Management Extension to upload your [PowerShell scripts](../device-management/tools/run-powershell-scripts-windows) in Intune, and then run these scripts on your devices. Also see what's required to use the extension, how to add them to Intune, and other important information.

This feature supports:

- Linux
- macOS
- Windows

## Update policies

[iOS/iPadOS and macOS managed software updates](../device-updates/apple/) shows you how to create and assign policies to install software updates on your iOS/iPadOS and macOS devices. You can also review the installation status.

For update policies on Windows devices, see [Delivery optimization](templates/configure-delivery-optimization-windows).

This feature supports:

- iOS/iPadOS
- macOS

## VPN

[VPN settings](templates/configure-vpn) assigns VPN profiles to users and devices in your organization, so they can easily and securely connect to the network.

Virtual private networks (VPNs) give users secure remote access to your company network. Devices use a VPN connection profile to start a connection with your VPN server.

This feature supports:

- Android device administrator
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows

## Wi-Fi

[Wi-Fi settings](templates/configure-wifi) assigns wireless network settings to users and devices. When you assign a WiFi profile, users get access to your corporate WiFi without having to configure it themselves.

This feature supports:

- Android device administrator
- Android (AOSP)
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows

## Windows health monitoring

[Windows health monitoring](templates/configure-health-monitoring-windows) lets Endpoint Analytics collect and analyze your event data. You can use this data to get insights on your Windows devices, including software updates and startup performance.

This feature supports:

- Windows

## Wired networks

[Wired networks](templates/configure-wired-networks) let you create and manage 802.1x wired connections for macOS and Windows desktop computers and devices. In your profile, you choose the network interface, select the accepted EAP types, and enter the server trust settings, including PKCS and SCEP certificates.

When you assign the profile, users get access to your corporate wired network without having to configure it themselves.

This feature supports:

- iOS/iPadOS
- macOS
- Windows

## Zebra Mobility Extensions (MX)

[Zebra Mobility Extensions (MX)](templates/configure-zebra-mx-android) allows administrators to use and manage Zebra devices in Intune. You create StageNow profiles with your settings, and then use Intune to assign and deploy these profiles to your Zebra devices. The [StageNow logs and common issues](templates/troubleshoot-zebra-mx-android) is a great resource to troubleshoot profiles, and see some potential issues when using StageNow.

This feature supports:

- Android device administrator (Mobility Extensions)

## Manage and troubleshoot

[Manage your profiles](monitor-device-profile) to check the status of devices, and the profiles assigned. Also help resolve conflicts by seeing the settings that cause a conflict, and the profiles that include these settings.

[Common questions and behaviors with policies and profiles](troubleshoot-device-profiles) helps administrators work with profiles. It describes what happens when deleting a profile, what causes notifications to be sent to devices, and more.