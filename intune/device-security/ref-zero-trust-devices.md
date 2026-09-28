---
layout: Conceptual
title: Configure Microsoft Intune for increased device security - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-devices
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: Secure devices with Microsoft Intune to support your Zero Trust journey.
ms.topic: reference
ms.date: 2025-10-20T00:00:00.0000000Z
ms.reviewer: ramical
ms.collection:
- tier 1
- M365-identity-device-management
locale: en-us
document_id: 942b60a6-de50-e351-dfee-194e87b0ce5b
document_version_independent_id: 942b60a6-de50-e351-dfee-194e87b0ce5b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/ref-zero-trust-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/ref-zero-trust-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/ref-zero-trust-devices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: daf60f40-a567-586b-dd31-f881a5b38398
---

# Configure Microsoft Intune for increased device security - Microsoft Intune | Microsoft Learn

Securing endpoints is a critical part of a Zero Trust strategy. These Intune recommendations help protect your network perimeter and devices through policy-driven controls that enforce encryption, restrict unauthorized access, and reduce vulnerability exposure. By applying configuration and security policies across platforms, these checks align with Microsoft’s [Secure Future Initiative](https://www.microsoft.com/trust-center/security/secure-future-initiative?msockid=2bad2df65a416adb0e5838355b3e6b95#SFI-pillars) and strengthen your organization’s overall security posture.

## Zero Trust security recommendations

### Local administrator credentials on Windows are protected by Windows LAPS

Without enforcing Local Administrator Password Solution (LAPS) policies, threat actors who gain access to endpoints can exploit static or weak local administrator passwords to escalate privileges, move laterally, and establish persistence. The attack chain typically begins with device compromise—via phishing, malware, or physical access—followed by attempts to harvest local admin credentials. Without LAPS, attackers can reuse compromised credentials across multiple devices, increasing the risk of privilege escalation and domain-wide compromise.

Enforcing Windows LAPS on all corporate Windows devices ensures unique, regularly rotated local administrator passwords. This disrupts the attack chain at the credential access and lateral movement stages, significantly reducing the risk of widespread compromise.

**Remediation action**

Use Intune to enforce Windows LAPS policies that rotate strong and unique local admin passwords, and that back them up securely:

- [Deploy Windows LAPS policy with Microsoft Intune](/en-us/intune/device-security/laps/deploy-policy#create-a-laps-policy)

For more information, see:

- [Windows LAPS policy settings reference](/en-us/windows-server/identity/laps/laps-management-policy-settings)
- [Learn about Intune support for Windows LAPS](/en-us/intune/device-security/laps/overview)

### Local administrator credentials on macOS are protected during enrollment by macOS LAPS

Without enforcing macOS LAPS policies during Automated Device Enrollment (ADE), threat actors can exploit static or reused local administrator passwords to escalate privileges, move laterally, and establish persistence. Devices provisioned without randomized credentials are vulnerable to credential harvesting and reuse across multiple endpoints, increasing the risk of domain-wide compromise.

Enforcing macOS LAPS ensures that each device is provisioned with a unique, encrypted local administrator password managed by Intune. This disrupts the attack chain at the credential access and lateral movement stages, significantly reducing the risk of widespread compromise and aligning with Zero Trust principles of least privilege and credential hygiene.

**Remediation action**

Use Intune to configure macOS ADE profiles that provision a local admin account with a randomized and encrypted password, and that enables secure rotation:

- [Configure macOS LAPS in Microsoft Intune](/en-us/intune/device-security/laps/setup-macos)
- [Rotate local admin password (macOS)](/en-us/intune/device-management/actions/rotate-local-admin-password?pivots=macos)

For more information, see:

- [macOS ADE setup guide](/en-us/intune/device-enrollment/apple/setup-automated-macos)

### Local account usage on Windows is restricted to reduce unauthorized access

Without a properly configured and assigned Local Users and Groups policy in Intune, threat actors can exploit unmanaged or misconfigured local accounts on Windows devices. This can lead to unauthorized privilege escalation, persistence, and lateral movement within the environment. If local administrator accounts aren't controlled, attackers can create hidden accounts or elevate privileges, bypassing compliance and security controls. This gap increases the risk of data exfiltration, ransomware deployment, and regulatory noncompliance.

Ensuring that Local Users and Groups policies are enforced on managed Windows devices, by using account protection profiles, is critical to maintaining a secure and compliant device fleet.

**Remediation action**

Configure and deploy a **Local user group membership** profile from Intune account protection policy to restrict and manage local account usage on Windows devices:

- Create an [Account protection policy for endpoint security in Intune](/en-us/intune/device-configuration/endpoint-security/account-protection#account-protection-profiles)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

### Data on Windows is protected by BitLocker encryption

Without a properly configured and assigned BitLocker policy in Intune, threat actors can exploit unencrypted Windows devices to gain unauthorized access to sensitive corporate data. Devices that lack enforced encryption are vulnerable to physical attacks, like disk removal or booting from external media, allowing attackers to bypass operating system security controls. These attacks can result in data exfiltration, credential theft, and further lateral movement within the environment.

Enforcing BitLocker across managed Windows devices is critical for compliance with data protection regulations and for reducing the risk of data breaches.

**Remediation action**

Use Intune to enforce BitLocker encryption and monitor compliance across all managed Windows devices:

- [Create a BitLocker policy for Windows devices in Intune](/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows#create-and-deploy-policy)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)
- [Monitor device encryption with Intune](/en-us/intune/device-management/monitor-encryption)

### FileVault encryption protects data on macOS devices

Without properly configured and assigned FileVault encryption policies in Intune, threat actors can exploit physical access to unmanaged or misconfigured macOS devices to extract sensitive corporate data. Unencrypted devices allow attackers to bypass operating system-level security by booting from external media or removing the storage drive. These attacks can expose credentials, certificates, and cached authentication tokens, enabling privilege escalation and lateral movement. Additionally, unencrypted devices undermine compliance with data protection regulations and increase the risk of reputational damage and financial penalties in the event of a breach.

Enforcing FileVault encryption protects data at rest on macOS devices, even if lost or stolen. It disrupts credential harvesting and lateral movement, supports regulatory compliance, and aligns with Zero Trust principles of device trust.

**Remediation action**

Use Intune to enforce FileVault encryption and monitor compliance on all managed macOS devices:

- [Create a FileVault disk encryption policy for macOS in Intune](/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos#create-endpoint-security-policy-for-filevault)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)
- [Monitor device encryption with Intune](/en-us/intune/device-management/monitor-encryption)

### Authentication on Windows uses Windows Hello for Business

If policies for Windows Hello for Business (WHfB) aren't configured and assigned to all users and devices, threat actors can exploit weak authentication mechanisms—like passwords—to gain unauthorized access. This can lead to credential theft, privilege escalation, and lateral movement within the environment. Without strong, policy-driven authentication like WHfB, attackers can compromise devices and accounts, increasing the risk of widespread impact.

Enforcing WHfB disrupts this attack chain by requiring strong, multifactor authentication, which helps reduce the risk of credential-based attacks and unauthorized access.

**Remediation action**

Deploy Windows Hello for Business in Intune to enforce strong, multifactor authentication:

- [Configure a tenant-wide Windows Hello for Business policy](/en-us/intune/device-security/identity-protection/configure-tenant-wide-policy#create-a-windows-hello-for-business-policy-for-device-enrollment) that applies at the time a device enrolls with Intune.
- After enrollment, [configure Account protection profiles](/en-us/intune/device-configuration/endpoint-security/account-protection#account-protection-profiles) and [assign](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups) different configurations for Windows Hello for Business to different groups of users and devices.

### Attack Surface Reduction rules are applied to Windows devices to prevent exploitation of vulnerable system components

If Intune profiles for Attack Surface Reduction (ASR) rules aren't properly configured and assigned to Windows devices, threat actors can exploit unprotected endpoints to execute obfuscated scripts and invoke Win32 API calls from Office macros. These techniques are commonly used in phishing campaigns and malware delivery, allowing attackers to bypass traditional antivirus defenses and gain initial access. Once inside, attackers escalate privileges, establish persistence, and move laterally across the network. Without ASR enforcement, devices remain vulnerable to script-based attacks and macro abuse, undermining the effectiveness of Microsoft Defender and exposing sensitive data to exfiltration. This gap in endpoint protection increases the likelihood of successful compromise and reduces the organization’s ability to contain and respond to threats.

Enforcing ASR rules helps block common attack techniques such as script-based execution and macro abuse, reducing the risk of initial compromise and supporting Zero Trust by hardening endpoint defenses.

**Remediation action**

Use Intune to deploy **Attack Surface Reduction Rules** profiles for Windows devices to block high-risk behaviors and strengthen endpoint protection:

- [Configure Intune profiles for Attack Surface Reduction Rules](/en-us/intune/device-configuration/endpoint-security/attack-surface-reduction#devices-managed-by-intune)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

For more information, see:

- [Attack surface reduction rules reference](/en-us/defender-endpoint/attack-surface-reduction-rules-reference) in the Microsoft Defender documentation.

### Defender Antivirus policies protect Windows devices from malware

If policies for Microsoft Defender Antivirus aren't properly configured and assigned in Intune, threat actors can exploit unprotected endpoints to execute malware, disable antivirus protections, and persist within the environment. Without enforced antivirus policies, devices operate with outdated definitions, disabled real-time protection, or misconfigured scan schedules. These gaps allow attackers to bypass detection, escalate privileges, and move laterally across the network. The absence of antivirus enforcement undermines device compliance, increases exposure to zero-day threats, and can result in regulatory noncompliance. Attackers leverage these weaknesses to maintain persistence and evade detection, especially in environments lacking centralized policy enforcement.

Enforcing Defender Antivirus policies ensures consistent protection against malware, supports real-time threat detection, and aligns with Zero Trust by maintaining a secure and compliant endpoint posture.

**Remediation action**

Configure and assign Intune policies for Microsoft Defender Antivirus to enforce real-time protection, maintain up-to-date definitions, and reduce exposure to malware:

- [Configure Intune policies to manage Microsoft Defender Antivirus](/en-us/intune/device-configuration/endpoint-security/antivirus#windows)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

### Defender Antivirus policies protect macOS devices from malware

If Microsoft Defender Antivirus policies aren't properly configured and assigned to macOS devices in Intune, attackers can exploit unprotected endpoints to execute malware, disable antivirus protections, and persist in the environment. Without enforced policies, devices run outdated definitions, lack real-time protection, or have misconfigured scan schedules, increasing the risk of undetected threats and privilege escalation. This enables lateral movement across the network, credential harvesting, and data exfiltration. The absence of antivirus enforcement undermines device compliance, increases exposure of endpoints to zero-day threats, and can result in regulatory noncompliance. Attackers use these gaps to maintain persistence and evade detection, especially in environments without centralized policy enforcement.

Enforcing Defender Antivirus policies ensures that macOS devices are consistently protected against malware, supports real-time threat detection, and aligns with Zero Trust by maintaining a secure and compliant endpoint posture.

**Remediation action**

Use Intune to configure and assign Microsoft Defender Antivirus policies for macOS devices to enforce real-time protection, maintain up-to-date definitions, and reduce exposure to malware:

- [Configure Intune policies to manage Microsoft Defender Antivirus](/en-us/intune/device-configuration/endpoint-security/antivirus#macos)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

### Windows Firewall policies protect against unauthorized network access

If policies for Windows Firewall aren't configured and assigned, threat actors can exploit unprotected endpoints to gain unauthorized access, move laterally, and escalate privileges within the environment. Without enforced firewall rules, attackers can bypass network segmentation, exfiltrate data, or deploy malware, increasing the risk of widespread compromise.

Enforcing Windows Firewall policies ensures consistent application of inbound and outbound traffic controls, reducing exposure to unauthorized access and supporting Zero Trust through network segmentation and device-level protection.

**Remediation action**

Configure and assign firewall policies for Windows in Intune to block unauthorized traffic and enforce consistent network protections across all managed devices:

- [Configure firewall policies for Windows devices](/en-us/intune/device-configuration/endpoint-security/firewall). Intune uses two complementary profiles to manage firewall settings:
    - **Windows Firewall** - Use this profile to configure overall firewall behavior based on network type.
    - **Windows Firewall rules** - Use this profile to define traffic rules for apps, ports, or IPs, tailored to specific groups or workloads. This Intune profile also supports use of [reusable settings groups](/en-us/intune/device-configuration/endpoint-security/firewall#add-reusable-settings-groups-to-profiles-for-firewall-rules) to help simplify management of common settings you use for different profile instances.
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

For more information, see:

- [Available Windows Firewall settings](/en-us/intune/device-configuration/endpoint-security/ref-firewall-settings#windows-firewall-profile)

### macOS Firewall policies protect against unauthorized network access

Without a centrally managed firewall policy, macOS devices might rely on default or user-modified settings, which often fail to meet corporate security standards. This exposes devices to unsolicited inbound connections, enabling threat actors to exploit vulnerabilities, establish outbound command-and-control (C2) traffic for data exfiltration, and move laterally within the network—significantly escalating the scope and impact of a breach.

Enforcing macOS Firewall policies ensures consistent control over inbound and outbound traffic, reducing exposure to unauthorized access and supporting Zero Trust through device-level protection and network segmentation.

**Remediation action**

Configure and assign **macOS Firewall** profiles in Intune to block unauthorized traffic and enforce consistent network protections across all managed macOS devices:

- [Configure the built-in firewall on macOS devices](/en-us/intune/device-configuration/endpoint-security/firewall)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)

For more information, see:

- [Available macOS firewall settings](/en-us/intune/device-configuration/endpoint-security/ref-firewall-settings#macos-firewall-profile)

### Windows Update policies are enforced to reduce risk from unpatched vulnerabilities

If Windows Update policies aren't enforced across all corporate Windows devices, threat actors can exploit unpatched vulnerabilities to gain unauthorized access, escalate privileges, and move laterally within the environment. The attack chain often begins with device compromise via phishing, malware, or exploitation of known vulnerabilities, and is followed by attempts to bypass security controls. Without enforced update policies, attackers leverage outdated software to persist in the environment, increasing the risk of privilege escalation and domain-wide compromise.

Enforcing Windows Update policies ensures timely patching of security flaws, disrupting attacker persistence, and reducing the risk of widespread compromise.

**Remediation action**

Start with [Manage Windows software updates in Intune](/en-us/intune/device-updates/windows/configure) to understand the available Windows Update policy types and how to configure them.

Intune includes the following Windows update policy type:

- [Windows quality updates policy](/en-us/intune/device-updates/windows/manage-quality-updates) - *to install the regular monthly updates for Windows.*
- [Expedite updates policy](/en-us/intune/device-updates/windows/expedite-updates) - *to quickly install critical security patches.*
- [Feature updates policy](/en-us/intune/device-updates/windows/manage-feature-updates)
- [Update rings policy](/en-us/intune/device-updates/windows/manage-update-rings) - *to manage how and when devices install feature and quality updates.*
- [Windows driver updates](/en-us/intune/device-updates/windows/manage-driver-updates) - *to update hardware components.*

### Security baselines are applied to Windows devices to strengthen security posture

Without properly configured and assigned Intune security baselines for Windows, devices remain vulnerable to a wide array of attack vectors that threat actors exploit to gain persistence and escalate privileges. Adversaries leverage default Windows configurations that lack hardened security settings to perform lateral movement using techniques like credential dumping, privilege escalation via unpatched vulnerabilities, and exploitation of weak authentication mechanisms. In the absence of enforced security baselines, threat actors can bypass critical security controls, maintain persistence through registry modifications, and exfiltrate sensitive data through unmonitored channels. Failing to implement a defense-in-depth strategy makes devices easier to exploit as attackers progress through the attack chain—from initial access to data exfiltration—ultimately compromising the organization’s security posture and increasing the risk of compliance violations.

Applying security baselines ensures Windows devices are configured with hardened settings, reducing attack surface, enforcing defense-in-depth, and supporting Zero Trust by standardizing security controls across the environment.

**Remediation action**

Configure and assign Intune security baselines to Windows devices to enforce standardized security settings and monitor compliance:

- [Deploy security baselines to help secure Windows devices](/en-us/intune/device-security/security-baselines/configure-baselines#create-a-profile-for-a-security-baseline)
- [Monitor security baseline compliance](/en-us/intune/device-security/security-baselines/monitor-baselines)

### Update policies for macOS are enforced to reduce risk from unpatched vulnerabilities

If macOS update policies aren’t properly configured and assigned, threat actors can exploit unpatched vulnerabilities in macOS devices within the organization. Without enforced update policies, devices remain on outdated software versions, increasing the attack surface for privilege escalation, remote code execution, or persistence techniques. Threat actors can leverage these weaknesses to gain initial access, escalate privileges, and move laterally within the environment. If policies exist but aren’t assigned to device groups, endpoints remain unprotected, and compliance gaps go undetected. This can result in widespread compromise, data exfiltration, and operational disruption.

Enforcing macOS update policies ensures devices receive timely patches, reducing the risk of exploitation and supporting Zero Trust by maintaining a secure, compliant device fleet.

**Remediation action**

Configure and assign macOS update policies in Intune to enforce timely patching and reduce risk from unpatched vulnerabilities:

- [Manage macOS software updates in Intune](/en-us/intune/device-updates/apple/deprecated-mdm-policies-macos)

### Update policies for iOS/iPadOS are enforced to reduce risk from unpatched vulnerabilities

If iOS update policies aren’t configured and assigned, threat actors can exploit unpatched vulnerabilities in outdated operating systems on managed devices. The absence of enforced update policies allows attackers to use known exploits to gain initial access, escalate privileges, and move laterally within the environment. Without timely updates, devices remain susceptible to exploits that have already been addressed by Apple, enabling threat actors to bypass security controls, deploy malware, or exfiltrate sensitive data. This attack chain begins with device compromise through an unpatched vulnerability, followed by persistence and potential data breach that impacts both organizational security and compliance posture.

Enforcing update policies disrupts this chain by ensuring devices are consistently protected against known threats.

**Remediation action**

Configure and assign iOS/iPadOS update policies in Intune to enforce timely patching and reduce risk from unpatched vulnerabilities:

- [Manage iOS/iPadOS software updates in Intune](/en-us/intune/device-updates/apple/planning-guide-ios-ipados)
- [Assign policies in Intune](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups)