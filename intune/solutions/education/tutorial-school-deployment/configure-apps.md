---
layout: Conceptual
title: Configure applications with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/configure-apps
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to configure applications with Microsoft Intune in preparation for device deployment.
zone_pivot_groups: platforms-windows-ios
ms.topic: tutorial
ms.date: 2024-05-02T00:00:00.0000000Z
locale: en-us
document_id: a1877142-a30c-d75b-0274-dd3dce3018f9
document_version_independent_id: a1877142-a30c-d75b-0274-dd3dce3018f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/configure-apps.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/configure-apps
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/configure-apps.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: f4086185-92a4-5a45-9d9f-6aee31925c31
---

# Configure applications with Microsoft Intune - Microsoft Intune | Microsoft Learn

With Intune, school IT administrators have access to diverse applications to help students unlock their learning potential. This section discusses tools and resources for adding apps to Intune.

Applications can be assigned to groups:

- If you target apps to a **group of users**, the apps will be installed on any managed devices that the users sign in to.
- If you target apps to a **group of devices**, the apps will be installed on those devices and available to any user who signs in.

## Add apps

![](../../../media/icons/16/check.svg) Add applications to your inventory

::: zone pivot="windows"

# [Intune](#tab/intune)
Intune supports the deployment several application types including desktop apps (msi, exe), Microsoft Store apps, web apps, appxbundle and MSIX.

#### Enterprise Application Management

Enterprise App Management enables you to easily discover and deploy applications and keep them up to date from the Enterprise App Catalog. The Enterprise App Catalog is a collection of prepared Microsoft and non-Microsoft applications. These apps are Win32 apps that are [prepared as Win32 apps](../../../app-management/deployment/create-win32-package) and hosted by Microsoft.

Important

Enterprise App Management is part of Microsoft Intune Suite and available for trial and purchase. For more information, see [Microsoft Intune advanced capabilities](../../../fundamentals/advanced-capabilities).

For more information, see [Enterprise Application Management](../../../app-management/deployment/enterprise-app-management).

#### Win32 apps (MSI, exe)

The addition of desktop applications to Intune should be carried out by repackaging the apps, and defining the commands to silently install them. The process is described in the article [Add, assign, and monitor a Win32 app in Microsoft Intune](../../../app-management/deployment/add-win32).

#### Microsoft Store app (new)

To create Microsoft Store apps in Intune:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** &gt; **All Apps** &gt; **Create**.
2. In **Select app type** pane, select **Microsoft Store app (new)** under the **Store app** section.
3. Choose **Select**at the bottom of the page to begin creating an app from the Microsoft Store. The app creation experience has three steps:
    - App information
    - Assignments
    - Review + create
4. Select **Search the Microsoft Store app** to search for and select the app.
5. Review and change settings as required. 
    Note

    Most administrators choose to deploy store apps in the **system** context on education devices for the fastest installation to all users of a device.
6. Select **Save**.

For more information, see [Add Microsoft Store apps](../../../app-management/deployment/add-microsoft-store).

#### Web apps

To create web applications in Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the **Other** types, select **Windows web link**.
4. Click **Select**. The **Add app** steps are displayed.
5. Provide a URL for the web app, a name, and optionally an icon and description.
6. Select **Save**

For more information, see [Add web apps](../../../app-management/deployment/add-web).

# [Intune For Education](#tab/intune-for-education)
Intune for Education supports the deployment of two types of Windows applications: **web apps** and **desktop apps**.

