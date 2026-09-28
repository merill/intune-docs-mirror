---
layout: Conceptual
title: Line-of-Business App Versioning in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/ref-lob-app-versioning
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.reviewer: bryanke
ms.subservice: apps
description: Introduces how app versions are used in Intune when an app is added or updated.
ms.date: 2024-11-18T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 70304bdb-b0e6-1340-21af-7a18b719be45
document_version_independent_id: 70304bdb-b0e6-1340-21af-7a18b719be45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/ref-lob-app-versioning.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/ref-lob-app-versioning
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/ref-lob-app-versioning.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c1f747e2-1772-2d36-f21e-7a99c3577105
---

# Line-of-Business App Versioning in Intune - Microsoft Intune | Microsoft Learn

When you add or update a line-of-business (LOB) app in Microsoft Intune, the version property of the app is extracted to detect and install the app on devices. The version value is stored in the **identityVersion** property of the LOB app entity. When the LOB app is updated, the Intune service compares the versions of the existing and updated app packages. If the versions are the same, the Intune service rejects the update.

The following items are considered as the version property of the app:

- App package-specific versions. Some app types contain more than one of these properties.
- The **InternalVersion** property that's specified in the app's metadata. This value refers to the internal tracking version for the content of the app, specifically when the app is updated.
- The **MetadataVersion** property that's specified in the app's metadata. This value refers to the internal tracking version for the metadata changes that have been applied to the app. The property is reset for each revision of the **InternalVersion** property.

## Locations where you can view the app version

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), you can view the app version in the following locations:

- When you add the app to Intune, the version is displayed in the **App package file** pane. The version value will be used for the **identityVersion** property.

    ![Select app package file](media/ref-lob-app-versioning/apps-lob-app-versioning-01.png)
- When you select an existing LOB app, the version is displayed in the details pane. The version value is the value of the **identityVersion** property.

    ![View an existing app](media/ref-lob-app-versioning/apps-lob-app-versioning-02.png)
- You can select to view the version in the list of apps. The version value is the value of the **identityVersion** property.

    ![View app versions](media/ref-lob-app-versioning/apps-lob-app-versioning-03.png)

You can see the version when you install the app from the Company Portal app.

![View app version during installation](media/ref-lob-app-versioning/apps-lob-app-versioning-03.png)

- For .appx and .apk files, the version value is the value of the **identityVersion** property.
- For other types of files, the version value is the value of the **InternalVersion** property in the app's metadata.

## iOS app packages

The iOS app package (.ipa) files contain two version-related keys:

- CFBundleShortVersionString: This key stores the version number.
- CFBundleVersion: This key stores the build number.

For more information about these keys, see [Apple Technical Note TN2420: Version Numbers and Build Numbers](https://developer.apple.com/library/content/technotes/tn2420/_index.html).

Currently, Intune uses the **CFBundleVersion** value for the **identityVersion** property of the [iosLobApp](/en-us/graph/api/resources/intune-apps-ioslobapp?view=graph-rest-beta&amp;preserve-view=true) entity.

### Extract the version number and build number of the iOS app

To manually extract the version number and build number of an .ipa file in Windows, follow these steps:

1. Rename the *&lt;AppName&gt;.ipa* file to *&lt;AppName&gt;.zip*.
2. Extract the *&lt;AppName&gt;.zip* file to a folder.
3. Go to the folder that contains the extracted files, open the `Payload\<AppName>.app` folder, and locate the Info.plist file.
4. Open the Info.plist file in a supported editor.
5. Check the values of the CFBundleShortVersionString and CFBundleVersion keys.

## Android app packages

The Android app package (.apk) files contain two version-related attributes:

- `android:versionCode`: An internal version number. This number is used only to determine whether one version is more recent than another (higher numbers indicate more recent versions). This value isn't the version number that's shown to users.
- `android:versionName`: The version number that's shown to users. This attribute can be set as a raw string, or as a reference to a string resource. The string has no other purpose than to be displayed to users. The **versionCode** attribute holds the significant version number used internally.

These attributes are stored in the app manifest file AndroidManifest.xml. For more information, see [Android developer guide: &lt;manifest&gt;](https://developer.android.com/guide/topics/manifest/manifest-element#vcode).

Currently, Intune uses the **versionCode** value for the **identityVersion** property of the [androidLobApp](/en-us/graph/api/resources/intune-apps-androidlobapp?view=graph-rest-beta&amp;preserve-view=true) entity.

### Extract the versionCode and versionName attributes of the Android app

To manually extract the attributes of an .apk file in Windows, follow these steps:

1. [Install the Apktool](https://ibotpeaches.github.io/Apktool/install/).
2. Run the Apktool to decode the .apk file to a folder. For example, run the following command:

    ```console
    apktool d <AppName>.apk -o <OutputFolder>
    ```
3. Go to the &lt;OutputFolder&gt; folder, and open the AndroidManifest.xml file in an editor.
4. Check the values of the `android:versionCode` and `android:versionName` attributes. Here's an example:

    ```xml
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
           package="com.realtechvr.nogravity"
           android:versionCode="17"
           android:versionName="1.1.7"
           android:installLocation="preferExternal" >
     ...
    </manifest>
    ```

Note

The third-party products that this article discusses are manufactured by companies that are independent of Microsoft. Microsoft makes no warranty, implied or otherwise, about the performance or reliability of these products.