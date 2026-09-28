---
layout: Conceptual
title: Remove your iOS device from Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to remove an iOS device from Intune and how to delete stored data.
ms.date: 2025-02-18T00:00:00.0000000Z
ms.reviewer: andycerat
locale: en-us
document_id: de7015db-d547-9c56-fbcd-9d99b8e6186c
document_version_independent_id: 8a31fdf7-e4b4-5688-d467-e63546938dfd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/unenrollment/unenroll-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/unenrollment/unenroll-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/unenrollment/unenroll-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 645a930e-512d-68d9-90d1-e9e36f439062
---

# Remove your iOS device from Intune - Microsoft Intune | Microsoft Learn

You can use the Company Portal app for iOS to remove an Intune-enrolled device so that it's no longer managed by your organization. After you remove the device:

- The device is removed from Company Portal.
- You lose access to internal file shares and websites from your device.
- You lose access to school or work apps from your device.
- You might be blocked from connecting to your org's network via Wi-Fi or virtual private network (VPN).
- Work or school email profiles are removed from the device.
- You can't install apps for the device from the Company Portal anymore.
- Changes to device settings (for example, disabling the camera or requiring a certain password length) are no longer required.

## Remove a device

Follow these steps to remove a device you no longer need for work or school from Intune.

1. Sign in to the Company Portal app and select **Devices**.
2. Select the device you want to remove. If you only have one device, skip to step 3.
3. Next to **Rename**, select the ellipses menu. Then tap **Remove device** &gt; **Remove**.

    ![Screenshot of the Company Portal app Devices screen, showing options after user has clicked Remove. Shows &quot;Remove Device&quot; button, &quot;Factory Reset&quot; button, and &quot;Cancel&quot; button.](media/remove-enrollment-ios/cp_ios_unenroll_after_1804_001.png)

    ![Screenshot of the Company Portal app Devices screen, showing options after user has clicked Remove Device button. Shows red highlighted &quot;Remove&quot; button, and blue highlighted &quot;Learn More&quot; button and &quot;Cancel&quot; button.](media/remove-enrollment-ios/cp_ios_unenroll_after_1804_002.png)

## Remove data collected by the Company Portal app

There are three places the Company Portal app stores local data on your device.

- **Information logs**: Standard app activity data that Microsoft collects, such as how long the app was open or if it crashed, is automatically erased when you remove the device from the Company Portal.
- **Apple analytics**: Standard app crash activity data that Apple collects. This information can only be removed by resetting your device back to factory settings. This will erase all personal information on your device. To do this, open **Settings** &gt; **General**. Tap the **Transfer or Reset** option, and then tap **Erase All Content and Settings**.
- **Keychain**: Your device stores your passwords and other information used for sign-ins in your Keychain. Microsoft apps share your sign-in information across any Microsoft-developed apps that you have on your device, including Microsoft Outlook and Microsoft Authenticator. Like Apple analytics, this information can only be removed by resetting your device back to factory settings. This will erase all personal information on your device. To do this, open **Settings** &gt; **General**. Tap the **Transfer or Reset** option, and then tap **Erase All Content and Settings**.