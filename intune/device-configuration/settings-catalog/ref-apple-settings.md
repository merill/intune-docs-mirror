---
layout: Conceptual
title: Apple configuration list for Intune settings catalog - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/ref-apple-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: beflamm
ms.author: beflamm
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use the Microsoft Intune settings catalog to add, configure, or restrict features on Apple devices. This article lists and describes the settings you can configure.
ms.topic: reference
ms.date: 2024-11-13T00:00:00.0000000Z
ms.reviewer: paoloma
locale: en-us
document_id: d7953ef1-5451-944d-b861-3cef4c4529db
document_version_independent_id: d7953ef1-5451-944d-b861-3cef4c4529db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/ref-apple-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/ref-apple-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/ref-apple-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: ea2321c3-909b-394f-6380-992182661550
---

# Apple configuration list for Intune settings catalog - Microsoft Intune | Microsoft Learn

This article lists and describes the Apple configurations you can manage using a settings catalog policy in Microsoft Intune.

This article applies to:

- iOS/iPadOS
- macOS

## Before you begin

- At a minimum, sign in to the Intune admin center as a member of the **Policy and Profile Manager** role. For more information on the built-in Intune roles, go to [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).
- Create a [settings catalog policy](./).

### How to use this article

This article covers the two types of configurations from Apple's mobile device management (MDM) protocol:

- Apple declarative configurations
- Apple MDM payloads

Each section can have links to other documents:

- **Apple platform guides**: The Apple Platform Deployment and Security guides that cover deployment and security features of Apple technology
- **Apple developer**: The developer documentation outlines the device management API that gets updated with every OS release
- **Apple YAML**: Apple GitHub repository that contains setting definitions that are ingested into the settings catalog. Use this information to see requirements like applicable OS version, enrollment types, and if supervision is required
- **Intune documentation**: Intune guides for scenario-based configuration like setting up Platform Single Sign On or deploying declarative software updates
- **Known issues**: Updated list of known issues related to each configuration

Some settings are available in device configuration templates and in the settings catalog. To help with a manual policy migration, this article lists the template settings that maps to their equivalent setting in the settings catalog.

Important

It's recommended to create all new policies using the settings catalog where possible. Some of the existing device configuration templates are no longer being updated. In a future Intune release, they will be migrated to use the settings catalog policy type and the ability to create new templates will be deprecated. These templates include:

- Device features
- Device restrictions
- Endpoint protection (Deprecated)
- Extensions (Deprecated)

Policies that should still be created using templates include:

- Derived credential
- Email
- PKCS certificate
- PKCS imported certificate
- SCEP certificate
- Trusted certificate
- VPN
- Wi-Fi
- Wired network

## Apple declarative configurations

