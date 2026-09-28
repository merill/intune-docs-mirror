---
layout: Conceptual
title: Enroll corporate device with Microsoft Intune app - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to enroll a corporate Android device in Intune
ms.date: 2024-11-07T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 948f89c7-1431-2a39-63aa-d3875fcb4277
document_version_independent_id: 948f89c7-1431-2a39-63aa-d3875fcb4277
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-intune-app-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-intune-app-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-intune-app-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d6954f94-698d-df85-f8e5-7acaaee75df9
---

# Enroll corporate device with Microsoft Intune app - Microsoft Intune | Microsoft Learn

Enroll your corporate-owned Android device to get secure access to work email, apps, and other data that your organization makes available. The Microsoft Intune app supports corporate-owned devices running Android 8.0 and later. It is automatically installed on new and factory-reset devices during enrollment.

There is more than one way to enroll a device for work or school. Your organization should let you know which option to use.

- Near Field Communication (NFC)
- Token
- QR Code
- Google Zero Touch

## Enroll device

Complete these steps to set up and enroll your device.

Note

The Android version or device manufacturer might require you to complete additional steps that aren't covered in this procedure. The colors and text you see in the screenshots might also appear different on your device.

1. Turn on your new or factory-reset device.
2. On the **Welcome** screen, select your language. If your workplace or school instructs you to enroll with a QR code or NFC, do that now. Your options:

    - NFC: Tap your NFC-supported device against a programmer device to connect to your organization's network. Follow the onscreen prompts. When you reach the screen for Chrome's Terms of Service, continue to step 5.
    - QR code: Complete the steps in QR code enrollment.

    If they instruct you to use another method, continue to step 3.
3. Connect to Wi-Fi and tap **NEXT**. Follow the step that matches your enrollment method.

    - Token: When you get to the Google sign-in screen, complete the steps in Token enrollment.
    - Google Zero Touch: After you connect to Wi-Fi, your organization can recognize your device. Continue to step 4 and follow the onscreen prompts until setup is complete.
4. Review the terms from Google. Then tap **ACCEPT & CONTINUE**.
5. Review Chrome's Terms of Service. Then tap **ACCEPT & CONTINUE**.
6. On the sign in screens, sign in with your work or school account.

    a. Enter your email and tap **Next**. b. Enter your password and tap **Sign in**.
7. Depending on your organization's requirements, you might be prompted to update settings, such as screen lock or encryption. If you see these prompts, tap **SET** and follow the onscreen instructions.
8. To install work apps on your device, tap **INSTALL**. After installation is complete, tap **NEXT**.
9. Tap **START** to open the Microsoft Intune app and register your device.
10. Tap **SIGN IN** and then tap **NEXT** to begin registration. When you see the message that registration is complete, tap **DONE**.
11. When you see the message that your device is ready, tap **DONE**.

If you have trouble accessing your organization's resources, you might need to update other settings on your device. Sign in to the Microsoft Intune app to check for required updates.

## QR code enrollment

Scan your company-provided QR code.

1. On the **Welcome** screen, tap the screen five times to start QR code setup.
2. Follow any onscreen instructions to connect to Wi-Fi.
3. If your device doesn't have a QR code scanner, the setup screens show the installation progress for a scanner. Wait for installation to complete.
4. When prompted, scan the enrollment profile QR code that your organization gave you.
5. Return to Enroll device step 4 to continue setup.

## Token enrollment

Enter your company-provided token.

1. On the Google sign-in screen, in the **Email or phone** box, type **afw#setup**. Tap **Next**.
2. Choose **Install** for the **Android Device Policy** app. Continue through the installation. Depending on your device, you might need to review and accept other terms.
3. On the **Enroll this device** screen, select **Next**.
4. Select **Enter code**.
5. On the **Scan or enter code** screen, type in the code that your organization gave you. Then select **Next**.
6. Return to Enroll device step 4 to continue setup.