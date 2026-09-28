---
layout: Conceptual
title: Company Portal device setting requirements for iOS/iPadOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/device-settings-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn more about Intune Company Portal device setting requirements for iOS/iPadOS devices.
ms.date: 2025-08-18T00:00:00.0000000Z
ms.reviewer: rishitasarin
locale: en-us
document_id: b7a9bed9-939c-c0dd-2fd5-662034d505bf
document_version_independent_id: b7a9bed9-939c-c0dd-2fd5-662034d505bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/device-settings-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/device-settings-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/device-settings-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
platformId: e16c5109-b720-8c6a-f929-31bc592ceac4
---

# Company Portal device setting requirements for iOS/iPadOS - Microsoft Intune | Microsoft Learn

This article describes the iOS/iPadOS device setting requirements that the Intune Company Portal can enforce on behalf of your workplace or school. Requirements are determined by your organization, and help keep your device secure while you're using it for work or school purposes. You only need to update settings flagged by Company Portal.

## Device limit reached

To prevent unauthorized access to internal data, your school or workplace might limit the number of devices you can register. If you reach the device limit, we recommend removing one of your devices or contacting your support person to increase the device limit. Your options:

- Remove a device in Company Portal.
- Contact your IT support person and ask if they can increase the number of devices you're allowed to register.

## Identify device

If Company Portal prompts you to identify your device during enrollment, then you have at least one device that's already enrolled and assigned to your account. In this case, the device was enrolled via a method other than the Company Portal app. To resolve this message, select your device from the list in Company Portal.

If your device isn't listed:

1. Select **new device**.
2. Select **Continue**.
3. Enter the last four characters of your device's serial number. For more information, see [Find the serial number of your Apple product](https://support.apple.com/en-us/102858) on Apple Support.

## Operating system isn't supported

The OS version that's on your device isn't supported. It's possible that the latest version of iOS/iPadOS doesn't work with your organization's apps, tools, and other internal infrastructure. To resolve this issue, contact your IT support person and find out what the OS requirements are for your device.

## Reconnect compromised device

A *jailbroken* device is a device that has been altered to enable unrestricted access to certain critical files. Jailbroken devices can compromise security and cause a threat to work or school data. If Company Portal detects a jailbroken device, it revokes access to work or school resources. You likely need to reset your device to factory settings to return your device to its original configuration. We recommend that you contact your IT support person for help and other possible options. For contact information, check the Company Portal app or [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).

## Sync with Microsoft Defender for Endpoint

Your organization requires you to install Microsoft Defender for Endpoint on your device and verify your device is secure enough to use work or school apps. Select **Resolve** to open Microsoft Defender for Endpoint. If you don't have the app, your device redirects you to the App Store to install it. Once you're in the app, run a security check to verify that your device is secure.

After the check is complete, Microsoft Defender automatically redirects you back to the work or school app where you were originally blocked for being noncompliant. You should now be able to access your work or school app. If Microsoft Defender doesn't automatically redirect you, return to the work or school app you were trying to access before. If you still see the noncompliance prompt, select **Refresh** and you should have access to your work or school app.

For more information about mobile threat defense apps like Microsoft Defender for Endpoint, see [Set up mobile threat defense](../security/setup-mobile-threat-defense).

## Update operating system version

Keeping your device up-to-date lets you access the newest features, and it also ensures that your device has the most secure version of its operating system (OS). While using the device for work or school, we recommend keeping both personal and corporate devices up-to-date with the newest versions. Before updating your device, back up all of the information on it. Keeping a backup can help you recover your data if something should interrupt any updates, or lets you transfer your information to a replacement device.

To check your device for available software updates, go to **Settings** and tap **General** &gt; **Software Update**.