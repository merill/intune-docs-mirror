---
layout: Conceptual
title: Move Android devices from device administrator to personally owned work profile management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/migrate-device-admin-to-work-profile
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Move Android devices from device administrator to personally owned work profile management in Intune.
ms.date: 2024-06-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: esalter
locale: en-us
document_id: 076380c3-4ba8-a626-c880-c43f76065c51
document_version_independent_id: 076380c3-4ba8-a626-c880-c43f76065c51
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/migrate-device-admin-to-work-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/migrate-device-admin-to-work-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/migrate-device-admin-to-work-profile.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 835454a2-a6af-a15d-18a1-782250b2b342
---

# Move Android devices from device administrator to personally owned work profile management - Microsoft Intune | Microsoft Learn

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

You can help users move their Android devices from device administrator to personally owned work profile management by using the compliance setting to **Block devices managed with device administrator**. This setting lets you make devices noncompliant if they're managed with device administrator.

When users see that they're out of compliance for this reason, they can tap **Resolve**. They are directed to a checklist that guides them through these steps:

1. Unenroll from device administrator management.
2. Enroll into personally owned work profile management.
3. Resolve any compliance issues.

## Prerequisites

- Users must have [Android device administrator enrolled devices](manage-device-administrator) with Android Company Portal version 5.0.4720.0 or later.
- Set up Android personally owned work profile management by [connecting your Intune tenant account to your Android Enterprise account](connect-managed-google-play).
- [Set Android Enterprise personally owned work profile enrollment](setup-personal-work-profile) for the group of users who are moving to personally owned work profile.
- Consider increasing your user device limits. When you unenroll devices from device administrator management, your device records might not be immediately removed. To provide cushion during this period, you might need to increase device limit capacity. This increase is so that the users can enroll into personally owned work profile management.
    - [Configure Microsoft Entra device settings](/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings) for Maximum number of devices per user.
    - Adjust the [Intune device limit restrictions](../create-device-limit-restrictions) by setting the device limit.

## Create device compliance policy

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices**.
2. Select **Compliance** &gt; **Create Policy**.

    ![Create policy](media/migrate-device-admin-to-work-profile/create-policy.png)
3. On the **Create a policy** page, set **Platform** to **Android device administrator** &gt; **Create**.
4. On the **Basics** page, type in the **Name** and **Description** &gt; **Next**.

    ![Basics page](media/migrate-device-admin-to-work-profile/basics.png)
5. On the **Compliance settings** page, in the **Device Health** section, set **Block devices managed with device administrator** to **Yes** &gt; **Next**.

    ![Block devices](media/migrate-device-admin-to-work-profile/block-devices.png)
6. On the **Actions for noncompliance** tab, you can configure the [available actions for noncompliance](../../device-security/compliance/configure-noncompliance-actions#available-actions-for-noncompliance) to customize the end-user experience for this flow.

    ![Noncompliance actions](media/migrate-device-admin-to-work-profile/noncompliance-actions.png)

    Some actions to consider include:

    - **Mark device noncompliant**: By default, this action is set to zero (0) days, marking devices as noncompliant immediately. You can increase the number of days to give users a grace period. During this grace period, they can see the flow to move to work profile management without yet being marked noncompliant. For example, you can set this action to 14 days to give users the time to move from device administrator to work profile management without the risk of losing access to resources.
    - **Send push notification to end user**: Configure this action to send push notifications to the device administrator devices. When a user selects the notification, the Android Company Portal opens to the **Update device settings** screen. Users can start the flow from there to set up their work profile.
    - **Send email to end user**: Use this action to notify users about the move from device administrator to work profile management. In the email, you can include the following URL. When this URL is selected, it launches the Android Company Portal to the Update device settings page. From this page, they can start the flow to move to work profile management.

        - `https://portal.manage.microsoft.com/UpdateSettings.aspx`.
        - For US government, you can use this link instead: `https://portal.manage.microsoft.us/UpdateSettings.aspx`.

        Note

        - Of course, you can use user-friendly hyper-text for the links in your communication with users. However, don't use URL-shorteners because the links may not work if changed that way.
        - If the Android Company Portal is open and in the background, when a user taps the link they might go to the last page they had open instead.
        - Users must tap the link on an Android device to open the Intune Company Portal app. If they paste the link in a browser, the app won't open.
7. Select **Next**.
8. On the **Scope tags** page, select any scope tags you want to include.
9. On the **Assignments** page, assign the policy to a group that has devices enrolled with device administrator management &gt; **Next**.
10. On the **Review + create** page, confirm all your settings, and then select **Create**.

## Troubleshooting

The [end user flow to move to new device management setup](../../user-help/enrollment/migrate-device-management-android) guides users through unenrolling from device administrator management. It also helps users set up work profile management on their personal devices. Users must have [Android device administrator enrolled devices](manage-device-administrator) with Android Company Portal version 5.0.4720.0 or later.

### User sees an error after tapping Resolve

If users see an error after tapping the **Resolve** button, it's likely because of one of these reasons:

- Work profile enrollment isn't set up correctly. Either an Android Enterprise account isn't connected or enrollment restrictions are set to block personally owned work profile enrollment.
- The device is running Android 4.4 or earlier, which doesn't support personally owned work profile enrollment.
- The device manufacturer doesn't support personally owned work profile enrollment on the device model.

### Resolve button doesn't appear on the user's device

The **Resolve** button won't appear on the user's device if the user enrolls into device administrator management after they are targeted with the device compliance policy explained above.

To get the **Resolve** button to appear, the user must postpone setup and restart the process from the notification.

To avoid this condition, use enrollment restrictions to block enrollment into device administrator management.

### User sees an error after tapping URL to Update device settings page

Users might see an error page in the browser when they tap the URL to the **Update device settings page** of the Android Company Portal. This error can be caused by one of the following conditions:

- The device isn't an Android.
- The Android device doesn't have the Company Portal app.
- The Android Company Portal version is earlier than 5.0.4720.0.
- The Android device uses Android 6 or earlier.