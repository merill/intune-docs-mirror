---
layout: Conceptual
title: Enroll Android device with Intune Company Portal - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-company-portal-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to set up an Android device for work or school with the Company Portal app.
ms.date: 2025-09-30T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 60b4eb41-d66a-b1c3-b417-4946643ba3d6
document_version_independent_id: 6f6e2af0-eb71-16e8-62d0-d86c73a56332
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-company-portal-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-company-portal-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-company-portal-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 5bd1358e-b2f3-c678-fdbd-6d6e4312dfe1
---

# Enroll Android device with Intune Company Portal - Microsoft Intune | Microsoft Learn

Enroll your personal or corporate-owned Android device with Intune Company Portal to get secure access to company email, apps, and data.

## Prerequisites

The Intune Company Portal app supports devices running Android 8.0 and later, including devices secured by Samsung Knox Standard 2.4 and later. To learn how to update your Android device to meet requirements, see [Check & update your Android version](https://support.google.com/android/answer/7680439).

Important

Support for Android Company Portal versions earlier than 5.0.5421.0 ended on October 1, 2025. Devices running older versions might no longer maintain their registration status and can be marked noncompliant. To keep devices registered and compliant, users must update to a supported version of the Company Portal app.

Note

Samsung Knox is a type of security that certain Samsung devices use for extra protection outside of what native Android provides. To check if you have a Samsung Knox device, go to **Settings** &gt; **About device**. If you don't see the **Knox version** listed there, you have a native Android device.

## Install Company Portal app

Install the Intune Company Portal app [from Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). See [Install Company Portal app in People's Republic of China](../company-portal/install-android-china) for a list of stores that offer the app in People's Republic of China.

1. On your device, open the **Play Store** app.
2. Search for and install **Intune Company Portal**.
3. When prompted about app permissions, tap **ACCEPT**.

## Enroll device

During enrollment, you might be asked to choose a category that best describes how you use your device. Company Portal uses your answer to check for work and school apps relevant to you.

1. Open the Company Portal app and sign in with your work or school account. Review notification permissions for Company Portal as they pop up. You can adjust notification permissions anytime in the Settings app.
2. If you're prompted to accept your organization's terms and conditions, tap **ACCEPT ALL**.

    ![Screenshot of the Company Portal, Terms screen, highlighting &quot;Accept all&quot; button.](media/enroll-company-portal-android/accept-terms-1911.png)
3. Review what your organization can and can't see. Then tap **CONTINUE**.

    ![Screenshot of Company Portal, We care about your privacy screen, highlighting the Continue button.](media/enroll-company-portal-android/android-privacy-screen-1911.png)
4. Review what to expect in the upcoming steps. Then tap **NEXT**.

    ![Screenshot of Company Portal, What's next screen, highlighting the Next button.](media/enroll-company-portal-android/android-whats-next-1911.png)
5. Depending on your version of Android, you might be prompted to allow access to certain parts of your device. These prompts are a Google requirement and not controlled by Microsoft.

    Tap **Allow** for the following permissions:

    - **Allow Company Portal to make and manage phone calls**: This permission enables your device to share its international mobile station equipment identity (IMEI) number with Intune, your organization's device management provider. It's safe to allow this permission. Microsoft never makes or manages phone calls.
    - **Allow Company Portal to access your contacts**: This permission lets the Company Portal app create, use, and manage your work account. It's safe to allow this permission. Microsoft never accesses your contacts.

    If you deny permission, you'll be prompted again the next time you sign in to Company Portal. To turn off these messages, select **Never ask again**. To manage app permissions, go to the Settings app &gt; **Apps** &gt; **Company Portal** &gt; **Permissions** &gt; **Phone**.
6. Activate the device admin app.

    Company Portal needs device administrator permissions to securely manage your device. Activating the app lets your organization identify possible security issues, such as repeated failed attempts to unlock your device, and respond appropriately.

    ![Screenshot of the Activate device administrator screen, highlighting the activate button.](media/enroll-company-portal-android/activate-device-administrator-1911.png)

Note

Microsoft doesn't control the messaging on this screen. We understand that its phrasing can seem drastic. Company Portal can't specify which restrictions and access are relevant to your organization. If you have questions about how your organization uses the app, contact your IT support person. Go to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) to find your organization's contact information.

1. Your device begins enrolling. Review and acknowledge the ELM Agent privacy policy if Company Portal prompts for it.
2. On the **Company Access Setup** screen, check that your device is enrolled. Then tap **CONTINUE**.

    ![Screenshot of Company Portal, Company Access Setup screen, showing Get your device managed is complete.](media/enroll-company-portal-android/update-settings-1911.png)
3. Your organization might require you to update your device settings. Tap **RESOLVE** to adjust a setting. When you're done updating settings, tap **CONTINUE**.

    ![Screenshot of Company Portal, Update device settings, highlighting Resolve and Continue buttons.](media/enroll-company-portal-android/resolve-settings-1911.png)
4. When setup is complete, tap **DONE**.

    ![Screenshot of Company Portal, Company Access Setup screen, showing completed setup and highlighting Done button.](media/enroll-company-portal-android/android-enrollment-done-1911.png)