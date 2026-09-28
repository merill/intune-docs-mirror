---
layout: Conceptual
title: Manage apps from Intune Company Portal website - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/apps/manage-apps-company-portal-website
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Manage and view available and installed apps
ms.date: 2025-03-05T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: 8e8d0cbb-84ca-94d3-1c4e-27384a89dc9d
document_version_independent_id: 8e8d0cbb-84ca-94d3-1c4e-27384a89dc9d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/apps/manage-apps-company-portal-website.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/apps/manage-apps-company-portal-website
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/apps/manage-apps-company-portal-website.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d6b3d3ee-e2f0-a240-d05a-0754ddf13f65
---

# Manage apps from Intune Company Portal website - Microsoft Intune | Microsoft Learn

**Applies to:**

- Android
- iOS/iPadOS
- macOS
- Windows

Sign in to the [Company Portal website](https://portal.manage.microsoft.com) to view and manage apps from your organization.

## View all apps

From the menu, select **Apps** to see all apps made available by your organization.

![Screenshot of Company Portal website, Apps page.](media/manage-apps-company-portal-website/intune-view-apps-1907.png)

This page lists the following details about each app:

- Name: The name of the app, with a link to the app's details page.
- Publisher: The name of the developer or company that distributed the app. A publisher is typically a software vendor or your organization.
- Status: The current state of the app on your device, which includes available, installed, and installing.
- Category: The app's function or purpose, such as featured, engineering, education, and productivity.

### Viewing apps for Windows devices

Company Portal doesn't immediately recognize newly added Windows devices. So before you can see your available apps, you have to tell Company Portal which device you're using. To do that:

1. Sign in to https://portal.manage.microsoft.com/devices.
2. Select **Devices**.
3. A message appears onscreen that prompts you to identify your device. Tap the message.
4. Select your device.

### Search and refine

Use the search bar to find apps. Search results are sorted automatically by relevancy.

![Screenshot of Company Portal website, Apps page, showing Refine options.](media/manage-apps-company-portal-website/intune-refine-all-apps-1907.png)

Select **Refine** to see filter and sort options. Filter the list to show apps with specific criteria, including **Type**, **Availability**, and **Publishers**. Select **Sort** to rearrange the apps by:

- App name, ascending or descending alphabetically
- Publisher name, ascending or descending alphabetically
- Publish date, oldest or newest

## View installed apps

From the menu, select **Downloads & updates** to view all apps installed on your device. This page lists the following details about each app:

- Name: The name of the app, with a link to the app's details page.
- Assignment type: How the app is assigned and made available to you. See Available and required apps for more details. Your organization can either make an app available for you to install yourself, or they can require and install an app on your device automatically.
- Publisher: The name of the developer or company that distributed the app. A publisher is typically a software vendor or your organization.
- Status: The current installation status of the app on your device. Apps can show as installing, installed, and install failed. Required apps could take up to 10 minutes to show an up-to-date status.

### Refine

Select **Refine** to see filter and sort options. Filter the list to show apps with specific criteria, including **Types**, **Publishers**, and **Statuses**. Select **Sort** to rearrange the apps by:

- App name, ascending or descending alphabetically
- Publisher name, ascending or descending alphabetically

### Available and required apps

Apps are assigned to you by your organization, and labeled as either available or required. You can see which apps you have under the **Assignment Type** column.

- Available apps: These apps are selected by your organization, and are appropriate and useful for work or school. They are optional to install, and are the only apps you'll find in the Company Portal to install.
- Required apps: Your organization might deploy necessary work and school apps directly to your device. These apps are automatically installed for you without intervention.

Apps are made available to you based on your device type. For example, if you're using the Company Portal website on a Windows device, you'll have access to Windows apps, but not iOS apps.

## View app details

Select an app on the **Apps** or **Downloads & updates** page to view its details. You'll be taken to **App details**, where you'll find the app's description and requirements. If an app isn't already installed on your device, you can install it from this page.

![Screenshot of Company Portal website, App details page.](media/manage-apps-company-portal-website/intune-app-details-1907.png)

## Device compliance status

View the compliance status of your devices from the Company Portal website. You can navigate to the [Company Portal](https://portal.manage.microsoft.com/devices) website and select the **Devices** page to see device status. Devices will be listed with a status of **Can access company resources**, **Checking access**, or **Can't access company resources**.