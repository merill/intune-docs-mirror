---
layout: Conceptual
title: Configure Microsoft Intune for increased tenant security - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/ref-zero-trust-tenant
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: Secure your tenant with Microsoft Intune to support your Zero Trust journey.
ms.topic: reference
ms.date: 2025-10-20T00:00:00.0000000Z
ms.reviewer: ramical
ms.collection:
- tier 1
- M365-identity-device-management
locale: en-us
document_id: 54b03070-dc22-11a5-6a68-9feada1eea08
document_version_independent_id: 54b03070-dc22-11a5-6a68-9feada1eea08
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/ref-zero-trust-tenant.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/ref-zero-trust-tenant
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/ref-zero-trust-tenant.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c196856f-180b-ba44-178a-f8c564921b45
---

# Configure Microsoft Intune for increased tenant security - Microsoft Intune | Microsoft Learn

Protecting your Intune tenant is essential to enforcing Zero Trust principles and maintaining a secure, well-managed environment. These recommendations align with Microsoft's [Secure Future Initiative](https://www.microsoft.com/trust-center/security/secure-future-initiative?msockid=2bad2df65a416adb0e5838355b3e6b95#SFI-pillars) by limiting blast radius and enforcing least-privilege access through segmented administrative control, secure device onboarding, and policy-driven protections. Together, they help reduce risk, maintain tenant hygiene, and strengthen compliance across platforms.

## Zero Trust security recommendations

### Scope tag configuration is enforced to support delegated administration and least-privilege access

If Intune scope tags aren't properly configured for delegated administration, attackers who gain privileged access to Intune or Microsoft Entra ID can escalate privileges and access sensitive device configurations across the tenant. Without granular scope tags, administrative boundaries are unclear, allowing attackers to move laterally, manipulate device policies, exfiltrate configuration data, or deploy malicious settings to all users and devices. A single compromised admin account can impact the entire environment. The absence of delegated administration also undermines least-privileged access, making it difficult to contain breaches and enforce accountability. Attackers might exploit global administrator roles or misconfigured role-based access control (RBAC) assignments to bypass compliance policies and gain broad control over device management.

Enforcing scope tags segments administrative access and aligns it with organizational boundaries. This limits the blast radius of compromised accounts, supports least-privilege access, and aligns with Zero Trust principles of segmentation, role-based control, and containment.

**Remediation action**

Use Intune scope tags and RBAC roles to limit admin access based on role, geography, or business unit:

- [Learn how to create and deploy scope tags for distributed IT](/en-us/intune/fundamentals/role-based-access-control/scope-tags)
- [Implement role-based access control with Microsoft Intune](/en-us/intune/fundamentals/role-based-access-control/overview)

### Device enrollment notifications are enforced to ensure user awareness and secure onboarding

Without device enrollment notifications, users might be unaware that their device has been enrolled in Intune—particularly in cases of unauthorized or unexpected enrollment. This lack of visibility can delay user reporting of suspicious activity and increase the risk of unmanaged or compromised devices gaining access to corporate resources. Attackers who obtain user credentials or exploit self-enrollment flows can silently onboard devices, bypassing user scrutiny and enabling data exposure or lateral movement.

Enrollment notifications provide users with improved visibility into device onboarding activity. They help detect unauthorized enrollment, reinforce secure provisioning practices, and support Zero Trust principles of visibility, verification, and user engagement.

**Remediation action**

Configure Intune enrollment notifications to alert users when their device is enrolled and reinforce secure onboarding practices:

- [Set up enrollment notifications in Intune](/en-us/intune/device-enrollment/setup-notifications)

### Windows automatic device enrollment is enforced to eliminate risks from unmanaged endpoints

If Windows automatic enrollment isn't enabled, unmanaged devices can become an entry point for attackers. Threat actors might use these devices to access corporate data, bypass compliance policies, and introduce vulnerabilities into the environment. Devices joined to Microsoft Entra without Intune enrollment create gaps in visibility and control. These unmanaged endpoints can expose weaknesses in the operating system or misconfigured applications that attackers can exploit.

