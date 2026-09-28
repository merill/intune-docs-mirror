---
layout: Conceptual
title: Device compliance policies in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-device-compliance
ms.subservice: protect
description: Overview of Microsoft Intune device compliance, including tenant-wide compliance policy settings and device compliance policies.
ms.date: 2026-07-02T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: ilwu
ai-usage: ai-assisted
locale: en-us
document_id: a1a25388-1434-ecb8-a0de-249b1442433c
document_version_independent_id: a1a25388-1434-ecb8-a0de-249b1442433c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2cb9858d-879d-7c3d-d151-391adc750ccd
---

# Device compliance policies in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune compliance policies are sets of rules and conditions that you use to evaluate the configuration of your managed devices. These policies help you secure organizational data and resources from devices that don't meet those configuration requirements. Managed devices must satisfy the conditions you set in your policies to be considered compliant by Intune.

If you integrate the compliance results from your policies with Microsoft Entra Conditional Access, you can benefit from an extra layer of security. Conditional Access enforces Microsoft Entra access controls based on a device's current compliance status, helping ensure only compliant devices can access corporate resources.

Intune compliance policies are divided into two areas:

- Compliance policy settings are tenant-wide configurations that act like a built-in compliance policy that every device receives. Compliance policy settings establish how compliance policy works in your Intune environment, including how to treat devices that aren't assigned an explicit device compliance policy.
- Device compliance policies are discrete sets of platform-specific rules and settings you deploy to groups of users or devices. Devices evaluate the rules in the policy to report a device compliance status. A noncompliant status can result in one or more actions for noncompliance. Microsoft Entra Conditional Access policies can also use that status to block access to organizational resources from that device.

## Compliance policy settings

*Compliance policy settings* are tenant-wide settings that determine how Intune’s compliance service interacts with your devices. These settings are distinct from the settings you configure in a device compliance policy.

To manage the compliance policy settings, sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Endpoint security** &gt; **Device compliance** &gt; **Compliance policy settings**.

Compliance policy settings include:

- **Mark devices with no compliance policy assigned as**

    This setting determines how Intune treats devices that aren't assigned a device compliance policy. This setting has two values:

    - **Compliant** (*default*): This security feature is off. Devices that aren’t sent a device compliance policy are considered *compliant*.
    - **Not compliant**: This security feature is on. Devices without a device compliance policy are considered noncompliant.

    If you use Conditional Access with your device compliance policies, change this setting to **Not compliant** to ensure that only devices that are confirmed as compliant can access your resources.

    If an end user isn't compliant because a policy isn't assigned to them, the [Company Portal app](../../app-management/configuration/configure-company-portal) shows No compliance policies have been assigned.
- **Compliance status validity period (days)**

    Specify a period in which devices must successfully report on all their received compliance policies. If a device fails to report its compliance status for a policy before the validity period expires, the device is treated as noncompliant.

    By default, the period is set to 30 days. You can configure a period from 1 to 120 days.

    You can view details about a device's compliance with the validity period setting. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** &gt; **Monitor** &gt; **Setting compliance**. This setting has a name of **Is active** in the *Setting* column. For more information about this setting and related compliance status views, see [Monitor device compliance](monitor-policy).

## Device compliance policies

Intune device compliance policies are discrete sets of platform-specific rules and settings that you deploy to groups of users or devices. Use compliance policies to:

- Define the rules and settings that users and managed devices must meet to be compliant. Examples of rules include requiring devices run a minimum OS version, not being jailbroken or rooted, and being at or under a *threat level* as specified by threat management software that integrates with Intune.
- Support [actions for noncompliance](configure-noncompliance-actions) that apply to devices that don't meet the policy's compliance rules. Examples of actions for noncompliance include marking the device as noncompliant, being remotely locked, and sending a device user email about the device status so they can fix it.

When using device compliance policies:

- Some compliance policy configurations can override the configuration of settings that you also manage through device configuration policies. To learn more about conflict resolution for policies, see [Compliance and device configuration policies that conflict](../../device-configuration/troubleshoot-device-profiles#compliance-and-device-configuration-policies-that-conflict).
- You can deploy policies to users in user groups or devices in device groups. When you deploy a compliance policy to a user, Intune checks all the user's devices for compliance. Using device groups in this scenario helps with compliance reporting.
- If you use Microsoft Entra Conditional Access, your Conditional Access policies can use the device compliance results to block access to resources from noncompliant devices.
- Like other Intune policies, compliance policy evaluations for a device depend on when the device checks in with Intune, and [policy and profile refresh cycles](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals). For Windows devices, Intune also supports [client-driven compliance evaluation](create-policy#client-driven-compliance-evaluation-preview). With this capability, supported devices can proactively request compliance re-evaluation when local state changes are detected.

The available settings you can specify in a device compliance policy depend on the platform type you select when you create a policy. Different device platforms support different settings, and each platform type requires a separate policy.

The following topics link to dedicated articles for different aspects of device compliance policy.

- [**Actions for noncompliance**](configure-noncompliance-actions) - By default, each device compliance policy includes the action to mark a device as noncompliant if it fails to meet a policy rule. Each policy can support more actions based on the device platform. Examples of extra action include:

    - **Sending email alerts** to users and groups with details about the noncompliant device. You might configure the policy to send an email immediately upon being marked as noncompliant, and then again, periodically, until the device becomes compliant.
    - **Remotely lock devices** that are noncompliant for some time.
    - **Retire devices** after they're noncompliant for some time. This action marks a qualifying device as ready to be retired. An admin can then view a list of devices marked for retirement and must take an explicit action to retire one or more devices. Retiring a device removes the device from Intune management and removes all company data from the device. For more information about this action, see [Available actions for noncompliance](configure-noncompliance-actions#available-actions-for-noncompliance).
- [**Create a compliance policy**](create-policy) - With the information in the linked article, you can review prerequisites, work through the options to configure rules, specify actions for noncompliance, and assign the policy to groups. This article also includes information about policy refresh times.

    View the device compliance settings for the different device platforms:

    - [Android device administrator](ref-android-administrator-settings)
    - [Android Enterprise](ref-android-enterprise-settings)
    - [Android Open Source Project (AOSP)](ref-android-aosp-settings)
    - [iOS](ref-ios-ipados-settings)
    - [Linux](ref-linux-settings)
    - [macOS](ref-macos-settings)
    - [Windows Holographic for Business](ref-windows-settings#windows-holographic-for-business)
    - [Windows](ref-windows-settings)
    - [Windows 8.1 and later](ref-windows-8-1-settings)
        Important

        On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.
- [**Custom compliance settings**](custom-settings) - By using custom compliance settings, you can expand on Intune's built-in device compliance options. Custom settings provide flexibility to base compliance on the settings that are available on a device without having to wait for Intune to add those settings.

    You can use custom compliance settings with the following platforms:

    - Linux
        - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
        - RedHat Enterprise Linux 9 or 10
    - macOS
    - Windows

## Monitor compliance status

Intune includes a device compliance dashboard that you use to monitor the compliance status of devices, and to drill into policies and devices for more information. To learn more about this dashboard, see [Monitor device compliance](monitor-policy).

## Integrate with Conditional Access

When you use Conditional Access, you can configure your Conditional Access policies to use the results of your device compliance policies to determine which devices can access your organizational resources. This access control is in addition to and separate from the actions for noncompliance that you include in your device compliance policies.

When a device enrolls in Intune, it registers in Microsoft Entra ID. The compliance status for devices is reported to Microsoft Entra ID. If your Conditional Access policies have Access controls set to *Require device to be marked as compliant*, Conditional Access uses that compliance status to determine whether to grant or block access to email and other organization resources.

If you use device compliance status with Conditional Access policies, review how your tenant configures the *Mark devices with no compliance policy assigned as* option, which you manage under Compliance policy settings.

For more information about using Conditional Access with your device compliance policies, see [Device-based Conditional Access](../conditional-access-integration/scenarios#device-based-conditional-access).

Learn more about Conditional Access in the Microsoft Entra documentation:

- [What is Conditional Access](/en-us/entra/identity/conditional-access/overview)
- [What is a device identity](/en-us/entra/identity/devices/overview)

### Reference for noncompliance and Conditional Access on the different platforms

The following table describes how noncompliant settings are managed when you use a compliance policy with a Conditional Access policy.

- **Remediated**: The device operating system enforces compliance. For example, the user is forced to set a PIN.
- **Quarantined**: The device operating system doesn't enforce compliance. For example, Android and Android Enterprise devices don't force the user to encrypt the device. When the device isn't compliant, the following actions take place:

    - If a Conditional Access policy applies to the user, the device is blocked.
    - The Company Portal app notifies the user about any compliance problems.

| **Policy setting** | **Platform** |
| --- | --- |
| **Allowed Distros** | **Linux***(only)* - Quarantined |
| **Device encryption** | - **Android 4.0 and later**: Quarantined - **Samsung Knox Standard 4.0 and later**: Quarantined - **Android Enterprise**: Quarantined - **iOS 8.0 and later**: Remediated (by setting PIN) - **macOS 10.11 and later**: Quarantined - **Linux**: Quarantined - **Windows**: Quarantined |
| **Email profile** | - **Android 4.0 and later**: Not applicable- **Samsung Knox Standard 4.0 and later**: Not applicable- **Android Enterprise**: Not applicable- **iOS 8.0 and later**: Quarantined - **macOS 10.11 and later**: Quarantined - **Linux**: Not applicable - **Windows**: Not applicable |
| **Jailbroken or rooted device** | - **Android 4.0 and later**: Quarantined (not a setting) - **Samsung Knox Standard 4.0 and later**: Quarantined (not a setting)- **Android Enterprise**: Quarantined (not a setting) - **iOS 8.0 and later**: Quarantined (not a setting) - **macOS 10.11 and later**: Not applicable - **Linux**: Not applicable - **Windows**: Not applicable |
| **Maximum OS version** | - **Android 4.0 and later**: Quarantined - **Samsung Knox Standard 4.0 and later**: Quarantined - **Android Enterprise**: Quarantined - **iOS 8.0 and later**: Quarantined - **macOS 10.11 and later**: Quarantined - **Linux**: See *Allowed Distros*- **Windows**: Quarantined |
| **Minimum OS version** | - **Android 4.0 and later**: Quarantined - **Samsung Knox Standard 4.0 and later**: Quarantined - **Android Enterprise**: Quarantined - **iOS 8.0 and later**: Quarantined - **macOS 10.11 and later**: Quarantined - **Linux**: See *Allowed Distros*- **Windows**: Quarantined |
| **PIN or password configuration** | - **Android 4.0 and later**: Quarantined - **Samsung Knox Standard 4.0 and later**: Quarantined - **Android Enterprise**: Quarantined - **iOS 8.0 and later**: Remediated - **macOS 10.11 and later**: Remediated - **Linux**: Quarantined - **Windows**: Remediated |
| **Windows health attestation** | - **Android 4.0 and later**: Not applicable - **Samsung Knox Standard 4.0 and later**: Not applicable - **Android Enterprise**: Not applicable - **iOS 8.0 and later**: Not applicable - **macOS 10.11 and later**: Not applicable - **Linux**: Not applicable - **Windows**: Quarantined |

Note

The Company Portal app enters the enrollment remediation flow when the user signs into the app and the device doesn't successfully check in with Intune for 30 days or more (or the device is noncompliant due to a *Lost contact* compliance reason). In this flow, Intune attempts to initiate a check-in one more time. If that check-in doesn't succeed, Intune issues a retire command to allow the user to re-enroll the device manually.