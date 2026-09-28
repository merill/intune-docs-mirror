---
layout: Conceptual
title: Set up personal device for work - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to enroll and register a personal iPhone or iPad for work or school using Intune Company Portal.
ms.date: 2025-03-13T00:00:00.0000000Z
ms.reviewer: rishitasarin
locale: en-us
document_id: 99a6423f-d6c8-0300-4155-0c42198d558c
document_version_independent_id: 99a6423f-d6c8-0300-4155-0c42198d558c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-ios.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: b7b222df-29a4-b5fd-ba85-2ddb1275fc53
---

# Set up personal device for work - Microsoft Intune | Microsoft Learn

**Applies to iOS/iPadOS** Enroll and register your iPhone or iPad for work or school to access apps, Wi-Fi, and other resources. This article describes how to enroll your personal device using the following enrollment options:

- Account driven user enrollment
- Device enrollment with Microsoft Intune Company Portal app
- Web enrollment
- Determine based on your choice

Typically, your organization decides which method to use. Refer to your organization's onboarding documentation to find out which method to use. To enroll a brand new corporate-owned device, see [Set up access on new work or school device](enroll-automated-ios).

Important

We don't sell any data collected by our service to any third parties for any reason.

Note

If you tried to access your work email in the Mail app, and received a prompt to get your device managed, you're in the right place. Follow the instructions in this article to regain access to your email and other work resources on your iOS device.

## Account driven user enrollment

Initiate enrollment in the Settings app by signing in with your work or school account, or organization-provided Apple ID. After you approve remote management, the enrollment profile silently installs and your organization's Intune policies apply, enabling you to sign in to apps such as Microsoft Teams and Microsoft Outlook with your work account. For this process, you need:

- Safari web browser
- iOS/iPadOS version 15 or later
- Stable Wi-Fi connection

If this method is unavailable on your device, enroll your device with the Company Portal app or via web enrollment.

1. Open the Settings app on your device.
2. Go to **General** &gt; **VPN & Device Management**.
3. Tap the option to sign in with your work or school account. Sign in with your work or school account, or with the Apple ID provided to you by your organization.
4. Sign in to iCloud. Enter the password for the username that appears onscreen. Then select **Continue**.
5. Tap **Allow Remote Management**.
6. Wait a few minutes while your device is configured and the configuration profile is installed.
7. To confirm your device is ready to use for work, return to **VPN & Device Management** in your Settings app. Confirm that your work account is listed as a managed account.
8. Microsoft Authenticator is required to access work apps. Wait a few minutes after enrollment for Authenticator to install on your device. An error message appears if you try to sign in to a work app without Authenticator.
9. Approve other work apps, as necessary. As you receive each prompt, select **Install** to approve its installation.
10. Sign in to a work app, such as Microsoft Teams, with your work or school account. The first time you sign in, your device will be checked to ensure it meets your organization's device and security policies. If your device is compliant, you can access your work account. If not, you receive a prompt to update your device settings.

## Device enrollment with Company Portal app

Initiate enrollment in the Intune Company Portal app. The Company Portal app is used to enroll and manage your device, install work apps, and get IT support. The app supports devices running iOS 14.0 and later. Maintain a Wi-Fi connection until all steps are complete. Pausing for more than a few minutes during device enrollment might cause the Company Portal app to close or end setup. If this happens, reopen the app and try again.

For this process, you need:

