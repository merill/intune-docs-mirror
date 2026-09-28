---
layout: Conceptual
title: Add a macOS DMG App to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-dmg-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- macOS
- FocusArea_Apps_LOB
- FocusArea_Apps_MacOS
ms.reviewer: arnab
ms.subservice: apps
description: Add a macOS DMG app to Microsoft Intune.
ms.date: 2026-04-14T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 160bcc67-5b7b-a4be-d600-1833d601b576
document_version_independent_id: 160bcc67-5b7b-a4be-d600-1833d601b576
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-dmg-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-dmg-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-dmg-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 56d23b7e-2458-0c9a-efc8-2ea3ec3904f5
---

# Add a macOS DMG App to Microsoft Intune - Microsoft Intune | Microsoft Learn

Use the information in this article to help you add a macOS DMG app to Microsoft Intune. A DMG app is a disk image file that contains one or more applications within it. Many common applications for macOS are available in DMG format. For more information about how to create a disk image file, see [Apple's website](https://support.apple.com/guide/disk-utility/create-a-disk-image-dskutl11888/mac).

Note

The DMG file must contain one or more files with .app extensions. DMG files containing other types of installer files will not be installed.

## Prerequisites

The following prerequisites must be met before a macOS DMG app is installed on macOS devices.

- Devices are managed by Intune.
- DMG app is smaller than 8 GB in size.
- The [Microsoft Intune management agent for macOS](management-agent-macos) is installed.

Note

The full disk access permission is required to update or delete DMG apps. Intune automatically requests the permission when a DMG app policy is assigned on macOS 13 and higher.

## Important considerations for deploying DMG apps

A single DMG should only contain a single application file or multiple application files that are dependent on one another. The containing application files can be listed under the **Included apps** section in the **Detection rules** tab in order starting with the parent app to be used in reports.

It is not recommended that multiple apps that are not dependent on each other are installed using the same DMG file. If multiple independent apps are deployed using the same DMG app, failure to install one app will cause other apps to be re-installed. In this case, monitoring reports consider the DMG installation a failure as well.

Note

You can update apps of type **macOS apps (DMG)** deployed using Intune. Edit a DMG app that is already created in Intune by uploading the update for the app with the same bundle identifier as the original DMG app. In addition, you must use the Microsoft Intune agent for macOS version 2304.039 or greater. Apps deployed as **Required** automatically update. For apps deployed as **Available**, the user must open Company Portal and select **Reinstall** to get the updated version.

## Select the app type

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, select the **macOS** platform, and then select **macOS app (DMG)**.
4. Choose **Select**. The **Add app** steps are displayed.

## Step 1 – App information

Select the app package file:

1. In the **Add app** pane, click **Select app package file**.
2. In the **App package file** pane, select the browse button. Then, select a macOS DMG file with the extension *.dmg*. The app details will be displayed.
3. When you're finished, select **OK** on the **App package file** pane to add the app.

### Set app information

1. In the **App information** page, add the details for your app. Depending on the app that you chose, some of the values in this pane might be automatically filled in.

    - **Name**: Enter the name of the app as it appears in the policy name and company portal. Make sure all app names that you use are unique. If the same app name exists twice, only one of the apps appears in the company portal.
    - **Description**: Enter the description of the app. The description appears in the company portal.
    - **Publisher**: Enter the name of the publisher of the app.
    - **Category**: Select one or more of the built-in app categories, or select a category that you created. Categories make it easier for users to find the app when they browse through the company portal.
    - **Information URL**: Optionally, enter the URL of a website that contains information about this app. The URL appears in the company portal.
    - **Privacy URL**: Optionally, enter the URL of a website that contains privacy information for this app. The URL appears in the company portal.
    - **Developer**: Optionally, enter the name of the app developer.
    - **Owner**: Optionally, enter a name for the owner of this app. An example is HR department.
    - **Notes**: Enter any notes that you want to associate with this app.
    - **Logo**: Upload an icon that is associated with the app. This icon is displayed with the app when users browse through the company portal.
2. Click **Next** to set the requirements.

## Step 2 – Requirements

You can choose the minimum operating system required to install this app.

**Minimum Operating System**: From the list, choose the minimum operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.

## Step 3 – Detection rules

You can use detection rules to choose how an app installation is detected on a managed macOS device.

**Ignore app version**: Select **Yes** to install the app if the app is not already installed on the device. This will only look for the presence of the app bundle ID. For apps that have an auto-update mechanism, select **Yes**. Select **No** to install the app when it is not already installed on the device, or if the deploying app's version number does not match the version that's already installed on the device.

Note

To **Uninstall** group assignments, consider the **Ignore app version** setting. When **Ignore app version** is set to **No**, the app bundle ID and version number must match to remove the app. When **Ignore app version** is set to **Yes**, only the app bundle ID must match to remove the app.

**Included apps**: Provide the apps that are contained in the uploaded file. Included app bundle IDs and build numbers are used for detecting and monitoring app installation status of the uploaded file. Included apps list should only contain the application(s) installed by the uploaded file in **Applications** folder on Macs. Any other type of file that is not an application or an application that is not installed to **Applications** folder should be excluded from the **Included apps** list. If **Included apps** list contains files that are not applications or if all the listed apps are not installed, app installation status does not report success.

Note

- The first app on the Included apps list is used for identifying the app when multiple apps are present in the DMG file.
- Mac Terminal can be used to lookup and confirm the included app details of an installed app. For example, to look up the bundle ID and build number of Company Portal, run the following:

    `defaults read /Applications/Company\ Portal.app/Contents/Info CFBundleIdentifier`

    Then, run the following:

    `defaults read /Applications/Company\ Portal.app/Contents/Info CFBundleShortVersionString`
- Alternatively, the `CFBundleIdentifier` and `CFBundleShortVersionString` can be found under the `<app_name>.app/Contents/Info.plist` file of a mounted DMG file on a Mac.
- For apps added to Intune, [you can use the Intune admin center to get the app bundle ID](../collect-bundle-ids).

## Step 4 – Select scope tags (optional)

You can use scope tags to determine who can see client app information in Intune. For full details about scope tags, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags). 1. Click Select scope tags to optionally add scope tags for the app. 2. Click Next to display the Assignments page.

## Step 5 - Assignments

You can select the **Required**, **Available**, or **Uninstall** group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups) and [Assign apps to groups with Microsoft Intune](assign-groups).

Note

A macOS app deployed using Intune agent will not automatically be removed from the device when the device is retired. The app and data it contains will remain on the device. It is recommended that the app is removed prior to retiring the device.

1. For the specific app, select an assignment type:

    - **Required**: The app is installed to `/Applications/` directory on devices in the selected groups.
    - **Available**: The app is available on devices in the selected groups.
    - **Uninstall**: The app is uninstalled from `/Applications/` directory on devices in the selected groups.
2. Click **Next** to display the **Review + create** page.

## Step 6 – Review + create

1. Review the values and settings you entered for the app.
2. When you are done, click **Create** to add the app to Intune. The **Overview** pane for the macOS DMG app is displayed.

The app you have created appears in the apps list where you can assign it to the groups you choose. For help, see [How to assign apps to groups](assign-groups).

Note

If the *.dmg* file contains multiple apps, then Microsoft Intune will only report that the app is successfully installed when all installed apps are detected on the device.

When you upload a new version of an available app to Intune, users must select **Install** or **Reinstall** in Company Portal to update the app on their device.