This section is specific to the configurations that are under the Declarative Device Management (DDM) category in the settings catalog. You can learn more about DDM at [Intro to declarative device management and Apple devices](https://support.apple.com/guide/deployment/depb1bab77f8/1/web/1.0) on Apple's website.

### Disk Management

Use Disk Management setting to install disk management settings on devices. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about Disk Management using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| [Storage management declarative configuration](https://support.apple.com/en-tm/guide/deployment/dep2b9f009ed/web) | [Disk Management Settings](https://developer.apple.com/documentation/devicemanagement/diskmanagementsettings) | [Disk Management Settings](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/diskmanagement.settings.yaml) |  |

**Known issues**

- None

### Math Settings

Use Math Settings to configure the Math and Calculator apps on devices. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about Math Settings using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| [Math and Calculator app declarative configuration](https://support.apple.com/en-tm/guide/deployment/dep7881be3bb/web) | [Math Settings](https://developer.apple.com/documentation/devicemanagement/mathsettings) | [Math Settings](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/math.settings.yaml) |  |

**Known issues**

- None

### Passcode

Use the passcode configuration to require that devices have a password or passcode that meet your organization's requirements. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about Passcode using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| - [Passcodes and passwords](https://support.apple.com/guide/security/sec20230a10d/web)<br>- [Passcode declarative configuration](https://support.apple.com/guide/deployment/depf72b010a8/1/web/1.0) | [Passcode](https://developer.apple.com/documentation/devicemanagement/passcode) | [Passcode](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/passcode.settings.yaml) |  |

**Known issues**

- None

### Safari Extension Settings

Use the Safari extensions settings to manage extensions in the Safari browser. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about Safari Extension Settings using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| [Safari extensions management declarative configuration](https://support.apple.com/en-tm/guide/deployment/depff7fad9d8/web) | [Safari Extension Settings](https://developer.apple.com/documentation/devicemanagement/safariextensionsettings) | [Safari Extension Settings](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/safari.extensions.settings.yaml) |  |

**Known issues**

- None

### Software Update

Use the Software Update configuration to enforce an update to install at a specific time. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about this configuration using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| - [Software Update declarative configuration](https://support.apple.com/guide/deployment/depca14ecd4d/1/web/1.0)<br>- [Installing and enforcing software updates](https://support.apple.com/guide/deployment/depd30715cbb/web) | [Software Update Enforcement Specific](https://developer.apple.com/documentation/devicemanagement/softwareupdateenforcementspecific) | [Software Update Enforcement Specific](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/softwareupdate.enforcement.specific.yaml) | [Use the settings catalog to configure managed software updates](../../device-updates/apple/) |

**Known issues**

- None

### Software Update Settings

Use the Software Update Settings configuration to defer OS updates and control how users can manually interact with software updates in System Settings. This configuration is located in the **Declarative Device Management (DDM)** category of the settings catalog. You can learn more about Software Update Settings using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| [Software Update Settings declarative configuration](https://support.apple.com/en-tm/guide/deployment/dep0578d8b8a/web) | [Software Update Settings](https://developer.apple.com/documentation/devicemanagement/softwareupdatesettings) | [Software Update Settings](https://github.com/apple/device-management/blob/release/declarative/declarations/configurations/softwareupdate.settings.yaml) | [Use the settings catalog to configure managed software updates](../../device-updates/apple/) |

**Known issues**

- None

## Apple MDM payload settings

This section is specific to Apple payloads that use the standard MDM channel. A list of these payloads is available at [Review MDM payloads for Apple devices](https://support.apple.com/guide/deployment/dep5370d089/web) on Apple's website.

### FileVault

Use FileVault configurations to manage disk encryption on macOS devices. These configurations are located in the **Full Disk Encryption** category of the settings catalog. You can learn more about FileVault using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| - [Introduction to FileVault](https://support.apple.com/guide/deployment/dep82064ec40/web)<br>- [FileVault payload for Apple devices](https://support.apple.com/guide/deployment/dep32bf53500/web) | - [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault)<br>- [FDEFileVaultOptions](https://developer.apple.com/documentation/devicemanagement/fdefilevaultoptions)<br>- [FDERecoveryKeyEscrow](https://developer.apple.com/documentation/devicemanagement/fderecoverykeyescrow) | - [FileVault](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.MCX.FileVault2.yaml)<br>- [FileVault Options](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.MCX%28FileVault2%29.yaml)<br>- [FileVault Recovery Key Escrow](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.security.FDERecoveryKeyEscrow.yaml) | [Encrypt macOS devices (Microsoft Learn)](../endpoint-security/encrypt-filevault-macos) |

**Known issues**

- [FileVault failing to enable on macOS devices during Setup Assistant](https://techcommunity.microsoft.com/t5/intune-customer-success/known-issue-filevault-failing-to-enable-on-macos-devices-during/ba-p/4180523)

#### Intune device configuration template to settings catalog mapping

| Endpoint protection template | Settings catalog category | Settings catalog setting |
| --- | --- | --- |
| Enable FileVault | Full Disk Encryption &gt; FileVault | Enable |
| Escrow location description of personal recovery key | Full Disk Encryption &gt; FileVault Recovery Key Escrow | Location |
| Personal recovery key rotation | Full Disk Encryption &gt; FileVault | Recovery Key Rotation In Months |
| Hide recovery key | Full Disk Encryption &gt; FileVault | Show Recovery Key |
| Disable prompt at sign out | Full Disk Encryption &gt; FileVault | Defer Don't Ask At User Logout |
| Number of times allowed to bypass | Full Disk Encryption &gt; FileVault | Defer Force At User Login Max Bypass Attempts |

### Firewall

Use the Firewall configuration to manage the native macOS application firewall. This configuration is located in the **Security** category of the settings catalog. You can learn more about Firewall using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML |
| --- | --- | --- |
| - [Firewall security in macOS](https://support.apple.com/guide/security/seca0e83763f/web)<br>- [Firewall payload](https://support.apple.com/guide/deployment/dep8d306275f/web) | [Firewall](https://developer.apple.com/documentation/devicemanagement/firewall) | [Firewall (YAML)](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.security.firewall.yaml) |

**Known issues**

- [macOS devices using stealth mode turn noncompliant after upgrading to macOS 15](https://techcommunity.microsoft.com/t5/intune-customer-success/known-issue-macos-devices-using-stealth-mode-turn-non-compliant/ba-p/4250583)

#### Intune device configuration template to settings catalog mapping

| Endpoint protection template | Settings catalog category | Settings catalog setting |
| --- | --- | --- |
| Enable Firewall | Networking &gt; Firewall | Enable Firewall |
| Block all incoming connections | Networking &gt; Firewall | Block All Incoming |
| Apps allowed | Networking &gt; Firewall | Applications (Allowed = True) |
| Apps blocked | Networking &gt; Firewall | Applications (Allowed = False) |
| Enable stealth mode | Networking &gt; Firewall | Enable Stealth Mode |

### Font

Note

Font files being uploaded to Intune must be less than 2MB in size.

Use the Font payload to configure fonts on devices. This configuration is located in the **System Configuration** category of the settings catalog. You can learn more about Font using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML | Intune documentation |
| --- | --- | --- | --- |
| [Fonts MDM payload settings](https://support.apple.com/en-tm/guide/deployment/depeba084b8/web) | [Font](https://developer.apple.com/documentation/devicemanagement/font) | [Font](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.font.yaml) |  |

**Known issues**

- None

### System Policy Control (Gatekeeper)

Use the System Policy Control payload to configure Gatekeeper settings. This configuration is located in the **System Policy Control** category of the settings catalog. You can learn more about System Policy Control using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML |
| --- | --- | --- |
| - [Gatekeeper and runtime protection](https://support.apple.com/guide/security/sec5599b66df/web)<br>- [Security MDM payload](https://support.apple.com/guide/deployment/dep61dc030/web) | [SystemPolicyControl](https://developer.apple.com/documentation/devicemanagement/systempolicycontrol) | [System Policy Control](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.systempolicy.control.yaml) |

**Known issues**

- None

#### Intune device configuration template to settings catalog mapping

| Endpoint protection template | Settings catalog category | Settings catalog setting |
| --- | --- | --- |
| Do not allow user to override Gatekeeper | System Policy Control &gt; System Policy Control | Enable Assessment |
| Allow apps downloaded from these locations | System Policy Control &gt; System Policy Control | Allow Identified Developers |

### System Extensions

Use the System Extensions payload to configure system extensions to be automatically loaded or prevent users from approving specific extensions. This configuration is located in the **System Configuration** category of the settings catalog. You can learn more about System Extensions using the following documentation:

| Apple Platform Guides | Apple Developer | Apple YAML |
| --- | --- | --- |
| - [System and kernel extensions](https://support.apple.com/guide/deployment/system-and-kernel-extensions-in-macos-depa5fb8376f/web)<br>- [System Extensions](https://support.apple.com/guide/deployment/dep5d1584ca4/web) | [System Extensions](https://developer.apple.com/documentation/devicemanagement/systemextensions) | [System Extensions](https://github.com/apple/device-management/blob/release/mdm/profiles/com.apple.system-extension-policy.yaml) |

**Known issues**

- None

#### Intune device configuration template to settings catalog mapping

| Extensions template | Settings catalog category | Settings catalog setting |
| --- | --- | --- |
| Block User Overrides | System Configuration &gt; System Extensions | Allow User Overrides |
| Allowed team identifiers | System Configuration &gt; System Extensions | Allowed Team Identifiers |
| Allowed system extensions | System Configuration &gt; System Extensions | Allowed System Extensions |
| Allowed system extension types | System Configuration &gt; System Extensions | Allowed System Extension Types |