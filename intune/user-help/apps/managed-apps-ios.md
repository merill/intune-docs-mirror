---
layout: Conceptual
title: Get work or school apps for iOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/apps/managed-apps-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to access work or school apps on your iOS device.
ms.date: 2024-05-15T00:00:00.0000000Z
ms.reviewer: amanh
locale: en-us
document_id: 1768a877-7806-dadf-4f05-7e88926a1491
document_version_independent_id: 1768a877-7806-dadf-4f05-7e88926a1491
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/apps/managed-apps-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/apps/managed-apps-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/apps/managed-apps-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d20613c5-ede1-42ed-b6cc-1f39332ae70e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/af64080b-70a9-4efa-8078-59a46ddbdaa4
platformId: 1e19f78e-8c12-f6a5-4fdb-db967b495a23
---

# Get work or school apps for iOS - Microsoft Intune | Microsoft Learn

Intune-managed apps (*managed* apps for short) are apps that've been configured for you to securely use at work or school. They're specially configured to meet your organization's security requirements and protect internal data. For example, if you're signed in to one of these apps with your work or school account, your org can restrict certain features, such as copy and paste. Or they could restrict you from saving work files to your device's local storage. These types of restrictions prevent proprietary information from being shared outside of the app or org.

To maximize data protection, your organization might configure several of these apps to work together. For example:

1. You connect to your organization's network in a managed browser app, such as Microsoft Edge.
2. You click a link to open a peer's presentation file.
3. An appropriate managed app, such as Microsoft PowerPoint, opens the file.

Your org can require you to use a specific app to do something like opening a work file, or accessing a web link. If you don't have the app, you might not be able to do these things.

## How do I know I'm using a managed app?

When you sign in or try to access work or school data in a managed app, you receive an on-screen message that tells you the app is protected by your organization.

![Screenshot of on-screen message received about protected app.](media/managed-apps-ios/managed-apps-message.png)

## How do I get work or school apps?

There are three ways to get apps for work or school:

- The apps automatically install on your device at time of enrollment.
- You install an app from the Apple App Store, and then sign in to the app with your work or school account.
- Your organization makes the apps available to you in Company Portal. Go to the Company Portal app or website to search, view, and install available apps. For more information, see the next section, Available apps.

### Apple Volume Purchase Program agreement

Your organization may purchase iOS app licenses in bulk to accommodate the number of students or employees they have. If prompted to, review and accept the Apple Volume Purchase Program agreement to install the app.

## Available apps

Your organization selects apps that are appropriate and useful for work or school and makes them available to install in Company Portal. You don't have to install these apps, but they're there if you need them. Apps are made available to you based on your device type. For example, when using the Company Portal app for iOS, you have access to iOS apps, but not Android apps.

## Request an app for work or school

If there's an app you need, but don't see in Company Portal, you can request it. Go to the Company Portal app **Support** tab for your support person's contact details. The same contact information is available on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).

## What can my org manage in an app?

The following list describes the settings your IT support person can control within an app. These settings affect how you view, access, and otherwise use work or school data on your device:

- Access to specific websites
- Transfers of data between apps
- Saving files
- Copy and paste operations
- PIN access requirements
- Sign-in experience, using company credentials
- Ability to back up to the cloud
- Ability to take screenshots
- Data encryption requirements

## Approve line-of-business app

By default, your device doesn't trust line-of-business (LOB) apps acquired outside of the App Store, which may prevent your organization's own company apps from being installed. You'll know this is happening if you open an installed LOB app and receive an *untrusted enterprise developer* message.

![Screenshot of iOS app message about an untrusted enterprise developer.](media/managed-apps-ios/end-user-company-portal-messages-01.png)

For information about how to manually install and trust an enterprise app on your device, see [Install custom enterprise apps on iOS](https://support.apple.com/en-us/HT204460) on the Apple Support site.