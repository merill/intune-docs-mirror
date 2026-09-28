---
layout: Conceptual
title: Unenroll device in Company Portal for macOS app - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to unenroll a device in the Company Portal for macOS app.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.reviewer: elocholi
locale: en-us
document_id: 29ad4c13-6299-b4e6-e864-ef526b9f629f
document_version_independent_id: 29ad4c13-6299-b4e6-e864-ef526b9f629f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/unenrollment/unenroll-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/unenrollment/unenroll-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/unenrollment/unenroll-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 492671b0-7656-9cc8-f18f-e941753c2608
---

# Unenroll device in Company Portal for macOS app - Microsoft Intune | Microsoft Learn

You can use the Company Portal app for macOS to unenroll a device that you no longer need for work or school.

After you remove a device:

- The device is removed from Intune.
- The device loses access to Company Portal features. For example, you can't install apps for the device from the Company Portal.
- You lose access to work or school file shares and websites previously accessed from the device.
- You lose access to work apps that are on the device.
- You might be blocked from connecting to your organization's network over Wi-Fi or virtual private network (VPN).
- Work and school email profiles are removed from the device.
- Device restrictions previously enforced by Company Portal (for example, disabling the camera or requiring a certain password length) are no longer enforced.

This article describes how to remove a device from within the Company Portal app, and then how to uninstall the app.

## Remove a device

Follow these steps to remove a device from Company Portal that you no longer need for work or school. For these steps to work, you must still have access to your work or school account. If you no longer have access to your account, see [Remove management profile](unenroll-macos#remove-management-profile) (in this article) to unenroll your device.

1. Sign in to Company Portal for macOS.
2. Go to **Devices** and select the device you want to unenroll.
3. From the app toolbar, select the **Devices** menu &gt; **Remove**.
4. When asked to confirm the removal, select **Remove**. The device is immediately removed from Intune.

After you complete these steps, you can uninstall Company Portal from your device.

## Remove management profile

To remove a device after you've left your workplace or school, you have to remove the *management profile* that was installed during enrollment. For steps specific to your version of macOS, see [Remove a configuration profile from your Mac](https://support.apple.com/guide/mac-help/configuration-profiles-standardize-settings-mh35561/mac) on the Apple Support website. After you remove the management profile, you can uninstall Company Portal from your device.

## Uninstall Company Portal app

To uninstall the Company Portal app from a macOS device, select and drag the Company Portal app to the trashcan located in your dock. For more information, see [Uninstall apps on your Mac](https://support.apple.com/en-us/102610) on the Apple Support website.