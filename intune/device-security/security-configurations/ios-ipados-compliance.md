---
layout: Conceptual
title: iOS/iPadOS device compliance security configurations - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-configurations/ios-ipados-compliance
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: protect
description: Review example device compliance configurations of basic, enhanced, and high security for iOS devices.
ms.date: 2025-03-20T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: 
locale: en-us
document_id: 682f01ee-f6a2-18ce-7ac7-e2dff28403b8
document_version_independent_id: 682f01ee-f6a2-18ce-7ac7-e2dff28403b8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-configurations/ios-ipados-compliance.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-configurations/ios-ipados-compliance
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-configurations/ios-ipados-compliance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: afa969be-30fb-cf9f-b8e0-6a232a4a4c09
---

# iOS/iPadOS device compliance security configurations - Microsoft Intune | Microsoft Learn

In support of the [Microsoft Zero Trust security model](/en-us/security/zero-trust/zero-trust-identity-device-access-policies-common), this article provides example configurations you can use with Microsoft Intune to configure iOS/iPad device compliance settings for mobile users using personal and supervised devices. These examples include levels of device security configuration that align with Zero Trust principles.

When using these examples, work with your security team to evaluate the threat environment, risk appetite, and the effect the different levels and configurations can have on usability. After reviewing and adjusting the examples to meet the needs of your organization, you can incorporate them within a ring deployment methodology for testing and production use by importing the sample [iOS/iPadOS Security Configuration Framework JSON templates](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/iOS) with [Intune's PowerShell scripts](https://github.com/microsoftgraph/powershell-intune-samples).

Note

Due to the limited number of settings available for device compliance, there is no basic security (level 1) offering.

## Enhanced security (level 2)

Level 2 is the recommended minimum security configuration for iOS/iPadOS devices where users access work or school data. This configuration is applicable to most mobile users accessing work or school data on a device.

The following table lists only configured settings. Settings not listed in the table aren't configured in this example.

| Section | Setting | Value | Notes |
| --- | --- | --- | --- |
| Device Health | Jailbroken devices | Block |  |
| Device Properties | Minimum OS version | Format: Major.MinorExample: 14.8 | Microsoft recommends configuring the minimum iOS major version to match the supported iOS versions for Microsoft apps. Microsoft apps support an N-1 approach where N is the current iOS major release version. For minor and build version values, Microsoft recommends ensuring devices are up to date with the respective security updates. For Apple's latest recommendations, see [Apple security updates](https://support.apple.com/HT201222). |
| System Security | Require a password to unlock mobile devices | Require |  |
| System Security | Simple passwords | Block |  |
| System Security | Minimum password length | 6 | Organizations should update this setting to match their password policy. |
| System Security | Required password type | Numeric | Organizations should update this setting to match their password policy. |
| System Security | Maximum minutes after screen lock before password is required | 5 | Organizations should update this setting to match their password policy. |
| System Security | Maximum minutes of inactivity until screen locks | 5 | Organizations should update this setting to match their password policy. |
| Actions for noncompliance | Mark device noncompliant | Immediately | By default, the policy is configured to mark the device as noncompliant. Additional actions are available. For more information, see [Configure actions for noncompliant devices in Intune](../compliance/configure-noncompliance-actions). |

## High security (level 3)

Level 3 is the recommended configuration for both:

- Organizations with large and sophisticated security organizations.
- Specific users and groups who might be uniquely targeted by adversaries.

Such organizations are typically targeted by well-funded and sophisticated adversaries.

This configuration expands upon level 2 by:

- Increasing the minimum operating system version.
- Ensuring that the device is compliant by enforcing the most secure Microsoft Defender for Endpoint or mobile threat defense level.
- Enacting stronger password policies.

The policy settings enforced in level 3 include all the policy settings recommended for level 2. The settings listed in the following table include only those that are added or changed. These settings can have significant impact to users or applications. They enforce a level of security more appropriate for risks facing targeted organizations.

| Section | Setting | Value | Notes |
| --- | --- | --- | --- |
| Device Health | Require the device to be at or under the Device Threat Level | Secured | This setting requires a mobile threat defense product. For more information, see [Mobile Threat Defense for enrolled devices](../mobile-threat-defense/create-compliance-policy).Customers should consider implementing Microsoft Defender for Endpoint or a mobile threat defense solution. It isn't necessary to deploy both. |
| Device Properties | Minimum OS version | Format: Major.MinorExample: 15.0 | Microsoft recommends configuring the minimum iOS major version to match the supported iOS versions for Microsoft apps. Microsoft apps support an N-1 approach where N is the current iOS major release version. For minor and build version values, Microsoft recommends ensuring devices are up to date with the respective security updates. For Apple's latest recommendations, see [Apple security updates](https://support.apple.com/HT201222). |
| Microsoft Defender for Endpoint | Require the device to be at or under the machine risk score | Clear | This setting requires Microsoft Defender for Endpoint. For more information, see [Enforce compliance for Microsoft Defender for Endpoint with Conditional Access in Intune](../microsoft-defender/overview).Customers should consider implementing Microsoft Defender for Endpoint or a mobile threat defense solution. It isn't necessary to deploy both. |
| System Security | Password expiration (days) | 365 |  |
| Actions for noncompliance | Mark device noncompliant | Immediately | By default, the policy is configured to mark the device as noncompliant. Additional actions are available. For more information, see [Configure actions for noncompliant devices in Intune](../compliance/configure-noncompliance-actions). |