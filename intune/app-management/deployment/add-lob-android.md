---
layout: Conceptual
title: Add an Android Line-of-Business App to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-lob-android
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
- FocusArea_Apps_LOB
ms.reviewer: bryanke
ms.subservice: apps
description: Learn about how to add a Android line-of-business (LOB) app to Microsoft Intune.
ms.date: 2026-05-11T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: c443aa68-5fba-1b77-a4aa-78d5fd4f82f6
document_version_independent_id: c443aa68-5fba-1b77-a4aa-78d5fd4f82f6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-lob-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-lob-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-lob-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 31af9ff3-f386-6047-87d9-4f1f7db8f4d2
---

# Add an Android Line-of-Business App to Microsoft Intune - Microsoft Intune | Microsoft Learn

A line-of-business (LOB) app is an app that you add to Intune from an app installation file. This kind of app is typically written in-house. Intune installs the LOB app on the user's device.

Note

For more information about LOB apps and the Google Play Developer Console, see [Managed Google Play private (LOB) app publishing using the Google Developer Console](add-managed-google-play?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console).

Apps for Android Enterprise devices can be deployed by using either Managed Google Play synchronization or direct deployment of an Android installation file (.apk). For information about deploying apps through Managed Google Play, see [Add Managed Google Play apps to Android Enterprise devices with Intune](add-managed-google-play). Direct deployment is only supported for Android Enterprise fully managed and dedicated devices.

Note

If the same app is deployed through both Managed Google Play and as an Android direct LOB app, the version uploaded directly to Intune is installed on the device, regardless of the app version deployed through Managed Google Play.

Note

If multiple versions of the same Android line-of-business app uploaded directly to Intune are assigned to a device, the higher version is installed.

## Select the app type

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, select the **Android** platform, and then select **Line-of-business app**.
4. Choose **Select**. The **Add app** steps are displayed.

## Step 1 - App information

### Select the app package file

1. In the **Add app** pane, click **Select app package file**.
2. In the **App package file** pane, select the browse button. Then, select an Android installation file with the extension **.apk**. The app details will be displayed.
3. When you're finished, select **OK** on the **App package file** pane to add the app.

### Set app information

1. In the **App information**page, add the details for your app. Depending on the app that you chose, some of the values in this pane might be automatically filled in.
    - **Name**: Enter the name of the app as it appears in the company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps appears in the company portal.
    - **Description**: Enter the description of the app. The description appears in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Targeted platform**: From the list, choose the targeted platform on which the app can be installed.
    - **Minimum Operating System**: From the list, choose the minimum operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.
    - **Category**: Select one or more of the built-in app categories, or select a category that you created. Categories make it easier for users to find the app when they browse through the company portal.
    - **Show this as a featured app in the Company Portal**: Display the app prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL appears in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL appears in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app. An example is **HR department**.
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Logo**: Upload an icon that is associated with the app. This icon is displayed with the app when users browse through the company portal.
2. Click **Next** to display the **Scope tags** page.

## Step 2 - Select scope tags (optional)

You can use scope tags to determine who can see client app information in Intune. For full details about scope tags, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

1. Click **Select scope tags** to optionally add scope tags for the app.
2. Click **Next** to display the **Assignments** page.

## Step 3 - Assignments

1. Select the **Required**, **Available for enrolled devices**, or **Uninstall** group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups) and [Assign apps to groups with Microsoft Intune](assign-groups).
2. Click **Next** to display the **Review + create** page.

## Step 4 - Review + create

1. Review the values and settings you entered for the app.
2. When you are done, click **Create** to add the app to Intune.

    The **Overview** blade for the line-of-business app is displayed.

## Step 5: Update a line-of-business app

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps**.
3. Find and select your app from the list of apps.
4. Select **Properties** under **Manage** from the app pane.
5. Select **Edit** next to **App information**.
6. Click on the listed file next to **Select file to update**. The **App package file** pane is displayed.
7. Select the folder icon and browse to the location of your updated app file. Select **Open**. The app information is updated with the package information.
8. Verify that **App version** reflects the updated app package.

If **Check apps from external sources** is enabled on the Android device, the user will be prompted before installing the update. Otherwise the update will be installed automatically.

Note

For the Intune service to successfully deploy a new APK file to the device, you must increment the `android:versionCode` string in the AndroidManifest.xml file in your APK package.

Important

When you upload a new version of an Android line-of-business app, existing app configuration policies associated with the previous version don't automatically apply to the updated app. To apply app configuration settings to the updated app, create and assign a new app configuration policy that targets the new app version.

## Known issues

The following known issues affect app install status reporting for Android Enterprise line-of-business (LOB) apps that are deployed directly to devices. In all cases, the app installs correctly on the device. Only the status displayed in the Microsoft Intune admin center is affected. These issues are being actively addressed.

- **Lower version shows as Installed instead of In-Conflict.** When two versions of the same LOB app are assigned to a device, the lower version may continue to show as **Installed** in the admin center instead of **In-Conflict**.
- **Play Store app shows Waiting for install or doesn't appear in the report.** When the same app is assigned as both a Managed Google Play app and a direct LOB app, the Play Store app policy may show **Waiting for install** or may not appear in the policy report, instead of showing **In-Conflict**.
- **Conflict resolution and reporting are inconsistent for mixed install intents.** When two versions of the same LOB app are assigned with different install intents (for example, **Install** for one version and **Uninstall** for another), conflict resolution and reporting may not behave as expected.