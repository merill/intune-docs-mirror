---
layout: Conceptual
title: Enroll Windows devices in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Set up your Windows device in Intune Company Portal to get remote access to work or school.
ms.date: 2025-10-14T00:00:00.0000000Z
ms.reviewer: madekeva
locale: en-us
document_id: d0befe65-64a5-0740-943c-94659227aa43
document_version_independent_id: dc8d4d82-5503-1e60-11c3-a6dce251a771
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5c65c665-8bd9-42e0-7288-613112a8677c
---

# Enroll Windows devices in Intune - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Enroll your Windows device in Intune to get mobile access to work or school apps, email, and Wi-Fi.

To identify the version of Windows running on your device, see [Which version of Windows operating system am I running?](https://go.microsoft.com/fwlink/?linkid=2166188). 

## Get Company Portal

You can enroll Windows devices through the Intune Company Portal website or app. Devices running Windows 7 or 8.1 must enroll through the Company Portal website. To access Company Portal:

- Install the app from the [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=2141417).
- [Sign on to the Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) with your work or school credentials.

## Enroll devices

Use Intune Company Portal to enroll devices running on Windows 10, version 1607 and later, and Windows 11.

1. Open Company Portal and sign in with your work or school account.
2. On the **Home** screen, select **Next** to set up your device.

    ![Example image of Company Portal &gt; Set up your device screen, showing that the device needs to be set up to connect to work and highlighting the Next button.](media/enroll-windows/set-up-your-device-company-portal-2107.png)
3. Select **Connect**.

    ![Example image of Company Portal &gt; Connect to work screen highlighting the Connect button.](media/enroll-windows/connect-to-work-company-portal-2107.png)
4. Sign in with your work or school account again. If you're using the Company Portal website, the sign-in prompt may open in a new window.

    ![Example image of Microsoft authentication screen that prompts user to &quot;Enter password.&quot;](media/enroll-windows/enter-password-prompt-company-portal-2107.png)
5. On the **Setting up your device** screen, select **Go**.
6. After setup is complete, return to the Company Portal app. Select **Next**.
7. Select **Done** to exit setup.

    ![Example image of Company Portal &gt; You're all set screen, highlighting the Done button.](media/enroll-windows/youre-all-set-company-portal-2107.png)

## Sync device to fix connection problems

After enrolling, if you have trouble accessing work or school things, try syncing your device. For more information about syncing, see [Sync device](../device-actions/sync-device-windows).

## Troubleshooting

For a non-exhaustive list of error messages and resolutions, see [Troubleshoot Windows device access](../troubleshooting/troubleshoot-device-access-windows).

## Support for IT administrators

If you're an IT administrator and run into problems while enrolling devices, see [Troubleshooting Windows device enrollment problems in Microsoft Intune](/en-us/troubleshoot/mem/intune/device-enrollment/troubleshoot-windows-enrollment-errors). This article lists common errors, their causes, and steps to resolve them.