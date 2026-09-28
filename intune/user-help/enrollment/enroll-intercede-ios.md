---
layout: Conceptual
title: Enroll iOS or iPadOS device with Intune Company Portal and Intercede - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intercede-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to enroll an iOS or iPadOS device and set up derived credential authentication with Intercede.
ms.date: 2019-10-31T00:00:00.0000000Z
ms.reviewer: tisilver
locale: en-us
document_id: 12b9c16d-ba84-d887-b6ff-a3ef51b7c218
document_version_independent_id: 12b9c16d-ba84-d887-b6ff-a3ef51b7c218
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-intercede-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-intercede-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-intercede-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
platformId: b0122406-9093-e30c-3f61-49402bb101d7
---

# Enroll iOS or iPadOS device with Intune Company Portal and Intercede - Microsoft Intune | Microsoft Learn

Enroll your device with the Intune Company Portal app to gain secure, mobile access to your organization's email, files, and apps. After your device is enrolled, it becomes *managed*. Your organization can assign policies and apps to the device through a mobile device management (MDM) provider, such as Intune.

During enrollment, you'll also install a derived credential on your device. Your organization might require you to use the derived credential as an authentication method when accessing resources, or for signing and encrypting emails.

You likely need to set up a derived credential if you use a smart card to:

- Sign in to school or work apps, Wi-Fi, and virtual private networks (VPN)
- Sign and encrypt school or work emails using S/MIME certificates

In this article, you will:

- Enroll a mobile iOS or iPadOS device with Intune Company Portal.
- Get a derived credential from your organization's derived credential provider, [Intercede](https://www.intercede.com/).

## What are derived credentials?

A derived credential is a certificate that's derived from your smart card credentials and installed on your device. It grants you remote access to work resources, while preventing unauthorized users from accessing sensitive information.

Derived credentials are used to:

- Authenticate students and employees who sign in to school or work apps, Wi-Fi, and VPN
- Sign and encrypt school or work emails with S/MIME certificates

Derived credentials are an implementation of the National Institute of Standards and Technology (NIST) guidelines for Derived Personal Identity Verification (PIV) credentials as part of Special Publication (SP) 800-157.

## Prerequisites

To complete enrollment, you must have:

- Your school or work-provided smart card
- Access to a computer or self-service kiosk where you can sign in with your smart card
- Your mobile device
- The Intune Company Portal app for iOS and iPadOS installed on your device

## Enroll device

1. Open the Company Portal app for iOS/iPadOS on your mobile device and sign in with your work account.
2. Write down the code that appears on screen.

    ![Example image of Company Portal app with onscreen message and code.](media/enroll-intercede-ios/copy-code-intercede.png)
3. Switch to your smart card-enabled device and go to https://microsoft.com/devicelogin.
4. Enter the code you previously wrote down.
5. Insert your smart card to sign in.
6. Return to the Company Portal app on your mobile device and follow the onscreen instructions to enroll your device.
7. After enrollment is complete, Company Portal will notify you to set up your smart card. Tap the notification. If you don't get a notification, check your email.

    ![Example screenshot of the Company Portal push notification on device home screen.](media/enroll-intercede-ios/action-required-in-app-intercede.png)
8. On the **Setup mobile smart card access** screen: a. Tap the link to your organization's setup instructions. If your organization doesn't provide additional instructions, you are sent to this article. b. Tap **Begin**.

    ![Example screenshot of the Company Portal Set up mobile smart card access screen.](media/enroll-intercede-ios/smart-card-info-intercede.png)
9. Switch to your smart card-enabled device or self-service kiosk and open the MyID app. Sign in with your work credentials.
10. Select the option to request your ID.
11. When asked what profile you want to use, select the option to activate with a mobile credential. A QR code appears.
12. Return to your mobile device. On the Company Portal &gt; **Get QR code** screen, tap **Continue**.

    ![Example screenshot of the Company Portal Get QR code screen.](media/enroll-intercede-ios/get-qr-code-intercede.png)
13. Tap **Use Camera** &gt; **OK**.

    ![Example screenshot of a Company Portal prompt, asking permission to allow camera access.](media/enroll-intercede-ios/allow-cp-camera-access-intercede.png)
14. Scan the image of the QR code that's on your smart card-enabled device.
15. Wait for Company Portal to finish setting up your device.