Enforcing automatic enrollment ensures Windows devices are managed from the start, enabling consistent policy enforcement and visibility into compliance. This supports Zero Trust by ensuring all devices are verified, monitored, and governed by security controls.

**Remediation action**

Enable automatic enrollment for Windows devices using Intune and Microsoft Entra to ensure all domain-joined or Entra-joined devices are managed:

- [Enable Windows automatic enrollment](/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment)

For more information, see:

- [Deployment guide - Enrollment for Windows](/en-us/intune/device-enrollment/enroll-devices?tabs=work-profile%2Ccorporate-owned-apple%2Cautomatic-enrollment#enrollment-for-windows)

### Compliance policies protect Windows devices

If compliance policies for Windows devices aren't configured and assigned, threat actors can exploit unmanaged or noncompliant endpoints to gain unauthorized access to corporate resources, bypass security controls, and persist within the environment. Without enforced compliance, devices can lack critical security configurations like BitLocker encryption, password requirements, firewall settings, and OS version controls. These gaps increase the risk of data leakage, privilege escalation, and lateral movement. Inconsistent device compliance weakens the organization’s security posture and makes it harder to detect and remediate threats before significant damage occurs.

Enforcing compliance policies ensures Windows devices meet core security requirements and supports Zero Trust by validating device health and reducing exposure to misconfigured endpoints.

**Remediation action**

Create and assign Intune compliance policies to Windows devices to enforce organizational standards for secure access and management:

- [Create and assign Intune compliance policies](/en-us/intune/device-security/compliance/create-policy#create-the-policy)
- [Review the Windows compliance settings you can manage with Intune](/en-us/intune/device-security/compliance/ref-windows-settings)

### Compliance policies protect macOS devices

If compliance policies for macOS devices aren't configured and assigned, threat actors can exploit unmanaged or noncompliant endpoints to gain unauthorized access to corporate resources, bypass security controls, and persist within the environment. Without enforced compliance, macOS devices can lack critical security configurations like data storage encryption, password requirements, and OS version controls. These gaps increase the risk of data leakage, privilege escalation, and lateral movement. Inconsistent device compliance weakens the organization’s security posture and makes it harder to detect and remediate threats before significant damage occurs.

Enforcing compliance policies ensures macOS devices meet core security requirements and supports Zero Trust by validating device health and reducing exposure to misconfigured endpoints.

**Remediation actions**

Create and assign Intune compliance policies to macOS devices to enforce organizational standards for secure access and management:

- [Create and assign Intune compliance policies](/en-us/intune/device-security/compliance/create-policy#create-the-policy)
- [Review the macOS compliance settings you can manage with Intune](/en-us/intune/device-security/compliance/ref-macos-settings)

### Compliance policies protect fully managed and corporate-owned Android devices

If compliance policies aren't assigned to fully managed Android Enterprise devices in Intune, threat actors can exploit noncompliant endpoints to gain unauthorized access to corporate resources, bypass security controls, and persist in the environment. Without enforced compliance, devices can lack critical security configurations such as passcode requirements, data storage encryption, and OS version controls. These gaps increase the risk of data leakage, privilege escalation, and lateral movement. Inconsistent device compliance weakens the organization’s security posture and makes it harder to detect and remediate threats before significant damage occurs.

Enforcing compliance policies ensures Android Enterprise devices meet core security requirements and supports Zero Trust by validating device health and reducing exposure to misconfigured or unmanaged endpoints.

**Remediation action**

Create and assign Intune compliance policies to fully managed and corporate-owned Android Enterprise devices to enforce organizational standards for secure access and management:

- [Create a compliance policy in Microsoft Intune](/en-us/intune/device-security/compliance/create-policy#create-the-policy)
- [Review the Android Enterprise compliance settings you can manage with Intune](/en-us/intune/device-security/compliance/ref-android-enterprise-settings)

### Compliance policies protect personally owned Android devices

If compliance policies aren't assigned to Android Enterprise personally owned devices in Intune, threat actors can exploit noncompliant endpoints to gain unauthorized access to corporate resources, bypass security controls, and introduce vulnerabilities. Without enforced compliance, devices can lack critical security configurations like passcode requirements, data storage encryption, and OS version controls. These gaps increase the risk of data leakage and unauthorized access. Inconsistent device compliance weakens the organization’s security posture and makes it harder to detect and remediate threats before significant damage occurs.

Enforcing compliance policies ensures that personally owned Android devices meet core security requirements and supports Zero Trust by validating device health and reducing exposure to misconfigured or unmanaged endpoints.

**Remediation action**

Create and assign Intune compliance policies to Android Enterprise personally owned devices to enforce organizational standards for secure access and management:

- [Create a compliance policy in Microsoft Intune](/en-us/intune/device-security/compliance/create-policy#create-the-policy)
- [Review the Android Enterprise compliance settings you can manage with Intune](/en-us/intune/device-security/compliance/ref-android-enterprise-settings)

### Compliance policies protect iOS/iPadOS devices

If compliance policies aren't assigned to iOS/iPadOS devices in Intune, threat actors can exploit noncompliant endpoints to gain unauthorized access to corporate resources, bypass security controls, and persist in the environment. Without enforced compliance, devices can lack critical security configurations like passcode requirements and OS version controls. These gaps increase the risk of data leakage, privilege escalation, and lateral movement. Inconsistent device compliance weakens the organization’s security posture and makes it harder to detect and remediate threats before significant damage occurs.

Enforcing compliance policies ensures iOS/iPadOS devices meet core security requirements and supports Zero Trust by validating device health and reducing exposure to misconfigured or unmanaged endpoints.

**Remediation action**

Create and assign Intune compliance policies to iOS/iPadOS devices to enforce organizational standards for secure access and management:

- [Create a compliance policy in Microsoft Intune](/en-us/intune/device-security/compliance/create-policy#create-the-policy)
- [Review the iOS/iPadOS compliance settings you can manage with Intune](/en-us/intune/device-security/compliance/ref-ios-ipados-settings)

### Platform SSO is configured to strengthen authentication on macOS devices

If Platform SSO policies aren't enforced on macOS devices, endpoints might rely on insecure or inconsistent authentication mechanisms, allowing attackers to bypass Conditional Access and compliance policies. This opens the door to lateral movement across cloud services and on-premises resources, especially when federated identities are used. Threat actors can persist by leveraging stolen tokens or cached credentials and exfiltrate sensitive data through unmanaged apps or browser sessions. The absence of SSO enforcement also undermines app protection policies and device posture assessments, making it difficult to detect and contain breaches. Ultimately, failure to configure and assign macOS Platform SSO policies compromises identity security and weakens the organization's Zero Trust posture.

Enforcing Platform SSO policies on macOS devices ensures consistent, secure authentication across apps and services. This strengthens identity protection, supports Conditional Access enforcement, and aligns with Zero Trust by reducing reliance on local credentials and improving posture assessments.

**Remediation action**

Use Intune to configure and assign Platform SSO policies for macOS devices to enforce secure authentication and strengthen identity protection, see:

- [Configure Platform SSO for macOS in Intune](/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos) – *Step-by-step guidance for enabling Platform SSO on macOS devices.*
- [Single sign-on (SSO) overview and options for Apple devices in Microsoft Intune](/en-us/intune/device-configuration/enterprise-sso-plugin?pivots=macos) – *Overview of SSO options available for Apple platforms.*

### Defender for Endpoint automatic enrollment is enforced to reduce risk from unmanaged Android threats

If automatic enrollment into Microsoft Defender for Endpoint isn't configured for Android devices in Intune, managed endpoints might remain unprotected against mobile threats. Without Defender onboarding, devices lack advanced threat detection and response capabilities, increasing the risk of malware, phishing, and other mobile-based attacks. Unprotected devices can bypass security policies, access corporate resources, and expose sensitive data to compromise. This gap in mobile threat defense weakens the organization's Zero Trust posture and reduces visibility into endpoint health.

Enabling automatic Defender enrollment ensures Android devices are protected by advanced threat detection and response capabilities. This supports Zero Trust by enforcing mobile threat protection, improving visibility, and reducing exposure to unmanaged or compromised endpoints.

**Remediation action**

Use Intune to configure automatic enrollment into Microsoft Defender for Endpoint for Android devices to enforce mobile threat protection:

- [Integrate Microsoft Defender for Endpoint with Intune and Onboard Devices](/en-us/intune/device-security/microsoft-defender/configure-integration)

### Device cleanup rules maintain tenant hygiene by hiding inactive devices

If device cleanup rules aren't configured in Intune, stale or inactive devices can remain visible in the tenant indefinitely. This leads to cluttered device lists, inaccurate reporting, and reduced visibility into the active device landscape. Unused devices might retain access credentials or tokens, increasing the risk of unauthorized access or misinformed policy decisions.

Device cleanup rules automatically hide inactive devices from admin views and reports, improving tenant hygiene and reducing administrative burden. This supports Zero Trust by maintaining an accurate and trustworthy device inventory while preserving historical data for audit or investigation.

**Remediation action**

Configure Intune device cleanup rules to automatically hide inactive devices from the tenant:

- [Create a device cleanup rule](/en-us/intune/governance/configure-cleanup-rules#how-to-create-a-device-cleanup-rule)

For more information, see:

- [Using Intune device cleanup rules](https://techcommunity.microsoft.com/blog/devicemanagementmicrosoft/using-intune-device-cleanup-rules-updated-version/3760854)*on the Microsoft Tech Community blog*

### Terms and Conditions policies protect access to sensitive data

If Terms and Conditions policies aren't configured and assigned in Intune, users can access corporate resources without agreeing to required legal, security, or usage terms. This omission exposes the organization to compliance risks, legal liabilities, and potential misuse of resources.

Enforcing Terms and Conditions ensures users acknowledge and accept company policies before accessing sensitive data or systems, supporting regulatory compliance and responsible resource use.

**Remediation action**

Create and assign Terms and Conditions policies in Intune to require user acceptance before granting access to corporate resources:

- [Create terms and conditions policy](/en-us/intune/device-enrollment/create-terms-and-conditions)

### Company Portal branding and support settings enhance user experience and trust

If the Intune Company Portal branding isn't configured to represent your organization’s details, users can encounter a generic interface and lack direct support information. This reduces user trust, increases support overhead, and can lead to confusion or delays in resolving issues.

Customizing the Company Portal with your organization’s branding and support contact details improves user trust, streamlines support, and reinforces the legitimacy of device management communications.

**Remediation action**

Configure the Intune Company Portal with your organization’s branding and support contact information to enhance user experience and reduce support overhead:

- [Configure the Intune Company Portal](/en-us/intune/app-management/configuration/configure-company-portal)

### Endpoint Analytics is enabled to help identify risks on Windows devices

If endpoint analytics isn't enabled, threat actors can exploit gaps in device health, performance, and security posture. Without the visibility endpoint analytics brings, it can be difficult for an organization to detect indicators such as anomalous device behavior, delayed patching, or configuration drift. These gaps allow attackers to establish persistence, escalate privileges, and move laterally across the environment. An absence of analytics data can impede rapid detection and response, allowing attackers to exploit unmonitored endpoints for command and control, data exfiltration, or further compromise.

Enabling endpoint analytics provides visibility into device health and behavior, helping organizations detect risks, respond quickly to threats, and maintain a strong Zero Trust posture.

**Remediation action**

Enroll Windows devices into endpoint analytics in Intune to monitor device health and identify risks:

- [Configure endpoint analytics](/en-us/intune/endpoint-analytics/configure?pivots=intune)

For more information, see:

- [What is endpoint analytics?](/en-us/intune/endpoint-analytics/index)