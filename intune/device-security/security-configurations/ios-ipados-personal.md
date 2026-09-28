---
layout: Conceptual
title: iOS/iPadOS personal device security configurations - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-configurations/ios-ipados-personal
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
description: Review example personal device security configurations of basic, enhanced, and high security for iOS devices.
ms.date: 2025-03-20T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: 
locale: en-us
document_id: 703be67a-7387-b5d8-bbb4-346f1c841b4f
document_version_independent_id: 703be67a-7387-b5d8-bbb4-346f1c841b4f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-configurations/ios-ipados-personal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-configurations/ios-ipados-personal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-configurations/ios-ipados-personal.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 3bdc122c-ed62-621f-99dd-307d63182bfe
---

# iOS/iPadOS personal device security configurations - Microsoft Intune | Microsoft Learn

In support of the [Microsoft Zero Trust security model](/en-us/security/zero-trust/zero-trust-identity-device-access-policies-common), this article provides example configurations you can use with Microsoft Intune to configure iOS/iPad device compliance settings for mobile users using personal devices. These examples include three levels of device security configuration that align with Zero Trust principles.

When using these examples, work with your security team to evaluate the threat environment, risk appetite, and the effect the different levels and configurations can have on usability. After reviewing and adjusting the examples to meet the needs of your organization, you can incorporate them within a ring deployment methodology for testing and production use by importing the sample [iOS/iPadOS Security Configuration Framework JSON templates](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/iOS) with [Intune's PowerShell scripts](https://github.com/microsoftgraph/powershell-intune-samples).

For more information on each policy setting, see [iOS/iPadOS device settings in Microsoft Intune](../../device-configuration/templates/ref-device-restrictions-apple).

## Personal basic security (level 1)

Level 1 is the recommended minimum security configuration for iOS/iPadOS personal devices where users access work or school data.

The policies in level 1 enforce a reasonable data access level while minimizing the impact to users. This is done by enforcing password policies, device lock characteristics, and disabling certain device functions (for example, untrusted certificates).

The following table lists only configured settings. Settings not listed in the table aren't configured in this example.

### Device restrictions

| Category | Setting | Value | Notes |
| --- | --- | --- | --- |
| App Store, Doc Viewing, Gaming | Treat AirDrop as an unmanaged destination | Yes |  |
| Built-in Apps | Block Siri while device is locked | Yes |  |
| Built-in Apps | Require Safari fraud warnings | Yes |  |
| Cloud and Storage | Force encrypted backup | Yes |  |
| Cloud and Storage | Block managed apps from storing data in iCloud | Yes |  |
| Connected Devices | Force Apple Watch wrist detection | Yes |  |
| General | Block untrusted TLS certificates | Yes |  |
| General | Block trusting new enterprise app authors | Yes |  |
| Locked Screen Experience | Block Notification Center access in lock screen | Yes |  |
| Locked Screen Experience | Block Today view in lock screen | Yes |  |
| Password | Require a password | Yes |  |
| Password | Block simple passwords | Yes |  |
| Password | Required password type | Numeric |  |
| Password | Minimum password length | 6 | Organizations should update this setting to match their password policy. |
| Password | Number of sign-in failures before wiping the device | 10 | Organizations should update this setting to match their password policy. |
| Password | Maximum minutes after screen lock before password is required | 5 | Organizations should update this setting to match their password policy. |
| Password | Maximum minutes of inactivity until screen locks | 5 | Organizations should update this setting to match their password policy. |

## Personal enhanced security (level 2)

Level 2 is the recommended configuration for personal devices where users access more sensitive information. These devices are a natural target in enterprises today. These settings don't assume a large staff of highly skilled security personnel. Therefore, they should be accessible to most enterprise organizations. This configuration is applicable to most mobile users accessing work or school data on a device.

This configuration expands upon the configuration in level 1 by enacting data sharing controls.

The level 2 settings include all the policy settings recommended for level 1. However, the settings listed in the following table include only those settings that are added or changed. These settings can have a slightly higher impact to users or to applications. They enforce a level of security more appropriate for risks facing users with access to sensitive information on mobile devices.

### Device restrictions

| Category | Setting | Value | Notes |
| --- | --- | --- | --- |
| App Store, Doc Viewing, Gaming | Block viewing corporate documents in unmanaged apps | Yes |  |
| App Store, Doc Viewing, Gaming | Block viewing non-corporate documents in corporate apps | Not configured | Enabling this device restriction blocks Outlook for iOS’s ability to export contacts. This setting isn't recommended if using Outlook for iOS. For more information, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-enabling-outlook-ios-contact-sync-with-ios12-mdm/ba-p/298453). |
| App Store, Doc Viewing, Gaming | Allow managed apps to write contacts to unmanaged contacts accounts | Yes | This setting is needed to allow Outlook for iOS to export contacts when **Block viewing corporate documents in unmanaged apps** is set to *Yes*. For more information, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-enabling-outlook-ios-contact-sync-with-ios12-mdm/ba-p/298453). |
| App Store, Doc Viewing, Gaming | Allow copy/paste to be affected by managed open-in | Not configured | Enabling this setting blocks personal accounts within managed Microsoft apps from sharing data to unmanaged apps. |
| Built-in Apps | Block Siri for dictation | Yes |  |
| Built-in Apps | Block Siri for translation | Yes |  |
| Cloud Storage | Block backup of enterprise books | Yes |  |
| Cloud Storage | Block notes and highlights sync for enterprise books | Yes |  |
| General | Block sending diagnostic and usage data to Apple | Yes |  |

## Personal high security (level 3)

Level 3 is the recommended configuration for both:

- Organizations with large and sophisticated security organizations.
- Specific users and groups who are uniquely targeted by adversaries.

Such organizations are typically targeted by well-funded and sophisticated adversaries.

This configuration expands upon level 2 by:

- Enacting stronger password policies.
- Disabling device functionality (for example, screenshots and screen recordings).
- Enforcing additional data transfer restrictions (for example, blocking Handoff).

The policy settings enforced in level 3 include all the policy settings recommended for level 2. The settings listed in the following table include only those that are added or changed. These settings can have significant impact to users or applications. They enforce a level of security more appropriate for risks facing targeted organizations.

### Device restrictions

| Category | Setting | Value | Notes |
| --- | --- | --- | --- |
| Cloud and Storage | Block Handoff | Yes |  |
| Connected Devices | Require AirPlay outgoing requests pairing password | Yes |  |
| Connected Devices | Block Apple Watch auto unlock | Yes |  |
| General | Block screenshots and screen recording | Yes |  |
| Password | Number of sign-in failures before wiping the device | 5 | Organizations should update this setting to match their password policy. |
| Password | Password expiration (days) | 365 | Organizations should update this setting to match their password policy. |
| Password | Prevent reuse of previous passwords | 5 | Organizations should update this setting to match their password policy. |
| Wireless | Block voice dialing while device is locked | Yes |  |