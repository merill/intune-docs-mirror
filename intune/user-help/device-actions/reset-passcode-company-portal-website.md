---
layout: Conceptual
title: Reset device passcode from Intune Company Portal website - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/device-actions/reset-passcode-company-portal-website
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Go to the Company Portal website to reset a lost or forgotten PIN on an enrolled device.
ms.date: 2025-02-04T00:00:00.0000000Z
ms.reviewer: jieyang
locale: en-us
document_id: 46d9d403-baaa-4040-6631-24cf2ef3f6db
document_version_independent_id: 46d9d403-baaa-4040-6631-24cf2ef3f6db
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/device-actions/reset-passcode-company-portal-website.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/device-actions/reset-passcode-company-portal-website
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/device-actions/reset-passcode-company-portal-website.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5d83165b-739e-a816-be59-c0989677cdf7
---

# Reset device passcode from Intune Company Portal website - Microsoft Intune | Microsoft Learn

**Applies to**:

- Android
- iOS/iPadOS

Remotely reset an enrolled device's PIN or passcode. Sign in to the [Company Portal website](https://portal.manage.microsoft.com) on any device to access the *reset passcode* option. Contact your support person for help if the option is missing and you need to reset a device.

Note

Passcode reset doesn't work on these types of devices:

- Personal devices that have an Android work profile, running Android 8.0 and later
- Dedicated Android Enterprise work devices, such as kiosks, running Android 8.0 and later
- Devices utilizing Android device administrator, running Android 8.0 and later

If you forget your passcode on one of these devices, the only way to regain access is to reset the whole device to factory settings.

## Reset your passcode

1. Sign in to the [Company Portal website](https://portal.manage.microsoft.com).
2. Go to **Devices**.
3. Select the device that needs a passcode reset.
4. Select **Reset Passcode**. If the passcode option isn't visible at the top of your page, select the **More (…)** menu to see all overflow actions.

    ![Device details page for a selected device on the Company Portal website, with a list of links at the top showing Rename, Remove, Reset Device, Reset Passcode, and Remote Lock. ](media/reset-passcode-company-portal-website/rename-reset-device-1808.png)
5. When prompted, choose **Sign out**. When prompted again, sign back in. Sign back in to the Company Portal website within five minutes, or Company Portal won't reset the device passcode. You must sign back in to confirm your identity. This step prevents malicious attempts to reset your device passcode.

    ![Example screenshots showing a prompt to sign out of the Company Portal. The buttons for user input are Sign Out and Cancel.](media/reset-passcode-company-portal-website/iwp-reset-passcode-popup-1808.png)
6. A message appears to warn you that the existing device passcode is about to be removed. Select **Reset passcode** to confirm.

    Warning

    After you reset your passcode, anyone who has physical access to the device can access most personal and corporate information on it. If you don't currently have the device in your possession, don't reset the passcode.

    ![Example screenshot showing second reset passcode message. Includes link to learn more about setting a new passcode in the documentation, and individual buttons to reset passcode and cancel.](media/reset-passcode-company-portal-website/iwp-reset-passcode-popup2-1808.png)
7. If you're resetting the passcode for an iOS device, its existing passcode is removed. For Android devices, you are issued a temporary passcode to unlock the device and set a new passcode.

    Note

    You can find the temporary password for an Android device in Company Portal. Select the device to drill down into device details.
8. On your device, go to the **Settings** app and change your passcode.
9. Select the notification that appears on the Company Portal website. Confirm that the password was successfully reset.

## Set up a new passcode

This section describes the passcode reset and the temporary password behavior for each device platform.

**Android**: Removes the existing passcode and creates a temporary passcode made up of letters and numbers.

**iOS**: Removes the existing passcode and doesn't create a temporary passcode. If you use Touch ID to open your device or make purchases, you must set it up again.

Still need help? Contact your company support. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).