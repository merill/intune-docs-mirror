---
layout: Conceptual
title: Remove Device from Intune Company Portal for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-android
author: abigail-stein2
ms.author: abigailstein
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to remove a device from Company Portal for Android and uninstall the Company Portal app.
ms.date: 2026-11-05T00:00:00.0000000Z
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
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
platformId: bd86f273-db86-37a9-daf7-29e389ad9e2d
---

# Remove Device from Intune Company Portal for Android - Microsoft Intune | Microsoft Learn

Remove an enrolled device so that your organization no longer manages it. After you remove the device from Company Portal:

- The device loses access to your organization's internal apps and websites.
- The device no longer appears in Company Portal. This change applies to enrolled devices and devices you set up just to access work emails.
- You can no longer install apps in Company Portal.
- Your organization no longer enforces setting requirements and restrictions, such as device PIN, disabling the camera, or prohibiting screenshots.

Note

This article is for devices set up by using the [Intune Company Portal app for Android](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). It doesn't apply to devices enrolled by using the [Microsoft Intune app](https://play.google.com/store/apps/details?id=com.microsoft.intune). You can't unenroll or remove a corporate-owned device by using the Microsoft Intune app.

## Remove device in Company Portal app

1. Sign in to the Company Portal app with your work account.
2. Select **Devices** and then select the device you want to remove.

    ![Screenshot of Company Portal app, highlighting a device called My Android.](media/unenroll-android/remove-device-from-company-portal-2101-01.png)
3. From the menu, select **Remove Device**.

    ![Screenshot of Company Portal app, highlighting the menu button and Remove Device option.](media/unenroll-android/remove-device-from-company-portal-2101-02.png)
4. Select **OK** to finish removing your device.

    ![Screenshot of Company Portal app, Remove this device confirmation, highlighting the OK option.](media/unenroll-android/remove-device-from-company-portal-2101-03.png)

## Disable Company Portal device management

You can remove your device from management by disabling the Company Portal app. After disabling the app, you can uninstall it from your device.

1. Sign in to Company Portal.
2. Select the main menu.

    ![Screenshot of Company Portal app, highlighting the menu button.](media/unenroll-android/remove-intune-company-portal-android-2101-01.png)
3. Select **Remove Company Portal**.

    ![Screenshot of Company Portal app, highlighting Remove Company Portal option in menu.](media/unenroll-android/remove-intune-company-portal-android-2101-02.png)
4. Select **OK** to remove Company Portal and unenroll the device you're on.

    ![Screenshot of Company Portal app, Remove Company Portal confirmation, highlighting the OK option.](media/unenroll-android/remove-intune-company-portal-android-2101-03.png)

Note

If you plan to use the app again, you can temporarily disable it without uninstalling it. After you re-enable the app, you must also re-enroll your device.

## Uninstall the Company Portal app

Company Portal is a device management app, so you can't uninstall it until you remove your device from management. After you remove the device, select and hold the Company Portal app icon until the app menu appears. Then select **Uninstall** to remove the app.

Alternatively, go to your device **Settings** &gt; **Apps** and select **Company Portal** &gt; **Uninstall**.

## Remove the Company Portal app as a device administrator

As a last resort, you can remove the Company Portal app as a device administrator. When you remove the app as a device administrator, you can unenroll your device and uninstall the app.

Tip

If you decline the Microsoft terms of use when signing in to the Company Portal app, you block all subsequent sign-in attempts. To remove the app as a device administrator and uninstall the app, follow the steps in this section. If you didn't mean to decline the Microsoft terms of use, you can reinstall the app and start over.

Device administrator settings might appear differently on your device. Use the option that aligns with your device experience.

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
    2. Select **Company Portal** &gt; **Clear data**.
2. Delete the following folder from your device: **\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal**

### Effects of removing required apps

If you have a company-owned device, your organization might require Company Portal on your device. If you uninstall it, you could lose access to protected work resources such as email, apps, Wi-Fi, or VPN. You can regain access by reinstalling the app and enrolling your device.