---
layout: Conceptual
title: Sync enrolled device for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/device-actions/sync-device-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Sync your enrolled device using the Company Portal app, the Start menu, the task bar, or the Settings app.
ms.date: 2024-10-16T00:00:00.0000000Z
ms.reviewer: priyar
locale: en-us
document_id: e9fabac8-49cd-cc71-9528-869e5c1fbe0c
document_version_independent_id: e9fabac8-49cd-cc71-9528-869e5c1fbe0c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/device-actions/sync-device-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/device-actions/sync-device-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/device-actions/sync-device-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 396b8d13-33fe-718f-1320-c9b21b49679b
---

# Sync enrolled device for Windows - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

Sync the enrolled device you're using for work to get the latest updates, requirements, and communications from your organization. Company Portal regularly syncs devices as long as you have a Wi-Fi connection. However, if you ever need to disconnect for an extended period of time, you can manually sync the device when you return to get any updates you missed. Syncing can also help resolve work-related downloads or other processes that are in progress or stalled. If you're experiencing slow or unusual behavior while installing or using a work app, try syncing your device to see if an update or requirement is missing.

This article describes how to start a sync from the:

- Company Portal app
- Windows desktop taskbar or Start menu
- System settings app

## Sync from Company Portal app for Windows

Complete these steps to sync a device in the Company Portal app. 

1. Open the Company Portal app on your device and go to **Settings**.

![Example screenshot of the Company Portal app homepage, highlighting the Settings option.](media/sync-device-windows/company-portal-windows-settings.png)
2. Select **Sync**.

![Example screenshot of the Company Portal app, highlighting Sync button.](media/sync-device-windows/company-portal-windows-sync.png)

## Sync from device taskbar or Start menu

You can access Company Portal syncing action from the desktop. This way is useful if you have the app pinned directly to your taskbar or Start menu, and want to quickly sync.

1. Find the Company Portal app icon in your taskbar or Start menu.
2. Right-click the app's icon so its menu (also referred to as a jump list) appears.

    ![Screenshot of the Windows taskbar on a device's desktop. Company Portal app icon was selected and shows a menu with options &quot;Pin to taskbar,&quot; &quot;Close window,&quot; and &quot;Sync this device&quot; action.](media/sync-device-windows/sync-device-from-start-menu-1807.png)
3. Select **Sync this device**. The Company Portal app opens and the sync begins.

## Sync from Settings app

You can sync devices running a supported version of Windows from the system Settings app.

1. On your device, select **Start** &gt; **Settings**.
2. Select **Accounts**.
3. Select the option that matches your onscreen experience.

    - If your screen shows the **Access work or school** option, jump to Access work or school steps in this article.

        ![Screenshot of the Settings app's account settings section highlighting the Access work or school option with a red rectangle.](media/sync-device-windows/w10-enroll-rs1-connect-to-work-or-school.png)
    - If your screen shows the **Work access** option, jump to Work access steps in this article.

### Access work or school steps

1. Select **Access work or school**.

    ![Screenshot showing Access work or school option.](media/sync-device-windows/w10-enroll-rs1-connect-to-work-or-school.png)
2. Select your work account, which is marked with a briefcase icon or Microsoft logo.

    ![Choose your account name next to the briefcase or Microsoft logo.](media/sync-device-windows/win10pc-rs1-sync-info-button.png)
3. Select **Info**.
4. Select **Sync**.

### Work access steps

1. Select **Work access**.
2. Under **Enroll in to device management**, select the account that's associated with your workplace.
3. Choose **Sync**. The button remains inactive until the sync is complete.

## Sync from Settings app (Microsoft HoloLens)

Sync HoloLens running the Windows 10 Anniversary Update (also known as RS1) or later from the system Settings app.

1. Open the Settings app on your device.
2. Select **Accounts**.
3. Select **Work Access**.
4. Find your connected account, and then select **Sync**.