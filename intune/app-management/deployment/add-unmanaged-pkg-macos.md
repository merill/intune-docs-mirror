---
layout: Conceptual
title: Add an Unmanaged macOS PKG App to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-unmanaged-pkg-macos
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
- FocusArea_Apps_MacOS
ms.reviewer: arnab
ms.subservice: apps
description: Learn about how to add an unmanaged macOS PKG app to Microsoft Intune.
ms.date: 2026-04-14T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 59ea9146-fb5f-6efc-7efb-33c8a446bb45
document_version_independent_id: 59ea9146-fb5f-6efc-7efb-33c8a446bb45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-unmanaged-pkg-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-unmanaged-pkg-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-unmanaged-pkg-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 77918101-60d1-3e51-a46a-6e6ba37da60a
---

# Add an Unmanaged macOS PKG App to Microsoft Intune - Microsoft Intune | Microsoft Learn

Use the information in this article to help you add an unmanaged macOS PKG app to Microsoft Intune. To deploy a managed PKG app, see [How to add macOS line-of-business (LOB) apps to Microsoft Intune.](add-lob-macos)

## Prerequisites

The following prerequisites must be met before an unmanaged macOS PKG app is installed on macOS devices.

- Devices are managed by Intune.
- The PKG file is smaller than 8 GB in size.
- The [Microsoft Intune management agent for macOS](management-agent-macos) version 2308.006 or greater is installed.
- The PKG file successfully runs using the `installer` command in Terminal.

## Important considerations for deploying PKG apps

The unmanaged macOS PKG app-type can install the following types of PKG apps:

- Nonflat packages with a hierarchical structure
- Component packages
- Unsigned packages
- Packages without a payload
- Packages that install apps outside `/Applications/`
- Custom packages with scripts

Note

These types of PKG apps may not successfully deploy using the managed LOB app-type.

The containing app files can be listed under the **Included apps** section in the **Detection rules** tab in order, starting with the parent app to be used in reports.

## Select the app type

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, select the **macOS** platform, and then select **macOS app (PKG)**.
4. Choose **Select**. The **Add app** steps are displayed.

## Step 1 – App information

Select the app package file:

1. In the **Add app** pane, click **Select app package file**.
2. In the **App package file** pane, select the browse button. Then, select a macOS PKG file with the extension *.pkg*. The app details will be displayed.
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
2. Select **Next** to set the requirements.

## Step 2 – Program

You can optionally configure a preinstall script and a post-install script to customize the app install.

**Pre-install script**: Provide a script that runs before the app is installed. Only when the preinstall script returns zero (indicating success), the app proceeds to install. If the preinstall script returns a nonzero code (indicating failure), the app doesn't install and reports its installation status as "failed". The preinstall script runs again for failed installations at the next device check-in (sync).

**Post-install script**: Provide a script that runs after the app installs successfully. If provided, the post-install script runs after a successful app installation. Irrespective of the post-install script run status, an installed app reports its installation status as "success".

Note

