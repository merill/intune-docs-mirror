---
layout: Conceptual
title: Protect data and devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: Learn about the Intune capabilities that can help you protect your devices and data against unauthorized access and other threats.
ms.date: 2026-02-17T00:00:00.0000000Z
ms.topic: overview
ai-usage: ai-assisted
ms.reviewer: davidra
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
locale: en-us
document_id: 33a9cec3-9b55-4214-e56a-2ef7e89c77fe
document_version_independent_id: 33a9cec3-9b55-4214-e56a-2ef7e89c77fe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6daa2dc9-6cef-b934-340a-bc19e8e1c186
---

# Protect data and devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune helps you keep managed devices secure and up to date while protecting your organization's data from compromised devices. Control what users do with organizational data on both managed and unmanaged devices, and block access to data from potentially compromised devices.

This article introduces Intune's built-in security capabilities and partner technologies that work together to support **Zero Trust** solutions for your organization. As an overview, it describes key protection capabilities and links to detailed documentation for configuration and deployment guidance.

Intune can also integrate with third-party products that provide device compliance and Mobile Threat Defense (MTD) signals.

## Platform support

From the Microsoft Intune admin center, Intune [supports managed devices](../fundamentals/ref-supported-platforms#intune-supported-operating-systems) that run:

- Android
- iOS/iPadOS
- Linux
- macOS
- Windows

In addition, when you use Configuration Manager to manage on-premises devices, you can extend Intune policies to those devices through tenant attach or co-management.

## Deploy security policies to protect devices

Deploy policies to configure and enforce security on enrolled devices. The following policy types work together to protect devices:

**[Endpoint security policies](endpoint-security-policies)** - Focused security policies for specific protection areas:

- **Account protection** - Windows Hello for Business, Credential Guard, and Windows LAPS
- **Antivirus** - Microsoft Defender Antivirus configuration and exclusions
- **App Control for Business** - Application allowlisting using Windows Defender Application Control
- **Attack surface reduction** - Reduce exploit vulnerabilities and attack vectors
- **Disk encryption** - BitLocker, Personal Data Encryption (PDE), and FileVault
- **Endpoint detection and response** - Microsoft Defender for Endpoint onboarding
- **Firewall** - Network protection and firewall rules

**[Device configuration policies](../device-configuration/overview)** - Broader device settings including endpoint protection, certificates, software updates, and VPN. Use when you need to combine security settings with device functionality configurations.

**[Device compliance policies](compliance/overview)** - Define device requirements like OS versions, encryption status, and threat levels. Noncompliant devices trigger alerts and can be blocked from organizational resources when combined with Conditional Access.

### Key security capabilities

The following security areas can be managed through these policies:

- **Authentication and identity**

    - **Certificates** - Deploy certificates using [SCEP and PKCS profiles](../fundamentals/certificates/overview), or use [Microsoft Cloud PKI](../cloud-pki/) for simplified cloud-based certificate management without on-premises infrastructure. Configure [derived credentials](certificates/derived-credentials) for smartcard scenarios.
    - **Modern authentication** - Enable [Windows Hello for Business](identity-protection/configure-tenant-wide-policy) for passwordless sign-in. Configure [Platform SSO for macOS](../device-configuration/settings-catalog/configure-platform-sso-macos) to strengthen authentication across apps and services.
    - **Multi-factor authentication** - Use Microsoft Entra Conditional Access to require MFA, and use Intune to configure device PIN/password and other sign-in related settings as needed.
- **Data encryption**

    - **Windows** - Deploy [BitLocker](../device-configuration/endpoint-security/encrypt-bitlocker-windows) for full disk encryption and [Personal Data Encryption (PDE)](../device-configuration/endpoint-security/encrypt-bitlocker-windows#personal-data-encryption-pde) for file-level encryption on Windows 11.
    - **macOS** - Manage [FileVault](../device-configuration/endpoint-security/encrypt-filevault-macos) for full disk encryption.
- **Software updates** - Control when and how devices receive updates:

    - **Android** - [FOTA updates](../device-updates/android/manage-fota) for OEM firmware, [Zebra LifeGuard OTA](../device-updates/android/setup-zebra-lifeguard) for Zebra devices.
    - **iOS/iPadOS and macOS** - [Configure update policies](../device-updates/apple/) to manage OS versions and update schedules.
    - **Windows** - Configure [Windows Update behaviors](../device-updates/windows/), schedule updates, and maintain feature update compliance.
- **Application control** - Use [App Control for Business](../device-configuration/endpoint-security/manage-app-control) policies to define which applications can run on Windows devices.
- **Attack surface reduction** - Deploy [ASR policies](../device-configuration/endpoint-security/attack-surface-reduction) to reduce vulnerabilities through exploit protection, device control, application isolation, and ASR rules.
- **Security baselines** - Deploy preconfigured [security baselines](security-baselines/overview) for Windows devices, Microsoft Edge, and Microsoft Defender for Endpoint that reflect Microsoft security team recommendations.
- **Network security**

    - **VPN profiles** - Configure [VPN connections](../device-configuration/templates/configure-vpn#vpn-connection-types) for secure remote access to organizational resources.
    - **Firewall policies** - Manage built-in firewall protection on Windows and macOS devices.
- **Privileged access management**

    - **[Windows LAPS](laps/overview)** - Manage local administrator passwords with automatic rotation and secure backup to Active Directory or Microsoft Entra.
    - **Endpoint Privilege Management** - Run users as standard accounts while allowing elevation for approved applications.

## Protect data with app protection policies

Protect organizational data at the application layer using [app protection policies](../app-management/protection/overview) with Intune-managed apps. These protections work on both enrolled and unenrolled devices, supporting Bring Your Own Device (BYOD) scenarios.

**Intune-managed apps** integrate the [Intune App SDK](../developer/app-sdk/) or use the [Intune App Wrapping Tool](../developer/app-sdk/integration-methods). See [Intune protected apps](../app-management/ref-protected-apps) for a list of supported apps.

When you require managed apps (for example, by using app-based Conditional Access policies), users can only access organizational data through those managed apps, while personal data remains unaffected.

**Key app protection policy capabilities:**

- Require PIN or biometric authentication for organizational data access.
- Block copy/paste, screenshots, and data transfer to unmanaged apps.
- Prevent saving organizational data to personal storage.
- Enforce encryption of organizational data at rest.
- Wipe organizational data remotely when devices are lost or users leave.

## Use device actions to protect devices and data

Run [device actions](../device-management/actions/) to respond to security incidents or maintain device security. Unlike policies that maintain ongoing configurations, device actions execute once when invoked. Actions take effect immediately for online devices, or at next check-in for offline devices. [Bulk device actions](../device-management/actions/#bulk-device-actions) can target multiple devices simultaneously.

**Common security actions:**

- **Remote lock** - Lock a device remotely to prevent unauthorized access.
- **Wipe** - Factory reset a device, removing all data and settings.
- **Retire** - Remove organizational data while preserving personal data.
- **BitLocker key rotation** (Windows) - Rotate encryption keys for enhanced security.
- **Antivirus scan** (Windows) - Run full or quick malware scans.
- **Update Defender intelligence** - Refresh threat definitions.
- **Disable Activation Lock** (iOS/iPadOS) - Remove Activation Lock for device reuse.

These actions are also available for devices managed through Configuration Manager when using co-management or tenant attach.

## Integrate with partner technologies

Extend Intune's protection capabilities through integrations with Microsoft technologies and third-party partners.

### Compliance partners

Integrate [device compliance data](compliance/third-party-partners) from third-party MDM solutions with Microsoft Entra ID. This enables organizations with mixed management environments to enforce unified Conditional Access policies across all devices, regardless of which MDM solution manages them.

### Configuration Manager

Extend Intune's cloud-based security policies to on-premises and hybrid-managed devices through [co-management](../configmgr/comanage/overview) or [tenant attach](../configmgr/tenant-attach/device-sync-actions). This integration provides a unified management experience for organizations transitioning to cloud management or maintaining hybrid infrastructure:

- **Co-management** - Concurrently manage Windows devices with both Configuration Manager and Intune, with workload sliders to control which service manages specific capabilities.
- **Tenant attach** - Synchronize Configuration Manager devices into the Microsoft Intune admin center for centralized visibility and management.

Both approaches enable [Intune security policies](endpoint-security-devices) on Configuration Manager devices, including endpoint security policies, compliance policies, certificate deployment (SCEP/PKCS), and security baselines. This creates a consistent security posture across cloud and on-premises managed devices.

### Mobile Threat Defense

[Mobile Threat Defense (MTD)](mobile-threat-defense/overview) partners extend threat detection beyond Microsoft's built-in capabilities by scanning for device-level threats, network threats, app-based threats, and phishing attempts. MTD apps continuously assess device risk and report threat levels to Intune, enabling risk-based access decisions through compliance policies, app protection policies, and Conditional Access.

**For [enrolled devices](mobile-threat-defense/create-compliance-policy)**, Intune deploys and manages MTD apps while using their threat level assessments in device compliance evaluations. Devices exceeding acceptable risk thresholds can be blocked from accessing organizational resources until threats are remediated.

**For [unenrolled devices](mobile-threat-defense/create-app-protection-policy)** in BYOD scenarios, MTD threat levels inform app protection policy decisions, blocking access to organizational data within managed apps when device risk is too high.

Intune supports [Microsoft Defender for Endpoint](microsoft-defender/overview) with enhanced integration capabilities, and multiple [third-party MTD partners](mobile-threat-defense/overview#mobile-threat-defense-partners) to fit diverse security requirements.

### Microsoft Defender for Endpoint

[Microsoft Defender for Endpoint deeply integrates with Intune](microsoft-defender/overview) across Windows, macOS, Linux, Android, and iOS/iPadOS, creating a unified security platform that combines device management with advanced threat protection. This integration enables:

- **Threat intelligence and risk assessment** - Defender's continuous threat detection and device risk scores flow directly into Intune compliance policies and Conditional Access decisions, enabling dynamic, risk-based access control
- **Enhanced endpoint security management** - Configure and deploy Defender capabilities through Intune policies, including [Antivirus](../device-configuration/endpoint-security/antivirus) settings, [EDR onboarding](../device-configuration/endpoint-security/deploy-edr), Attack Surface Reduction rules, [controlled configuration](../device-configuration/endpoint-security/antivirus#controlled-configuration-for-microsoft-defender-settings-preview) (which also supports tamper protection), web protection, and device control
- **Vulnerability management** - [Security tasks](microsoft-defender/remediate-vulnerabilities) create a collaboration workflow where Defender's threat and vulnerability management identifies at-risk devices and provides remediation guidance that Intune admins can act on directly
- **[Microsoft Tunnel](microsoft-tunnel/overview)** - Defender for Endpoint serves as the VPN client for Microsoft Tunnel on Android devices, providing secure remote access without requiring separate Defender licensing

### Conditional Access

[Conditional Access](conditional-access-integration/overview) is a Microsoft Entra capability that serves as the enforcement engine for Zero Trust access policies. It evaluates signals from Intune and other sources to make real-time access decisions, helping to ensure only trusted users on compliant devices can access organizational resources.

**Conditional Access evaluates multiple signals:**

- Device compliance status from Intune policies
- Device risk levels from Microsoft Defender for Endpoint and MTD partners
- User risk and sign-in risk from Microsoft Entra ID Protection
- Location, device platform, and application being accessed

**Conditional Access with Intune enables:**

- [Device-based policies](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) - Require devices to meet compliance requirements before accessing organizational resources.
- [App-based policies](conditional-access-integration/app-based-policies) - Ensure only apps protected by Intune app protection policies can access Microsoft 365 and other services.
- Risk-based access - Dynamically adjust access requirements based on real-time threat intelligence from Defender and MTD partners.

Conditional Access works across managed and unmanaged devices, helping create an access control layer that adapts to changing threat conditions.

## Add Endpoint Privilege Management

[Endpoint Privilege Management (EPM)](../epm/overview) enforces **least privilege access** for Windows users by running them as standard users while allowing temporary elevation for approved applications. This approach reduces attack surface by preventing blanket administrative access.

**How EPM works:**

- Users run as standard accounts by default.
- Elevation rules define which applications can run with elevated privileges.
- Applications are validated using file hashes, certificates, or other criteria.
- Common elevated scenarios: application installations, driver updates, Windows diagnostics.

Note

EPM is a [Microsoft Intune advanced capability](../fundamentals/advanced-capabilities) for Windows devices and requires additional licensing beyond Microsoft Intune.