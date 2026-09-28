---
layout: Conceptual
title: Install mobile threat defense app on your mobile device - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/security/setup-mobile-threat-defense
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Find out what mobile threat defense apps are and how to set one up to meet work or school requirements.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: aanavath
locale: en-us
document_id: 15a2c16e-975e-cdee-226f-4f305f67401e
document_version_independent_id: 2355e80f-0abd-dff8-642d-bc2e982147b9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/security/setup-mobile-threat-defense.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/security/setup-mobile-threat-defense
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/security/setup-mobile-threat-defense.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
platformId: b8be005b-e66c-d01b-9113-d01730c2b3bb
---

# Install mobile threat defense app on your mobile device - Microsoft Intune | Microsoft Learn

**Applies to:**

- iOS/iPadOS
- Android

Install a mobile threat defense (MTD) app on the personal device you use for work or school. An MTD app works by detecting and alerting you to threats on your device, like suspicious apps or networks, and operating system vulnerabilities. In this article, you'll learn how to set up and activate an MTD app so that you can satisfy your organization's security requirement and access work apps.

## Step 1: Install MTD app

Note

An additional step, called *device registration*, happens prior to app installation on devices that aren't registered. Registration is required to confirm your identity and connect your work or school account to your device. For more information about device registration, see [Register your personal device on your organization's network](/en-us/azure/active-directory/user-help/user-help-register-device-on-network).

Install a mobile threat defense (MTD) app on the device you use for work or school. Your organization chooses the MTD app you need to access internal resources. If the app name or listing isn't provided to you during enrollment or app setup, contact your IT support person to determine which app you need to use. The following MTD apps are commonly used on Apple devices. Select an app to open its listing in the App Store.

- [ActiveShield](https://apps.apple.com/app/activeshield/id980234260)
- [Microsoft Defender for Endpoint](https://apps.apple.com/app/microsoft-defender-atp/id1526737990)
- [Jamf Trust](https://apps.apple.com/us/app/jamf-trust/id1608041266)
- [Lookout for Work](https://apps.apple.com/app/lookout-for-work/id997193468)
- [Pradeo Security](https://apps.apple.com)
- [Harmony Mobile Protect](https://apps.apple.com/app/sandblast-mobile-protect/id1006390797)
- [SEP Mobile](https://apps.apple.com/app/sep-mobile/id695620821)
- [Sophos Intercept X for Mobile](https://apps.apple.com/app/sophos-mobile-security/id1086924662)
- [Zimperium MTD](https://apps.apple.com/app/zimperium-zips/id1030924459)

The following MTD apps are commonly used on Android devices. Select an app to open its listing in Google Play.

- [Microsoft Defender for Endpoint](https://play.google.com/store/apps/details?id=com.microsoft.scmx)
- [Jamf Trust](https://play.google.com/store/apps/details?id=com.wandera.android)
- [Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise&amp;hl)
- [Pradeo Security](https://play.google.com/store/apps/details?id=net.pradeo.service)
- [Harmony Mobile Protect](https://play.google.com/store/apps/details?id=com.lacoon.security.fox)
- [SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure)
- [Sophos Intercept X for Mobile](https://play.google.com/store/apps/details?id=com.sophos.smsec)
- [Zimperium MTD](https://play.google.com/store/apps/details?id=com.zimperium.zips)

## Step 2: Activate MTD app

The prompt to install a MTD app happens when you're setting up your device for work or school. The prompt could appear as an Intune Company Portal push notification or as a message in the Company Portal app or website. Tap the prompt to get the appropriate MTD app.

After you install the MTD app, activate the MTD app on your iOS or Android device.

### Activation for iOS app

1. Open the MTD app.
2. The MTD app asks for permission to open Microsoft Authenticator. Select **Open**.
3. Sign in with your work account.
4. Wait while the MTD app scans your device for security threats. If the scan doesn't happen automatically, you can start the scan yourself.
5. Return to the Intune Company Portal app or website, and run a device check to register the changes you made on your device.

    - In the Company Portal app, select **CONFIRM DEVICE SETTINGS**.
    - On the Company Portal website, select **Check status**.

After you've met this requirement, you can securely sign in and access work apps and files on your device. If Company Portal is still blocking you from access:

- Check the MTD app for threats and resolve them.
- Return to the Company Portal app or website and check for other flagged device settings. Your workplace might have other requirements that require your attention. For more information, see [Check device compliance in Company Portal app for iOS](../device-actions/sync-device-ios).

### Activation for Android app

1. Open the MTD app.
2. Review and grant permissions, as needed, to the MTD app. Permissions vary by MTD app.
3. Wait while the MTD app scans your device for security threats. If the scan doesn't happen automatically, you can start the scan yourself.
4. Return to the Intune Company Portal app or website, and run a device check to register the changes you made on your device.

    - In the Company Portal app, select **CONFIRM DEVICE SETTINGS**.
    - On the Company Portal website, select **Check status**.
5. After you've met this requirement, you can securely sign in and access work apps and files on your device. If Company Portal is still blocking you from access:

    - Check the MTD app for threats and resolve them.
    - Return to the Company Portal app and check for other compliance issues that need your attention. For more information, see [Check compliance in Company Portal app for Android](../compliance/validate-compliance-android).

## Resolving a threat

If a threat is detected and exceeds an acceptable threat level, your workplace could:

- Block access: Block you from using apps while signed in to your work or school account.
- Wipe data: Delete your work or school data from one or more work apps.

To resolve a threat and regain access to work apps, complete the following steps.

1. Open the MTD app on your device.
2. Open the threat details in the app. These details explain how the threat could affect your device if left unresolved, and how to resolve it.
3. Make the required changes on your device. For example, you might need to uninstall an app that's not safe.
4. Return to the MTD app and start a new scan.
5. Repeat these steps until all threats are resolved. Wait a few minutes for your changes to sync between the MTD app and Company Portal.

## Information your organization can see

Your organization can't see any data, such as texts, emails, and pictures, in your personal apps. The MTD app reports information to your organization about apps, including:

- App name
- App ID: The unique name that identifies the app in Google Play.
- App version and short version number: The specific release numbers for an app.
- App bundle and dynamic size: The amount of space an app uses on your device.

The actual information reported depends on the MTD vendor your organization uses. For more information, contact your IT support person.

## Get support

Contact your support person for help with:

- Identifying which MTD app to use
- App installation
- Failed installation
- Detecting/resolving a threat
- Uninstalling an MTD app

Sign in to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) with your work or school account to find your organization's IT helpdesk information.