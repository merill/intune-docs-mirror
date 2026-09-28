---
layout: Conceptual
title: Configure compliance policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/deploy-compliance-step-3
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Description for configuring compliance policies
ms.date: 2023-11-22T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 29ce4c2d-3a4c-81b2-a920-d42bbd18b66d
document_version_independent_id: 29ce4c2d-3a4c-81b2-a920-d42bbd18b66d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/deploy-compliance-step-3.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/deploy-compliance-step-3
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/deploy-compliance-step-3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d6911c2b-af34-4265-384c-c04991c68b50
---

# Configure compliance policies - Microsoft Intune | Microsoft Learn

Previously, you set up your Intune subscription and created app protection policies. Next, plan for and configure device compliance settings and policies to help protect organizational data by requiring devices to meet requirements that you set.

![Diagram that shows getting started with Microsoft Intune with step 3, which is creating compliance and Conditional Access policies.](media/deploy-compliance-step-3/deployment-plan-compliance-conditional-access.png)

If you're not yet familiar with compliance policies, see [Compliance overview](../device-security/compliance/overview).

This article applies to:

- Android Enterprise (Fully Managed, and Personally owned work profiles)
- Android Open-Source Project (AOSP)
- iOS/iPadOS
- Linux
- macOS
- Windows

You deploy compliance policies to groups of devices or users. When deployed to users, any device the user signs into must then meet the policies requirements. Some common examples of compliance requirements include:

- Requiring a minimum operating system version.
- Use of a password or PIN that meets certain complexity and length requirements.
- A device being at or below a *threat level* as determined by mobile threat defense software you use. Mobile threat defense software includes Microsoft Defender for Endpoint or one of Intune's other supported partners.

When devices fail to meet the requirements of a compliance policy, that policy can apply one or more *actions for noncompliance*. Some actions include:

- Remotely locking the noncompliant device.
- Send email or notifications to the device or user about the compliance issue, so a device user can bring it back into compliance.
- Identify a device that might be ready for retirement should it remain out of compliance for an extended time. When you're planning for and deploying your compliance policies, it can help to approach compliance policies through our recommendations through different levels. We recommend starting with the minimal compliance settings, which are common to most or all platforms, and then expanding by adding more advanced configurations and integrations that provide more capabilities.

Because different device platforms support different compliance capabilities or use different names for similar settings, listing each option is beyond this deployment plan. Instead, we provide categories and examples of settings in those categories for each of the following levels:

- **Level 1** – **Minimal device compliance**. This category includes configurations that we recommend all tenants have in place.
- **Level 2** – **Enhanced device compliance settings**. These include common device configurations such as encryption, or system level file protections.
- **Level 3** – **Advanced device compliance configurations**. High level recommendations include configurations that require deeper integration with other products, such as Microsoft Entra Conditional Access.

Generally, our recommendations place settings that are considered key configurations that are common across platforms at the minimal compliance level, providing a strong return for your investment. Settings listed for at higher levels can involve more complexity, such as settings that require integration of third-party products. Be sure to review all the range recommendations and be ready to adjust your own deployment plan to fit your organization's needs and expectations.

The following articles can help you understand the settings that Intune policies natively support:

- [Android device administrator](../device-security/compliance/ref-android-administrator-settings)
- [Android Enterprise](../device-security/compliance/ref-android-enterprise-settings)
- [Android Open-Source Project (AOSP)](../device-security/compliance/ref-android-aosp-settings)
- [iOS](../device-security/compliance/ref-ios-ipados-settings)
- [macOS](../device-security/compliance/ref-macos-settings)
- [Windows](../device-security/compliance/ref-windows-settings)

## Level 1 - Minimal device compliance

![](../media/icons/16/check.svg)**Configure tenant-wide Compliance policy settings**![](../media/icons/16/check.svg)**Set up responses for noncompliance devices (Actions for noncompliance)**![](../media/icons/16/check.svg)**Understand how device compliance and device configuration policies interact**![](../media/icons/16/check.svg)**Use a core set of minimal compliance settings across platforms you support**

