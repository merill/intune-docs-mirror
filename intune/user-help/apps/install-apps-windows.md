---
layout: Conceptual
title: Install work apps from Intune Company Portal app for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/apps/install-apps-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Sign in to the Company Portal app for Windows to browse and install work or school-related apps on your enrolled device.
ms.date: 2024-10-07T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: b910273e-7a39-f974-909c-95cbb6884914
document_version_independent_id: 929c216b-6b45-313c-4d7a-3b9125483608
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/apps/install-apps-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/apps/install-apps-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/apps/install-apps-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0732514d-ccb8-d3d6-f1c5-ae3d927725ca
---

# Install work apps from Intune Company Portal app for Windows - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

Browse and install work apps in the Intune Company Portal app for Windows. This article describes how to install, view, and share work apps from Company Portal.

Tip

As a companion to this article, see our [Intune app protection for Windows setup guide](../../app-management/protection/enable-mam-windows) to review best practices and learn to enforce policies, deploy apps, and protect corporate data across a variety of devices. For a customized experience based on your environment, you can access the [Intune app protection for Windows guide](https://go.microsoft.com/fwlink/?linkid=2309606) in the Microsoft 365 admin center.

## Types of apps

There are two types of apps available in Company Portal: *optional apps* and *required apps*.

Optional apps are selected by your organization and deemed useful and appropriate for work or school. These apps are available to you, but it's up to you to install them.

Required apps are necessary for work and school and are deployed directly to your work device. These apps are automatically installed for you without intervention. Required apps appear in your installed apps list alongside the optional apps you install.

To find out which installed apps are required:

1. Sign in to the Company Portal app with your work or school account.
2. Go to **Downloads & updates**.

    ![Screenshot of the Downloads &amp; updates page for the Company Portal app for Windows. ](media/install-apps-windows/windows-companyportal-02.png)
3. In the table, look under the column **Required by your organization**. A *yes* means that the app is required on your enrolled device.

## Install apps

Before you begin, install [Intune Company Portal for Windows from the Microsoft Store](https://apps.microsoft.com/detail/9WZDNCRFJ3PZ).

1. Sign in to the Company Portal app on your work or school device. You'll see the latest notifications on the Home page.

    ![Screenshot of the Home page with notifications in the Company Portal app for Windows.](media/install-apps-windows/windows-companyportal-03.png)
2. You can access available apps from the following places in Company Portal:

    - **Home**: Go to **Home** to view your organization's featured apps.
    - **Apps**: Go to **Apps** to view, sort, and filter through all available apps.
    - **App categories**: Go to **App categories** to browse apps by type or function. Apps in this area are sorted into categories picked by your organization, like *featured*, *education*, and *productivity*.
    - **Search for apps**: Use the static search bar in the navigation pane to search apps by name or publisher.
3. Select an app, and then choose **Install**. The app's installation status changes to *Installing* while the app installation occurs, then *Installed* when installation is done. Select **Retry** if a required app fails to install and the option to retry is available. It could take up to ten minutes for the installation status to update itself.

Tip

To select and install more than one app at a time, go to **Apps** and switch the layout view to multi-select mode. Then select the checkbox next to each app you want to install. Choose **Install selected** to install them.

## View all apps

Go to **Apps** to see a list of all available and installed apps on your device.

- **Name**: The name of the app.
- **Version**: The version number of the app.
- **Publisher**: The name of the developer or company that distributed the app. A publisher is typically a software vendor or your organization.
- **Date Published**: The date that the app was made available to download. Publish date could show an app's initial release or an app's most recent update.
- **Status**: The current installation status of the app on your device, which could include *Available*, *Installing*, *Installed*, and *Install failed*.

Select **Sort by** to rearrange the apps alphabetically by app or publisher name, or chronologically by publish date. Under **Refine**, you can select a category to narrow results to a certain type of app.

## View installed apps

Go to **Downloads & updates** to see a list of installed apps on your device. If no apps are available to view, you'll see a message that no company apps were installed.

![Screenshot of the Downloads &amp; updates page for the Company Portal app for Windows.](media/install-apps-windows/windows-companyportal-02.png)

The following information is available for each app:

- **Name**: The name of the app.
- **Version**: The version number of the app.
- **Required by your organization**: How the app is assigned and made available to you.
- **Publisher**: The name of the developer or company that distributed the app. A publisher is typically a software vendor or your organization.
- **Status**: The current installation status of the app on your device, which could include *Available*, *Installing*, *Installed*, and *Install failed*. Required apps could take up to 10 minutes to show an up-to-date status. See Install apps in this article for important details about installing required apps.

## Installing Microsoft Office

Depending on the size of your workplace or school, there could be multiple versions of Office available to install in Company Portal. You should only install one version of Office. If you try to install an additional one, the first one will be uninstalled. If you're unsure which version is best for your role, contact your IT support person for guidance.

## Share apps

Share and recommend apps to your work or school contacts. The following steps describe how to share a link directly from Company Portal.

1. In Company Portal, right-click or press and hold the app to open the [context menu](/en-us/windows/uwp/design/controls-and-patterns/menus).
2. Select **Share**.
3. Select a single contact or select another program, such as OneNote, to share the app link with a group of people. The recipient receives a link and a message to view the app. The link opens the Company Portal app details page.

## Request an app for work or school

Request an app that's unavailable in the Company Portal app. Go to **Help & support** for your organization's helpdesk details. The same contact information is available on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).

![Screenshot of the Company Portal app for Windows, Help &amp; Support page, highlighting the Helpdesk section.](media/install-apps-windows/1812_ucp_help_support_helpdesk.png)

## Uninstall apps

The option to uninstall apps is available in the Company Portal app for some Win32 apps and Microsoft store apps:

1. Go to **Apps**.
2. Select the app you want to uninstall.
3. Choose **Uninstall**.