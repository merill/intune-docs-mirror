---
layout: Conceptual
title: Lock your device from the Company Portal - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/device-actions/restrict-device-company-portal-website
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Remotely lock a lost or stolen device from the Company Portal website.
ms.date: 2024-11-08T00:00:00.0000000Z
ms.reviewer: jieyang
locale: en-us
document_id: d46d1635-9e69-a20b-66f0-eab6b5fe3c90
document_version_independent_id: d46d1635-9e69-a20b-66f0-eab6b5fe3c90
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/device-actions/restrict-device-company-portal-website.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/device-actions/restrict-device-company-portal-website
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/device-actions/restrict-device-company-portal-website.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f77f026a-0160-f80a-dbaa-f02f48e43bf7
---

# Lock your device from the Company Portal - Microsoft Intune | Microsoft Learn

**Applies to**

- Android
- iOS/iPadOS

Remotely lock the screen of a lost or stolen enrolled device. The *remote lock* action is available on the Intune Company Portal website and can be used on supported devices. After you lock a device, it will stay locked until someone finds it and enters the correct passcode.

## Lock a device

1. On any device, sign in to the [Company Portal website](https://portal.manage.microsoft.com) with your work or school account.
2. Go to **Devices**.
3. Select the device you want to lock.
4. Select **Remote lock**. If the lock option isn't visible at the top of your page, select the **More (…)** menu to check all overflow actions.
5. A message appears to warn you that you are about to lock your device. Tap **Remote lock** to confirm.

## Check remote lock status

While the Company Portal attempts to lock your device, you'll see a **Remote lock pending** status. When your device finally locks, the status changes to **Remote lock successful**. The status appears throughout the website in your notifications area and on device=specific pages.

Tip

If you see a notification that the remote lock failed, wait a few minutes, and then try to lock your device again. The status will change back to **Remote lock pending**. If the retry doesn't work, contact your support person for help.