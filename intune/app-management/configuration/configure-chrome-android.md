---
layout: Conceptual
title: Configure Google Chrome for Android Devices Using Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-chrome-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Android
- FocusArea_Apps_Add
ms.subservice: apps
description: Use Intune configuration policies with Google Chrome for Android devices.
ms.date: 2024-11-21T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: esalter
locale: en-us
document_id: b92909cd-5383-d6eb-660c-c19185c910b0
document_version_independent_id: b92909cd-5383-d6eb-660c-c19185c910b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/configure-chrome-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/configure-chrome-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/configure-chrome-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 16046e18-69ae-4722-9d96-161dfd796097
---

# Configure Google Chrome for Android Devices Using Intune - Microsoft Intune | Microsoft Learn

You can use an Intune app configuration policy to configure Google Chrome for Android devices. The settings for the app can be automatically applied. For example, you can specifically set the bookmarks and the URLs that you would like to block or allow.

## Prerequisites

- The user's Android Enterprise device must be enrolled in Intune. For more information, see [Set up enrollment of Android Enterprise personally-owned work profile devices](../../device-enrollment/android/setup-personal-work-profile).
- Google Chrome is added as a Managed Google Play app. For more information about Managed Google Play, see [Connect your Intune account to your Managed Google Play account](../../device-enrollment/android/connect-managed-google-play).

## Add the Google Chrome app to Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create** then add the **Managed Google Play** app.
3. Go to Managed Google Play, search with **Google Chrome** and approve.

    ![Search and approve Google Chrome](media/configure-chrome-android/search.png)
4. Assign Google Chrome to a group as a required app type. Google Chrome is deployed automatically when the device is enrolled into Intune.

For more information about adding a Managed Google Play app to Intune, see [Managed Google Play store apps](../deployment/add-managed-google-play#managed-google-play-store-apps).

## Add app configuration for managed AE devices

1. From the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** &gt; **Configuration** &gt; **Create** &gt; **Managed devices**.
2. Set the following details:

    - **Name** - The name of the profile that appears in the portal.
    - **Description** - The description of the profile that appears in the portal.
    - **Device enrollment type** - This setting is set to **Managed devices**.
    - **Platform** - Select **Android**.

    ![Add Google Chrome Configuration policy](media/configure-chrome-android/add-policy.png)
3. Select **Associated app** to display the **Associated app** pane. Find and select **Google Chrome**. This list contains [Managed Google Play apps that you've approved and synchronized with Intune](../deployment/add-managed-google-play).

    ![Select Google Chrome under Associated app](media/configure-chrome-android/associated-app.png)
4. Select **Configuration settings**, select **Use configuration designer**, and then select **Add** to select the configuration keys.

    ![Add Use configuration designer](media/configure-chrome-android/configuration.png)

    Below is the example of the common settings:

    - **Block access to a list of URLs**: `["*"]`
    - **Allow access to a list of URLs**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Managed Bookmarks**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Incognito mode availability**: `Incognito mode disabled`

    Once the configuration settings are added using the configuration designer, they'll be listed in a table.

    ![Common settings](media/configure-chrome-android/common-settings.png)

    The above settings create bookmarks and block access to all URLs except `baidu.com`, `youtube.com`, `chromium.org`, and `chrome://`.
5. Select **OK** and **Add** to add your configuration policy to Intune.
6. Assign this configuration policy to a user group. For more information, see [Assign apps to groups with Microsoft Intune](../deployment/assign-groups).

## Verify the device settings

Once the Android device is enrolled with Android Enterprise, the managed Google Chrome app with the portfolio icon will be deployed automatically.
![Managed Google Chrome with the portfolio icon](media/configure-chrome-android/chrome-icon.png)
Launch Google Chrome and you'll find the settings applied.

Bookmarks:![View bookmarks](media/configure-chrome-android/bookmarks.png)

Blocked URL:![Blocked URL](media/configure-chrome-android/blocked-url.png)

Allow URL:![Allow URL](media/configure-chrome-android/allowed-url.png)

Incognito tab:![Incognito tab](media/configure-chrome-android/incognito-tab.png)

## Troubleshooting

1. Check Intune to monitor the policy deployment status.

    ![Monitor the policy deployment status](media/configure-chrome-android/monitor-status.png)
2. Launch Google Chrome and visit **chrome://policy**. We can confirm if the settings are applied successfully.

    ![Confirm settings are applied successfully](media/configure-chrome-android/confirm.png)

## Additional information

- [Add app configuration policies for managed Android Enterprise devices](configure-managed-android)
- [Chrome Enterprise policy list](https://cloud.google.com/docs/chrome-enterprise/policies/)