The minimal device compliance settings include the following subjects that all tenants who plan to use compliance policies should understand and be prepared to use:

- *Compliance policy settings* – Tenant-wide settings that affect how the Intune compliance service works with your devices.
- *Actions for noncompliance* – These configurations are common to all device compliance policies.
- *Minimal device compliance policy recommendations* – This category includes the platform specific device compliance settings we believe every tenant should implement to help keep their organizations resources safe.

In addition, we recommend you be familiar with how device compliance policies and device configuration policies are related and interact.

### Compliance policy settings

All organizations should review and set the tenant-wide *compliance policy settings*. These settings are foundational to supporting platform specific policies. They can also mark devices that haven't evaluated a compliance policy as noncompliant, which can help you protect your organization from new or unknown devices that might fail to meet your security expectations.

- Compliance policy settings are a few configurations you make at the tenant-level that then apply to all devices. They establish how the Intune compliance service functions for your tenant.
- These settings are configured directly in the Microsoft Intune admin center and are distinct from device compliance policies that you create for specific platforms and deploy to discreet groups of devices or users.

To learn more about Compliance Policy Settings at the tenant level, and how to configure them, see [Compliance policy settings](../device-security/compliance/overview#compliance-policy-settings).

### Actions for noncompliance

Each device compliance policy includes *actions for noncompliance*, which are one or more time-ordered actions that are applied to devices that fail to meet the compliance requirements of the policy. By default, marking a device as noncompliant is an immediate action that's included in each policy.

For each action you add, you define how long to wait after a device is marked as noncompliant before that action runs.

Available actions you can configure include the following, but not all are available for each device platform:

- **Mark device non-compliant** (default action for all policies)
- **Send push notification to end user**
- **Send email to end user**
- **Remotely lock the noncompliant device**
- **Retire the noncompliant device**

Policy administrators should understand the available options for each action and complete supporting configurations before deploying a policy that requires them. For example, before you can add the *send email* action, you must first create one or more email templates with the messages you might want to send. Such an email might include resources to help the user bring their device into compliance. Later, when defining an email action for a policy you can select one of your templates to use with a specific action.

Because each non-default action can be added to a policy multiple times, each with a separate configuration, you can customize how the actions apply.

For example, you could configure several related actions to occur in a sequence. First, immediately upon being noncompliant you might have Intune send an email to the device's user, and perhaps an administrator as well. Then a few days later, a second action could send a different email reminder, with details about a deadline for remediating the device. You might also configure a final action to add a device to a list of devices you might want to retire, with the action set to run only after a device continues to remain noncompliant for an excessive period.

While compliance policy can mark a device as noncompliant, you also need a plan for how to remediate noncompliant devices. This plan could include admins using noncompliant device status to request updates or configurations be made to a device. To provide general guidance to device users, you can configure the *send email to end user* action for noncompliance to include useful tips or contacts for resolving a device compliance issue.

To learn more, see [Actions for noncompliance](../device-security/compliance/configure-noncompliance-actions).

### Understand how device compliance and device configuration policies interact

Before diving into compliance policy recommendations by levels, it's important to understand the sometimes-close relationship between compliance policies and device configuration policies. With awareness of these interactions, you can better plan for and deploy successful policies for both feature areas.

- Device configuration policies configure devices to use specific configurations. These settings can range across all aspects of the device.
- Device compliance policies focus on a subset of device configurations that are related to security.

Devices that receive compliance policies are evaluated against the compliance policy configurations with results returned to Intune for possible actions. Some compliance configurations like password requirements result in enforcement on the device, even when device configurations are more lenient.

When a device receives conflicting configurations for a setting either different or similar policy types, conflicts can occur. To help prepare for this scenario, see [Compliance and device configuration policies that conflict](../device-configuration/troubleshoot-device-profiles#compliance-and-device-configuration-policies-that-conflict)

Consider synchronizing any planned configurations between device configuration and device compliance teams to help identify configuration overlaps. Ensure the two policy types agree on the same configuration for targeted devices as this can help avoid policy conflicts or leaving a device without the configuration or resource access you expect.

### Minimal compliance settings

After you establish tenant-wide compliance policy settings and establish communications or rules for actions for noncompliant devices, you're likely ready to create and deploy device compliance policies to discrete groups of devices or users.

Review the platform specific policies in the Microsoft Intune admin center to identify which compliance settings are available for each platform and more details about their use. To configure policies, see [Create a compliance policy](../device-security/compliance/create-policy).

We recommend using the following settings in your minimal device compliance policies:

| Minimal device compliance categories and examples | Information |
| --- | --- |
| **Antivirus**, **Antispyware**, and **Antimalware** **Windows**:  Evaluate devices for solutions that register with Windows Security Center to be on and monitoring for: - Antivirus - Antispyware - Microsoft Defender Antimalware **Other platforms**:  Compliance policies for platforms other than Windows don't include evaluation for these solutions. | Active solutions for Antivirus, Antispyware, and Antimalware solutions are important. Windows compliance policy can assess the state of these solutions when they're active and registered register with Windows Security Center on a device. Non-Windows platforms should still run solutions for antivirus, antispyware, and antimalware, even though Intune compliance policies lack options to evaluate their active presence. |
| **Operating System versions** **All devices**:  Evaluate settings and values for operating system versions, including:  - Maximum OS  - Minimum OS - Minor and Major build versions - OS patch levels | Use available settings that define a minimum allowed OS version or build and important patch levels to ensure device operating systems are current and secure.  Maximum OS settings can help identify new but untested results, and beta or developer OS builds that could introduce unknown risks.  Linux supports an option to define the Linux distribution type, like Ubuntu.  Windows supports another setting to set supported build ranges. |
| **Password configurations** **All devices**: - Enforce settings that lock the screen after a period of inactivity, requiring a password or PIN to unlock.  - Require complex passwords that use combinations of letters, numbers, and symbols. - Require a password or Pin to unlock devices.  - Set requirements for a minimum password length. | Use compliance to evaluate devices for password structure and length, and to identify devices that lack passwords or use simple passwords. These settings can help protect access to the device.  Other options like password reuse or length of time before a password must be changed are explicitly included at the enhanced compliance level. |

## Level 2 - Enhanced device compliance settings

![](../media/icons/16/check.svg)**Use enhanced device configuration policies for supported platform types**

### Enhanced compliance settings

Support for enhanced level compliance settings varies greatly by platform as compared to the settings found in the minimal recommendations. Some platforms might not support settings that are supported by related platforms. For example, Android AOSP lacks options that exist for Android Enterprise platforms to configure compliance for system level file and boot protections.

Review the platform specific policies in the Microsoft Intune admin center to identify which compliance settings are available for each platform and more details about their use. To configure policies, see [Create a compliance policy](../device-security/compliance/create-policy).

We recommend using the following settings in your enhanced device compliance policies:

| Enhanced device compliance categories and examples | Information |
| --- | --- |
| **Applications** **Android Enterprise**: - Block apps from unknown sources - Company Portal app runtime integrity  - Manage source locations for apps  - Google Play services  - SafteyNet options for attestation and evaluation **iOS/iPadOS** - Restricted apps**macOS**: - Allow apps from specific locations - Block apps from unknown sources - Firewall settings**Windows**: - Block apps from unknown sources - Firewall settings | Configure requirements for various applications.  For Android, manage the use and operation of applications like Google Play, SafteyNet, and evaluation of the Company Portal app runtime integrity.  For all platforms, when supported, manage where apps can be installed from, and which apps shouldn't be allowed on devices that access your organizations resources.  For macOS and Windows, compliance settings support requiring an active and configured Firewall. |
| **Encryption** **Android Enterprise**: - Require encryption of data storage**Android AOSP**: - Require encryption of data storage**macOS**: - Require encryption of data storage**Linux**:  - Require encryption of data storage**Windows**: - Require encryption of data storage - BitLocker | Add compliance settings that require the encryption of data storage. Windows also supports requiring use of BitLocker. |
| **Password configurations** **Android Enterprise**: - Password expiration, and reuse**iOS/iPadOS**:  - Password expiration, and reuse**macOS**:  - Password expiration, and reuse**Windows**: - Password expiration, and reuse | Add password compliance settings to ensure passwords are rotated periodically, and that passwords aren't reused frequently. |
| **System level file and boot protection** **Android AOSP**: - Rooted devices **Android Enterprise**:  - Block USB debugging on device - Rooted devices **iOS/iPadOS** - Jailbroken devices**macOS**: - Require system integrity protection **Windows**: - Require code integrity - Require Secure Boot to be enabled on the device - Trusted Platform Module (TPM) | Configure the platform specific options that evaluate devices for system level or kernel level risks. |

## Level 3 - Advanced device compliance configurations

![](../media/icons/16/check.svg)**Add data from Mobile Threat Defense partners to your device compliance policies**![](../media/icons/16/check.svg)**Integrate a third-party compliance partner with Intune**![](../media/icons/16/check.svg)**Define custom compliance settings for Windows and Linux**![](../media/icons/16/check.svg)**Use compliance data with Conditional Access to gate access to your organization's resources**![](../media/icons/16/check.svg)**Use advanced device configuration policies for supported platform types**

With robust device compliance policies in place, you can then implement more advanced compliance options that go beyond only configuring settings in device compliance policies, including:

- Using data from *Mobile Threat Defense partners* as part of your device compliance policies, and in your Conditional Access policies.
- Integrating device compliance status with *Conditional Access* to help gate which devices are allowed to access email, other cloud services, or on-premises resources.
- Including compliance data from *third-party compliance partners*. With such a configuration, compliance data from those devices can be used with your [Conditional Access policies](../device-security/compliance/overview#integrate-with-conditional-access).
- Expanding on built-in device compliance policies by defining custom compliance settings that aren't available natively through the Intune compliance policy UI.

### Integrate data from a Mobile Threat Defense partner

A Mobile Threat Defense (MTD) solution is software for mobile devices that helps to secure them from various cyber threats. By protecting mobile devices, you help protect your organization and resources. When integrated, MTD solutions provide an additional information source to Intune for your device compliance policies. This information can also be used by Conditional Access rules you can use with Intune.

When integrated, Intune supports use of MTD solutions with enrolled devices, and when supported by the MTD solution, unenrolled devices by using [Microsoft Intune protected apps](../app-management/ref-protected-apps) and app protection policies.

Be sure to use an MTD partner that is [supported by Intune](../device-security/mobile-threat-defense/overview#mobile-threat-defense-partners) and that supports the capabilities your organization needs on the full range of platforms you use.

For example, [Microsoft Defender for Endpoint](../device-security/microsoft-defender/overview) is a Mobile Threat Defense solution you might already use that can be used with the Android, iOS/iPadOS, and Windows platforms. Other solutions, typically support Android and iOS/iPadOS. See [Mobile Threat Defense partners](../device-security/mobile-threat-defense/overview) to view the list of supported MTD partners.

To learn more about using Mobile Threat Defense software with Intune, start with [Mobile Threat Defense integration with Intune](../device-security/mobile-threat-defense/overview).

### Use data from third-party compliance partners

Intune supports the use of third-party compliance partners where the partner serves as the mobile device management (MDM) authority for a group of devices. When you use a supported compliance partner, you use that partner to configure device compliance for the devices that solution manages. You also configure that partner solution to pass the compliance results to Intune, which then stores that data in Microsoft Entra ID along with compliance data from Intune. The third-party compliance data is then available for use by Intune when evaluating device compliance policies, and for use by Conditional Access policies.

In some environments, Intune might serve as the only MDM authority you need to use, as by default, Intune is a registered compliance partner for the Android, iOS/iPadOS, and Windows platforms. Other platforms require other compliance partners to serve as a devices MDM authority, like use of Jamf Pro for macOS devices.

If you use a third-party device compliance partner in your environment, ensure they're [supported with Intune](../device-security/compliance/third-party-partners#supported-device-compliance-partners). To add support, you configure a [connection for the partner](../device-security/compliance/third-party-partners#configure-intune-to-work-with-a-device-compliance-partner) from within the Microsoft Intune admin center, and follow that partners documentation to complete the integration.

For more information on this subject, see [Support third-party device compliance partners in Intune](../device-security/compliance/third-party-partners).

### Use custom compliance settings

You can expand on Intune's built-in device compliance options by configuring custom compliance settings for managed Linux and Windows devices.

Custom settings give you the flexibility to base compliance on the settings that are available on a device without having to wait for Intune to add these settings.

To use custom compliance, you must configure a .JSON file that defines values on the device to use for compliance, and a discovery script that runs on the device to evaluate the settings from the JSON.

To learn more about perquisites, supported platforms, and the JSON and script configurations required for custom compliance, see [Use custom compliance policies and settings for Linux and Windows devices with Microsoft Intune](../ protect/compliance-use-custom-settings.md).

### Integrate compliance with Conditional Access

Conditional Access is a Microsoft Entra capability that works with Intune to help protect devices. For devices that register with Microsoft Entra, Conditional Access policies can use device and compliance details from Intune to enforce access decisions for users and devices.

Combine Conditional Access policy with:

- [Device compliance policies](/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) can require a device be marked as compliant before that device can be used to access your organization's resources. The Conditional Access policies specify apps services you want to protect, conditions under which the apps or services can be accessed, and the users the policy applies to.
- [App protection policies](../device-security/conditional-access-integration/app-based-policies) can add a security layer that ensures only client apps that support Intune app protection policies can access your online resources, like Exchange or other Microsoft 365 services.

Conditional Access also works with the following to help you keep devices secure:

- Microsoft Defender for Endpoint and third-party MTD apps
- Device compliance partner apps
- Microsoft Tunnel

To learn more, see [Learn about Conditional Access and Intune](../device-security/conditional-access-integration/overview).

### Advanced compliance settings

Review the platform specific policies in the Microsoft Intune admin center to identify which compliance settings are available for each platform and more details about their use. To configure policies, see [Create a compliance policy](../device-security/compliance/create-policy).

To configure policies, see [Create a compliance policy](../device-security/compliance/create-policy).

We recommend using the following settings in your enhanced device compliance policies:

| Advanced device compliance categories and examples | Information |
| --- | --- |
| **Runtime defenses** **Android Enterprise**:  - Require the device to be at or under the Device Threat Level  - Require the device to be at or under the machine risk score **iOS/iPadOS**: - Require the device to be at or under the Device Threat Level  - Require the device to be at or under the machine risk score**Windows**:  - Require the device to be at or under the machine risk score | When you integrate Intune with a Mobile Threat Defense partner, you can use that partners device threat level evaluation as criteria in your compliance policies.  When you've integrated Microsoft Defender for Endpoint with Intune, you can use the risk score from Defender as a compliance check. |

## Follow the minimum recommended baseline policies

This article is part of a five-step series that describes how to deploy Microsoft Intune. The series includes the following articles, in order:

1. [Set up Microsoft Intune](deploy-setup-step-1)
2. [Add, configure, and protect apps](deploy-protect-apps-step-2)
3. 🡺 **Plan for compliance policies** (this article)
4. [Configure device features](deploy-configuration-step-4)
5. [Enroll devices](../device-enrollment/enroll-devices)