---
layout: Conceptual
title: Remove device from Intune Company Portal for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to remove a device from Company Portal for Android and uninstall the Company Portal app.
ms.date: 2024-07-01T00:00:00.0000000Z
ms.reviewer: esalter
locale: en-us
document_id: 5f36f418-0120-4e3b-208d-828870211b5d
document_version_independent_id: 799ea618-f0b4-dc57-5efe-5081cb1f6701
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/unenrollment/unenroll-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/unenrollment/unenroll-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/unenrollment/unenroll-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: bd86f273-db86-37a9-daf7-29e389ad9e2d
---

# Remove device from Intune Company Portal for Android - Microsoft Intune | Microsoft Learn

Remove an enrolled device so that it's no longer managed by your organization. After you remove the device from Company Portal:

- The device loses access to your organization's internal apps and websites.
- The device no longer appears in Company Portal. This applies to enrolled devices and devices you set up just to access work emails.
- You can no longer install apps in Company Portal.
- Setting requirements and restrictions, such as device PIN, disabling the camera, or prohibiting screenshots, are no longer enforced.

Note

This article is for devices set up via the [Intune Company Portal app for Android](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). It doesn't apply to devices enrolled using the [Microsoft Intune app](https://play.google.com/store/apps/details?id=com.microsoft.intune). You can't unenroll or remove a corporate-owned device from the Microsoft Intune app.

## Remove device in Company Portal app

1. Sign in to the Company Portal app with your work account.
2. Select **Devices** and then select the device you want to remove.

    ![Screenshot of Company Portal app, highlighting a device called &quot;My Android&quot;.](media/unenroll-android/remove-device-from-company-portal-2101-01.png)
3. Select the menu &gt; **Remove Device**.

    ![Screenshot of Company Portal app, highlighting the menu button and &quot;Remove Device&quot; option.](media/unenroll-android/remove-device-from-company-portal-2101-02.png)
4. Select **OK** to finish removing your device.

    ![Screenshot of Company Portal app, &quot;Remove this device?&quot; confirmation, highlighting the &quot;OK&quot; option.](media/unenroll-android/remove-device-from-company-portal-2101-03.png)

## Disable Company Portal device management

Another way to remove your device from management is to disable the Company Portal app. Then you can uninstall the app from your device.

1. Sign in to Company Portal.
2. Tap the main menu.

    ![Screenshot of Company Portal app, highlighting the menu button.](media/unenroll-android/remove-intune-company-portal-android-2101-01.png)
3. Tap **Remove Company Portal**.

    ![Screenshot of Company Portal app, highlighting &quot;Remove Company Portal&quot; option in menu.](media/unenroll-android/remove-intune-company-portal-android-2101-02.png)
4. Tap **OK** to remove Company Portal and unenroll the device you're on.

    ![Screenshot of Company Portal app,&quot;Remove Company Portal?&quot; confirmation, highlighting the &quot;OK&quot; option.](media/unenroll-android/remove-intune-company-portal-android-2101-03.png)

Note

You can temporarily disable the app without uninstalling it if you plan to use it again. After you re-enable the app you must also re-enroll your device.

## Uninstall the Company Portal app

Company Portal is a device management app and can't be uninstalled until you remove your device from it. After you remove the device, tap and hold the Company Portal app icon until the app menu appears. Then tap **Uninstall** to remove the app.

Alternatively, go to your device **Settings** &gt; **Apps** and select **Company Portal** &gt; **Uninstall**.

## Remove the Company Portal app as a device administrator

As a last resort, you can remove the Company Portal app as a device administrator. Doing this will allow you to unenroll your device and uninstall the app.

Tip

If you decline the Microsoft terms of use when signing in to the Company Portal app, all subsequent sign-in attempts will be blocked. Follow the steps in this section to remove the app as a device administrator, and then uninstall the app. If you didn't mean to decline the Microsoft terms of use, you can reinstall the app and start over.

Device administrator settings may appear differently on your device. Use the option that aligns with your device experience.

**Option 1**:

1. Go to device **Settings** &gt; **Security** &gt; **Additional Security Settings** &gt; **Device Administrators**.
2. Clear the **Company Portal** selection.

**Option 2**:

1. Select **Settings** &gt; **Security and privacy** &gt; **Other security settings** &gt; **Device admin apps**.
2. Clear the **Company Portal** selection.
3. Follow the onscreen prompts to remove Company Portal and your work profile.

## Remove data collected by the Company Portal app

To remove all data that the Company Portal app for Android stores on your device:

1. Clear app data.
    1. Go to device **Settings** &gt; **Apps**.
    2. Tap **Company Portal** &gt; **Clear data**.
2. Delete the following folder from your device: **\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal**

### Effects of removing required apps

If you have a company-owned device, your organization might require Company Portal on your device. If you uninstall it, you could lose access to protected work resources such as email, apps, Wi-Fi, or VPN. You can regain access by reinstalling the app and enrolling your device.