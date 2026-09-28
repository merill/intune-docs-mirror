---
layout: Conceptual
title: Enroll device and create Android work profile - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-work-profile-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: How create a work profile and enroll device with Intune Company Portal.
ms.date: 2024-11-13T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: f5ddb916-d680-d5c0-078d-9f0f0b2048b5
document_version_independent_id: f5ddb916-d680-d5c0-078d-9f0f0b2048b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-work-profile-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-work-profile-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-work-profile-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d264474f-d0e8-df54-7903-a43a355008bd
---

# Enroll device and create Android work profile - Microsoft Intune | Microsoft Learn

Enroll your personal Android device to get access to work emails, apps, Wi-Fi, and other resources. During enrollment, you will:

1. Create a work profile.
2. Activate the work profile.
3. Update device settings.

This article describes how to enroll your device using the Intune Company Portal app. For more information about the work profile and its features, see [Introduction to Android work profile](work-profile-android). 

## Before you begin

[Install the Intune Company Portal app from Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). The Company Portal app is used to enroll and manage your device, install work apps, and get IT support.

## Enroll device

Make sure you're signed in to the primary user account on your device. Work profile enrollment isn't supported on secondary user accounts.

1. Open the Intune Company Portal app and sign in with your work or school account.
2. On the **Company Access Setup** screen, review the tasks required to enroll your device. Then tap **BEGIN**.

    ![Screenshot of Company Access Setup screen highlighting the Begin button.](media/enroll-work-profile-android/access-setup-work-profile-1911.png)
3. On the privacy information screen, review the list of items that your organization can and can't see on your device. Then tap **CONTINUE**.

    ![Screenshot of Company Portal's We care about your privacy screen, highlighting the Continue button.](media/enroll-company-portal-android/android-privacy-screen-1911.png)
4. Review the Google terms for creating a work profile. Accept the terms to continue. The appearance of this screen varies based on OS version.

![Screenshot of Company Portal showing link to Google terms, and highlighting the Accept &amp; continue button.](media/enroll-work-profile-android/google-terms-screen-work-profile.png)
5. Review the Samsung Knox privacy policy. Select **Agree** to continue. This screen only appears if you're using a Samsung device.

![Screenshot of Company Portal showing link to Samsung Knox Privacy Policy and highlighting Agree button.](media/enroll-work-profile-android/samsung-knox-privacy-policy-2307.png)
6. Wait a few minutes while your work profile is set up. Then select **Next**.

![Screenshot of Company Portal highlighting the Next button.](media/enroll-work-profile-android/work-profile-setup-next-2307.png)
7. On the **Company Access Setup** screen, confirm that you created the profile. Then tap **CONTINUE** to proceed to the next enrollment task.

![Screenshot of Company Access Setup showing work profile is created.](media/enroll-work-profile-android/work-profile-complete-1911.png)
8. Wait while the app registers your device. When prompted to, sign in with your work account.
9. On the **Company Access Setup** screen, confirm that the work profile is active. Then tap **CONTINUE** to proceed to the next enrollment task.

![Screenshot of Company Access Setup showing work profile is active.](media/enroll-work-profile-android/work-profile-active-1911.png)
10. In the Company Portal app, review the list of settings your organization requires. Update the settings on your device if necessary. Tap **RESOLVE** to open the setting on your device. After you're done updating settings, tap **CONFIRM DEVICE SETTINGS**.

![Screenshot of Company Portal's Update device settings screen highlighting the RESOLVE button and CONFIRM DEVICE SETTINGS button.](media/enroll-work-profile-android/confirm-device-settings-work-profile-2307.png)

1. When setup and enrollment are complete, you're sent back to the setup list, where you should see a green checkmark next to each enrollment task. Tap **DONE**.

    ![Screenshot of Company Portal's Company Access Setup screen, showing completed setup and highlighting Done button.](media/enroll-work-profile-android/work-profile-done-1911.png)
2. Optionally, when prompted to view suggested work apps in Google Play Store, tap **OPEN**. If you're not ready to install apps, you can do it later by going to the Play Store app in your work profile.

    ![Screenshot of Company Portal prompt to open badged version of Google Play.](media/enroll-work-profile-android/get-apps-banner-android-2005.png)

    You can also access available apps from the Company Portal menu &gt; **Get Apps**.

    ![Screenshot of the Company Portal menu, highlighting the Get Apps link.](media/enroll-work-profile-android/updated-drawer-android-2005.png)

## Android Enterprise availability

Work profiles are supported in [countries and regions where Android Enterprise is available](https://support.google.com/work/android/answer/6270910) (opens Google Support website). Company Portal can't set up a work profile on your device if you're outside these areas. If Android Enterprise isn't available in your country or region, ask your support person for other ways to access work resources.

## Update Google Play services

If the version of Google Play services on your device is outdated, you may be unable to enroll your device. [Open Google Play services](https://play.google.com/store/apps/details?id=com.google.android.gms) on your device to check for available updates. For more information about how to update Android apps, see [Update your Android apps](https://support.google.com/googleplay/answer/113412)(opens Google Support website).