[![Intune for Education - Apps](media/configure-apps/intune-education-apps.png)](media/configure-apps/intune-education-apps.png#lightbox)

#### Desktop apps

Intune for Education supports:

- **Single file MSI** - Single file MSI files can be uploaded directly to Intune for Education. For more information, see [Add desktop apps in Intune for Education](/en-us/intune-education/add-desktop-apps-edu).
- **Win32 apps** - The addition of desktop applications to Intune should be carried out by repackaging the apps, and defining the commands to silently install them. The process is described in the article [Add, assign, and monitor a Win32 app in Microsoft Intune](../../../app-management/deployment/add-win32).

Note

For consistency, it is recommended that you choose to use only one of the desktop app installation methods. For example, if you have any applications that require the use of the Win32 app capability, then package and deploy all apps using the Win32 apps capability and don't use the single file MSI (LOB) option.

#### Web apps

To create web applications in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** &gt; **New web app**.
4. Provide a URL for the web app, app name, and optionally an icon and description.
5. Select **Save**.

For more information, see [Add web apps](/en-us/intune-education/add-web-apps-edu).

#### Microsoft Store app (new)

To create Microsoft Store apps in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** &gt; **New Microsoft Store app (new)**.
4. Search for and select the app.
5. Review and change settings as required. 
    Note

    Most customers choose to deploy store apps in the **system** context on education devices for the fastest installation to all users of a device.
6. Select **Save**.

For more information, see [Add Microsoft Store apps](../../../app-management/deployment/add-microsoft-store).

---

::: zone-end

::: zone pivot="ios"

Tip

The best user experience for receiving apps on a device is for apps to be assigned using Apple School Manager and the Volume Purchase Program (VPP) with device licensing. When device-licensed VPP apps are assigned to devices or users, the app can be installed without user interaction. For iOS apps without VPP, the user is prompted to sign in to the App Store with an Apple ID.

# [Intune](#tab/intune)
#### Volume purchase program (VPP) apps

To add apps from VPP, set up a connection to Apple School Manager and add your apps in Apple School Manager.

For more information, see [Configure VPP tokens](../../../app-management/deployment/manage-vpp-apple).

#### iOS App

To add apps to iOS devices without using VPP in Intune for Education:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, select **iOS store app**.
4. Click **Select**. The **Add app** steps are displayed.
5. Select **Search the App Store**.
6. In the **Search the App Store** pane, select the App Store country/region locale.
7. In the **Search** box, type the name (or part of the name) of the app. Intune searches the store and returns a list of relevant results.
8. In the results list, select the app you want, and then select **Select**.
9. Follow the steps remaining steps and select **Create**.

Note

Apps installed with this method will require the user of the device to sign in using an Apple ID to install the application. To avoid prompting the user for an Apple ID, use VPP apps.

#### Web apps

To create web applications:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In the **Select app type** pane, under the **Other** types, select **iOS/iPadOS web clip**.
4. Click **Select**. The **Add app** steps are displayed.
5. Follow the steps remaining steps and select **Create**.

For more information, see [Add web apps](../../../app-management/deployment/add-web).

# [Intune For Education](#tab/intune-for-education)
#### Volume purchase program (VPP) apps

To add apps from VPP, set up a connection to Apple School Manager and add your apps in Apple School Manager.

For more information, see [Configure VPP tokens](/en-us/intune-education/setup-ios-device-management#configure-vpp-tokens).

#### iOS App

To add apps to iOS devices without using VPP in Intune:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** &gt; **New iOS app**.
4. Search the app store by entering the app name and selecting the country.
5. Select the app in the list.
6. Click **Add to Intune**.

Note

Apps installed with this method will require the user of the device to sign in using an Apple ID to install the application. To avoid prompting the user for an Apple ID, use VPP apps.

#### Web apps

To create web applications in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Apps**.
3. Select **New app** &gt; **New web app**.
4. Provide a URL for the web app, a name, and optionally an icon and description.
5. Select **Save**.

For more information, see [Add web apps](/en-us/intune-education/add-web-apps-edu).

---

### Other apps

Intune also supports deploying **[iOS/iPadOS LOB apps](../../../app-management/deployment/add-lob-ios)** from the Intune admin center. A line-of-business (LOB) app is an app that you add to Intune from an IPA app installation file.

::: zone-end

## Assign apps

![](../../../media/icons/16/check.svg) Assign apps from your inventory to groups

::: zone pivot="windows"

# [Intune](#tab/intune)
To assign applications to a group of users or devices:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps**.
3. In the **Apps** pane, select the app you want to assign.
4. In the **Manage** section of the menu, select **Properties**.
5. Next to assignments, select **Edit**.
6. Select one or more groups to for the app assignment and select **Select**.
7. Review your selections and select **Save**.

# [Intune For Education](#tab/intune-for-education)
To assign applications to a group of users or devices:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** &gt; Pick a group to manage.
3. Select **Apps**.
4. Select either **Web apps** or **Windows apps**.
5. Select the apps you want to assign to the group &gt; **Save**.

---

::: zone-end

::: zone pivot="ios"

# [Intune](#tab/intune)
To assign applications to a group of users or devices:

1. 1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps**.
3. In the **Apps** pane, select the app you want to assign.
4. In the **Manage** section of the menu, select **Properties**.
5. Next to assignments, select **Edit**.
6. Select one or more groups to for the app assignment and select **Select**.
7. Review your selections and select **Save**.

# [Intune For Education](#tab/intune-for-education)
1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** &gt; Pick a group to manage.
3. Select **Apps**.
4. Select either **Web apps** or **iOS apps**.
5. Select the apps you want to assign to the group &gt; **Save**.

---

::: zone-end