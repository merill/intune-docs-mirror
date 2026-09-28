---
layout: Conceptual
title: Get App Bundle ID - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/collect-bundle-ids
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Get the app bundle ID in Microsoft Intune for Android, iOS/iPadOS, macOS, and Windows apps. Use the bundle ID in your app policies, device configuration profiles, enrollment policies, and compliance policies in Microsoft Intune.
ms.date: 2024-04-30T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: 
locale: en-us
document_id: ae40927d-562a-289d-06cb-21cb996e51aa
document_version_independent_id: ae40927d-562a-289d-06cb-21cb996e51aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/collect-bundle-ids.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/collect-bundle-ids
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/collect-bundle-ids.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1091dbd2-889d-27f1-fe8a-27c2d851c637
---

# Get App Bundle ID - Microsoft Intune | Microsoft Learn

When you add an app to Intune or use the built-in apps, the bundle ID of the app is also added. This bundle ID identifies the app, and you can use the bundle ID in your policies.

For example, you can use the bundle ID in an Intune device configuration profile to allow or block specific apps.

Applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

This article lists the steps to get the app bundle IDs using the Intune admin center.

## Get the app bundle ID

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps**.
3. Select **Columns**.

    ![Screenshot that shows how to select the Columns option in All Apps in Microsoft Intune and the Intune admin center.](media/collect-bundle-ids/all-apps-column.png)
4. In the list, select **App identifier** &gt; **Apply**.

    ![Screenshot that shows how to select the App Bundle ID column in All Apps in Microsoft Intune and the Intune admin center.](media/collect-bundle-ids/columns-select-app-identifier.png)
5. The **App identifier** column shows the bundle ID of the app.