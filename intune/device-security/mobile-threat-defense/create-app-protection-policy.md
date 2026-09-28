---
layout: Conceptual
title: Create Mobile Threat Defense (MTD) app protection policy with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: Create Mobile Threat Defense (MTD) app protection policy with Microsoft Intune.
ms.date: 2024-08-20T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: cfcd2e9b-e3c7-ce1f-f878-78340f855c3b
document_version_independent_id: cfcd2e9b-e3c7-ce1f-f878-78340f855c3b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/create-app-protection-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/create-app-protection-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/create-app-protection-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d60f2ac1-e739-257b-ee17-34ab7cd88a92
---

# Create Mobile Threat Defense (MTD) app protection policy with Intune - Microsoft Intune | Microsoft Learn

Intune with Mobile Threat Defense (MTD) helps you detect threats and assess risk on mobile and Windows devices. You can create an Intune app protection policy that assesses risk to determine if the application is allowed to access corporate data or not.

Note

This article applies to all Mobile Threat Defense partners that support app protection policies:

- Better Mobile (Android, iOS/iPadOS)
- BlackBerry Mobile (CylancePROTECT for Android, iOS/iPadOS)
- Check Point Harmony Mobile (Android, iOS/iPadOS)
- Jamf (Android, iOS/iPadOS)
- Lookout for Work (Android, iOS/iPadOS)
- Microsoft Defender for Endpoint (Android, iOS/iPadOS, Windows)
- SentinelOne (Android, iOS/iPadOS)
- Symantec Endpoint Security (Android, iOS/iPadOS)
- Trellix Mobile Security (Android, iOS/iPadOS)
- Windows Security Center (Windows) - *For information about the Windows versions that support this connector, see [Data protection for Windows MAM](../../app-management/protection/enable-mam-windows).*
- Zimperium (Android, iOS/iPadOS)

## Before you begin

As part of the MTD setup, in the MTD partner console, you created a policy that classifies various threats as high, medium, and low. You now need to set the Mobile Threat Defense level in the Intune app protection policy.

Prerequisites for app protection policy with MTD:

- Set up MTD integration with Intune. Without this integration, the MTD app protection policy has no effect.

## To create an MTD app protection policy for mobile

Use the procedure to [create an Application protection policy for either iOS/iPadOS or Android](../../app-management/protection/create-policy#app-protection-policies-for-iosipados-and-android-apps), and use the following information on the *Apps*, *Conditional launch*, and *Assignments* pages:

- **Apps**: Select the apps you wish to target with app protection policies. For this feature set, these apps are blocked or selectively wiped based on device risk assessment from your chosen Mobile Threat Defense vendor.
- **Conditional launch**: Below *Device conditions*, use the drop-down box to select **Max allowed device threat level**.

    Options for the threat level **Value**:

    - **Secured**: This level is the most secure. The device can't have any threats present and still access company resources. If any threats are found, the device is evaluated as noncompliant.
    - **Low**: The device is compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
    - **Medium**: The device is compliant if the threats found on the device are low or medium level. If high-level threats are detected, the device is determined as noncompliant.
    - **High**: This level is the least secure and allows all threat levels, using Mobile Threat Defense for reporting purposes only. Devices are required to have the MTD app activated with this setting.

    Options for **Action**:

    - **Block access**
    - **Wipe data**
- **Assignments**: Assign the policy to groups of users. The devices used by the group's members are evaluated for access to corporate data on targeted apps via Intune app protection.

## To create an MTD app protection policy for Windows

Use the procedure to [create an Application protection policy for Windows](../../app-management/protection/ref-settings-windows), and use the following information on the *Apps*, *Health Checks*, and *Assignments* pages:

- **Apps**: Select the apps you want to target app protection policies. For this feature set, these apps are blocked or selectively wiped based on device risk assessment from your chosen Mobile Threat Defense vendor.
- **Health Checks**: Below *Device conditions*, use the drop-down box to select **Max allowed device threat level**.

    Options for the threat level **Value**:

    - **Secured**: This level is the most secure. The device can't have any threats present and still access company resources. If any threats are found, the device is evaluated as noncompliant.
    - **Low**: The device is compliant if only low-level threats are present. Anything higher puts the device in a noncompliant status.
    - **Medium**: The device is compliant if the threats found on the device are low or medium level. If high-level threats are detected, the device is determined as noncompliant.
    - **High**: This level is the least secure and allows all threat levels, using Mobile Threat Defense for reporting purposes only. Devices are required to have the MTD app activated with this setting.

    Options for **Action**:

    - **Block access**
    - **Wipe data**
- **Assignments**: Assign the policy to groups of users. The devices used by the group's members are evaluated for access to corporate data on targeted apps via Intune app protection.

Important

If you create an app protection policy for any protected app, the device's threat level is assessed. Depending on the configuration, devices that don't meet an acceptable level are either blocked or selectively wiped through conditional launch. If blocked, they are prevented from accessing corporate resources until the threat on the device is resolved and reported to Intune by the chosen MTD vendor.