- Safari web browser
- iOS/iPadOS version 14 or later
- Stable Wi-Fi connection
- [Intune Company Portal app](https://apps.apple.com/us/app/intune-company-portal/id719171358)(opens the Apple App Store)
- Latest version of the Microsoft Authenticator app

1. Open the Company Portal app, and sign in to the Company Portal app with your work or school account. Example: jojordan@contoso.com
2. On the **How to set up your device** screen, review the enrollment steps and information about what your organization can see and do on an enrolled device. Then select **Get started**.
3. The Safari web browser opens the Intune Company Portal website. When prompted to, select **Allow** to download the Intune configuration profile for your device.
4. A pop-up appears when installation is complete. Select **Close**.
5. Open the Settings app on your device and go to **Profile Downloaded**.

    - If this option isn't available, go to **General** &gt; **VPN & Device Management**.
6. Tap **Management Profile**. Then tap **Install**.
7. You might need to reenter your passcode. Then tap **Install** again.
8. When prompted to, read the remote management warning. Tap **Install** again to continue. Then tap **Trust**.
9. Wait while the management profile installs. Tap **Done** when installation is complete.
10. Return to the Company Portal app and go to **Notifications**. Under pending requirements, tap the option to register your device.
11. Wait a few minutes while your device receives apps and policies from your organization.

    - After enrollment, you might receive prompts from your organization to install required apps. Tap **Install** on the app prompts to install the apps.
    - If you already installed Microsoft Authenticator on your device, you're prompted to allow Microsoft to take management of the Microsoft Authenticator app. Tap **Manage** to allow.
    - Your organization might require a mobile threat defense app on your device, which monitors your work apps for threats and viruses. Tap **Install** to proceed with installation. If the app is a requirement and you skip installation, you might not be allowed to access work resources.
12. Go to a work app like Microsoft Teams or Microsoft Outlook and sign in with your work or school account to confirm that you have access.

    1. If access is limited due to compliance requirements, you receive an in-app prompt upon sign-in. Tap **Check compliance** to open Company Portal and review pending notifications and requirements.
    2. After you update device settings, tap **Retry** to recheck and refresh your compliance status. If the retry fails right away, wait a few minutes for your most recent changes to register with Microsoft. Then try again.

## Web enrollment

Initiate enrollment on the Intune Company Portal website. For this process, you need:

- Safari web browser
- iOS/iPadOS version 15 or later
- Stable Wi-Fi connection

1. Open Safari and go to https://portal.manage.microsoft.com/enrollment/webenrollment/ios. Sign in with your work or school account.
2. When prompted to, download the configuration profile. Wait in Safari while Company Portal downloads the profile.
3. Open the Settings app on your device and go to **General** &gt; **VPN & Device Management** to view and install the new configuration profile.

    1. Select **Profile Downloaded**.
    2. Select **Install** and follow the onscreen instructions to install the profile.
4. Wait until Microsoft Authenticator is installed on the device before signing in to a work or school app. The device won't be ready for work use until Authenticator is on the device, which can take a few minutes. To verify that Authenticator installed, open your device settings and go to **Profile** &gt; **Management Profile** &gt; **Single Sign On Extension**. Authenticator should be listed as the SSO extension.
5. Sign in to a work app, such as Microsoft Teams, with your work account.
6. Wait while the app identifies required setting updates. For example, you may be required to update your device's operating system before you can use the app. Check the app you're signed in to for pending action items. When you're done making changes, recheck the device settings.

## Determine based on user choice

1. Open the Company Portal app on your personal device and sign in with your work or school account.
2. On the **Set up access** screen, select **Begin.**

    ![Example screenshot of Company Portal, &quot;Set up access&quot; screen.](media/enroll-ios/ios-enrollment-checklist-1909.png)
3. Select your device and enrollment type. Tap **I own this device** since you're using a personal device that you brought from home. Then continue to the next step. If you're enrolling a company-provided device, tap **My company owns this device**, and then go to [Device enrollment with Company Portal](enroll-ios#device-enrollment-with-company-portal-app) to finish setup.

    ![Example screenshot of Company Portal, &quot;Select device and enrollment type&quot; screen, device type options.](media/enroll-ios/ios-device-type-1909.png)
4. Choose how to protect the data on your device once it's enrolled.

    ![Example screenshot of Company Portal, &quot;Select device and enrollment type&quot; screen, enrollment type options.](media/enroll-ios/ios-enrollment-type-1909.png)

    Your options:

    - Tap **Secure entire device** to secure all apps and data on the device. Then go to [Device enrollment with Company Portal](enroll-ios#device-enrollment-with-company-portal-app).
    - Tap **Secure work-related apps and data only** to secure only the apps and data you access with your work account. Then go to [Account driven user enrollment](enroll-ios#account-driven-user-enrollment).

## IT administrator support

If you're an IT administrator and run in to problems while enrolling devices, see [Troubleshooting iOS device enrollment problems in Microsoft Intune](/en-us/troubleshoot/mem/intune/device-enrollment/troubleshoot-ios-enrollment-errors). This article lists common errors, their causes, and steps to resolve them.