- Each pre-install or post-install script must be less than 15360 characters long.
- The Microsoft Intune management agent for macOS version 2309.007 or greater is required to configure pre-install and post-install scripts for macOS PKG apps.
- For more details on configuring pre-install and post-install scripts, refer to [Prerequisites of shell scripts](../../device-management/tools/run-shell-scripts-macos#prerequisites).

## Step 3 – Requirements

You can choose the minimum operating system required to install this app.

**Minimum Operating System**: From the list, choose the minimum operating system version on which the app can be installed. If you assign the app to a device with an earlier operating system, it will not be installed.

## Step 4 – Detection rules

You can use detection rules to choose how an app installation is detected on a managed macOS device.

**Ignore app version**: Select **Yes** to install the app if the app isn't already installed on the device. This will only look for the presence of the app bundle ID. For apps that have an autoupdate mechanism, select **Yes**. Select **No** to install the app when it isn't already installed on the device, or if the deploying app's version number doesn't match the version that's already installed on the device.

**Included apps**: Provide the apps that are contained in the uploaded file. Included app bundle IDs and build numbers are used for detecting and monitoring app installation status of the uploaded file. Included apps list should only contain the application(s) installed by the uploaded file. Any other type of file that isn't an application should be excluded from the **Included apps** list. If **Included apps** list contains files that aren't applications or if all the listed apps aren't installed, app installation status doesn't report success.

Note

- If a PKG package contains multiple apps, only one of these can be shown in the related app reports.
- The first app/bundle ID in the Included apps list is the one that will be reported on. The list can be re-ordered if necessary.
- In the case of the Intune Company Portal app, there are many additional libraries included in the PKG which can safely be removed (using the trash can icon). This will leave only a single app bundle ID: `com.microsoft.CompanyPortalMac`

Tip

The `CFBundleIdentifier` and `CFBundleShortVersionString` can be found under the `<app_name>.app/Contents/Info.plist` file of an installed app on a Mac.

Alternatively, Mac Terminal can be used to look up and confirm the included app details of an installed app at a known location.

For example, to look up the bundle ID and build number of Company Portal, run the following:`defaults read /Applications/Company\ Portal.app/Contents/Info CFBundleIdentifier`Then, run the following:`defaults read /Applications/Company\ Portal.app/Contents/Info CFBundleShortVersionString`For apps added to Intune, [you can use the Intune admin center to get the app bundle ID](../collect-bundle-ids).

## Step 5 – Select scope tags (optional)

You can use scope tags to determine who can see client app information in Intune. For full details about scope tags, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags). 1. Click **Select scope tags** to optionally add scope tags for the app. 2. Select **Next** to display the **Assignments** page.

## Step 6 - Assignments

You can select either the **Required** or **Available** group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups) and [Assign apps to groups with Microsoft Intune](assign-groups).

Note

A macOS app deployed using Intune agent will not automatically be removed from the device when the device is retired. The app and data it contains will remain on the device. It is recommended that the app is removed prior to retiring the device.

1. For the specific app, select either the **Required** or **Available** assignment type.
2. Select **Next** to display the **Review + create** page.

Note

When you upload a new version of an available app to Intune, users do not need to take any action. It installs automatically.

## Step 7 – Review + create

1. Review the values and settings you entered for the app.
2. When you're done, select **Create** to add the app to Intune. The **Overview** pane for the macOS PKG app is displayed.

The app you have created appears in the apps list where you can assign it to the groups you choose. For help, see [How to assign apps to groups](assign-groups).

## Known issues

- The **Uninstall** assignment type isn't available. Only Required and Available assignments are currently supported.
- The Intune Company Portal shows the **Pending** state even after a successful app install. Specifically, **Available** apps show as **Pending** after the user clicks the **Install** button in the Company Portal app even after apps have successfully installed. Users may reattempt installation by clicking **Check status** on the local device in the **Devices** tab of the Company Portal app. Reporting in the Intune Admin Console isn't affected by this issue. This issue is being actively addressed to be resolved.

## Troubleshooting

macOS app installation may not be successful due to any of the following reasons provided in the table below. To resolve these errors, follow the remediation steps. If the app remains assigned, failed installations are retried at the next agent check-in with up to three time retries.

| Error code | Error message | Remediation steps |
| --- | --- | --- |
| 0x87D30137 | The device doesn't meet the minimum OS requirement set by the admin. | Update macOS to the minimum OS version required by the admin. |
| 2016214710 | The preinstall script provided by the admin failed. | This might be expected if the preinstall script is waiting for a condition to become true before the app install can proceed. The failed preinstall script will be tried again at the next device check-in. Check the preinstall script if the error persists. |
| 0x87D3012F, 0x87D30130, 0x87D30133, 0x87D30134, 0x87D30136, | The app couldn't be installed due to an internal error. Contact Intune support if the error persists. | Something went wrong while installing the app using Intune. Try installing the app manually or try creating a new macOS app profile containing the app. Contact Intune support if the error persists. |

Note that post-install script failure isn't reported. A successful app installation followed by a failed post-install script will report the app installation status as "success".