---
layout: Conceptual
title: Add Web Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-web
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Web
ms.reviewer: bryanke
ms.subservice: apps
description: Learn about adding web apps (client-server applications) to Microsoft Intune.
ms.date: 2025-11-18T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b638c963-2702-5b2f-0da7-1b419051ffc9
document_version_independent_id: b638c963-2702-5b2f-0da7-1b419051ffc9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-web.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-web
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-web.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7f1129fd-ee67-3105-e36e-38ff12d2e57e
---

# Add Web Apps to Microsoft Intune - Microsoft Intune | Microsoft Learn

Intune supports a variety of app types, including web apps. A web app is a client-server application. The server provides the web app, which includes the UI, content, and functionality. Additionally, modern web-hosting platforms commonly offer security, load balancing, and other benefits. A web app is separately maintained on the web. You use Microsoft Intune to point to this app type. You also assign the groups of users that can access this app.

Before you can manage and assign an app for your users, add the app to Intune.

Intune creates a shortcut to the web app on the user's device. For iOS/iPadOS devices, a shortcut to the web app is added to the home screen. For macOS devices, end users can pin web apps to the dock on their macOS device. For Android Device Admin devices, a shortcut to the web app is added to the Intune company portal widget and the widget needs to be pinned manually by the user. For Windows devices, a shortcut to the web app is placed on the Start Menu.

Note

A browser must be installed on the user's device to launch web apps.

For Android Enterprise devices, see [Managed Google Play web links](add-managed-google-play#managed-google-play-web-links).

For iOS devices, web clips (pinned web apps) open in Microsoft Edge when required to open in a protected browser.

## Add a web app to Intune

To add an app to Intune as a shortcut to an app on the web, do the following:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the **Other** types, select **Web link**. Other options include **iOS/iPadOS web clip**, **macOS web clip**, and **Windows web link**.
4. Click **Select**. The **Add app** steps are displayed.
5. On the **App information**page, add the following information:
    - **Name**: Enter the name of the app as it is to be displayed in the company portal.

        Note

        If you change the name of the app through Intune after you have deployed and installed the app, the app will no longer be able to be targeted using commands.
    - **Description**: Enter a description for the app. This description is displayed to users in the company portal.
    - **Publisher**: Enter the name of the publisher of this app.
    - **App URL**: Enter the URL of the website that hosts the app that you want to assign.

        Note

        Once you deploy a web link app, the App URL cannot be modified, which is by design.
    - **Require a managed browser to open this link**: Select this option to assign to your users a link to a website or web app that they can open in Microsoft Edge. Microsoft Edge must be installed on their device.

        Note

        iOS/iPadOS web clips that require a managed browser will not work with [home screen layout policies.](../../device-configuration/templates/ref-device-features-apple)
    - **Full screen**: [iOS/iPadOS only] If configured to **Yes**, launches the web clip as a full-screen web app without a browser. Additionally, there's no URL or search bar, and no bookmarks.
    - **Ignore manifest scope**: [iOS/iPadOS only] If configured to **Yes**, a full screen web clip can navigate to an external web site without showing Safari UI. Otherwise, Safari UI appears when navigating away from the web clip's URL. This setting has no effect when **Full screen** is set to **No**. Available in iOS 14 and later.
    - **Precomposed**: [iOS/iPadOS only] If configured to **Yes**, prevents Apple's application launcher (SpringBoard) from adding "shine" to the icon.
    - **Target application bundle identifier**: [iOS/iPadOS only] Enter the application bundle identifier that specifies the application that opens the URL. Available in iOS 14 and later.
    - **Category**: Optionally, select one or more of the built-in app categories, or a category that you created. Doing so makes it easier for users to find the app when they browse the company portal.
    - **Show this as a featured app in the Company Portal**: Select this option to display the app suite prominently on the main page of the company portal when users browse for apps.
    - **Information URL**: Link people to a website or documentation that has more information about the app. The information URL will be visible to users in Company Portal.
    - **Privacy URL**: Provide a link for people who want to learn more about the app's privacy settings and terms. The privacy URL will be visible to users in Company Portal.
    - **Developer**: The name of the company or Individual that developed the app. This information will be visible to people signed in to the admin center.
    - **Owner**: The name of the person in your organization who manages licensing or is the point-of-contact for this app. This name will be visible to people signed in to the admin center.
    - **Notes**: Add additional notes about the app. Notes will be visible to people signed in to the admin center.
    - **Logo**: Upload an icon that will be associated with the app. This icon is displayed with the app when users browse the company portal.

    Note

    On Windows devices it is expected that the configured icon does not apply within the start menu. The Microsoft Edge logo is displayed instead.
6. Click **Next** to display the **Scope tags** page.
7. Click **Select scope tags** to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
8. Click **Next** to display the **Assignments** page.
9. Select the group assignments for the app. For more information, see [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).

Note

iOS/iPadOS and macOS web clips that are assigned as **Required** cannot be installed as removable. To remove these web clips, you must change their assignment to **Uninstall**. If you delete the assignment without first changing it to **Uninstall**, the web clip will remain on the device and cannot be removed by the user. 10. Click **Next** to display the **Review + create** page. Review the values and settings you entered for the app.

1. When you are done, click **Create** to add the app to Intune.

    The **Overview** blade of the app you've created is displayed.

End-users can launch web apps directly from the Windows Company Portal app by selecting the web app and then choosing the option **Open in browser**. The published web URL is opened directly in the web browser.