---
layout: Conceptual
title: Managed work and school apps for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/apps/managed-apps-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn about managed apps and where to get Android apps for work or school.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 7de3e51f-1f77-d105-3e67-3c56d2d9927b
document_version_independent_id: a929eff9-1635-f09d-9f01-2eb4a21a67a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/apps/managed-apps-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/apps/managed-apps-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/apps/managed-apps-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 0398b5dc-a62d-2bd5-25b7-2a3f00c5371f
---

# Managed work and school apps for Android - Microsoft Intune | Microsoft Learn

Note

Managed apps are not currently supported on AOSP devices.

Intune-managed apps (*managed* apps for short) are work-approved apps managed by your organization and configured to prevent intentional or unintentional data loss. When signed in to a managed app with your work or school account, you might encounter your organization's requirements and restrictions for access. This article provides an overview of Intune-managed apps, how to get the ones you need for work or school, and their restrictions and requirements.

## How do I know I have a managed app?

When you sign in or try to access work data in a managed app, you receive a message that the app is protected by your organization.

On a device with a work profile, a work app is marked with a briefcase badge. For more information about Android work profiles, see [Introduction to Android work profile](../enrollment/work-profile-android).

## App and data protection policies

Managed apps enforce your organization's app and data-protection policies, which might restrict or require:

- Access to specific websites
- Access to internal company websites using Microsoft Edge and the Microsoft Entra ID proxy
- Minimum app and OS version
- Ability to share and transfer data between apps
- How and where you save work files
- Copy and paste functionality
- PIN access
- How you sign in, using workplace credentials
- Ability to back up data to the cloud
- Ability to take screenshots
- Data encryption requirements

These policies prevent sensitive work information from being shared or leaked outside of your org. Restrictions and requirements are only enforced when using an app for work or school, such as when:

- You're signed in to an app with your work account.
- You try to access work files in OneDrive, Teams, or SharePoint.
- You're using apps in the work profile area on your device.

## How do I install work or school apps?

There are three ways to get work apps:

- Install an app from the Google Play store, and then sign in to the app with your work or school account.
- Your organization configures apps to install automatically at the time of device enrollment.
- Your organization makes apps available to you in Company Portal.

You don't need to enroll your device in Intune to use work or school apps unless your organization requires it, but you do need to have the Intune Company Portal app installed on your device.

### Add work or school account

You can only associate one work or school account with the managed apps on your device. This policy is enforced in the following scenarios:

- If you try to add a second work or school account, Company Portal prompts you to remove the work account you're not using.
- If your IT admin assigns a policy to your second account, Company Portal prompts you to remove the work account you're not using.

### Available apps

*Available* apps aren't necessarily required for you to install, but are appropriate apps to use for work or school. You can view all available apps in the Company Portal app. Apps are made available based on device type. For example, if you're using the Company Portal app on your Android device, you'll have access to Android apps, but not iOS apps.

### Request an app for work or school

If there's an app you need but don't see in Company Portal, you can request it from your support person. Sign in to the Company Portal app or [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) for contact information.

### View protected media files with Azure Information Protection app

The Azure Information Protection (AIP) mobile apps let you view protected emails, PDFs, images, and text files that you can't open with your regular apps for these file types.

For more information about AIP, see [View protected files with Microsoft Purview Information Protection viewer](https://support.microsoft.com/topic/view-protected-files-with-microsoft-purview-information-protection-viewer-9fb56fae-7989-48b0-850f-f446e057cf73).

## View and edit default apps

Company Portal securely saves and stores your default app selections for managed apps. To view and remove your default selections:

1. Open Company Portal.
2. Tap the main menu &gt; **Settings**.
3. Scroll down to **Default Apps** and tap **See Defaults** to view and remove your current defaults.