---
layout: Conceptual
title: Remove your Windows device from Intune management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Disconnect your work or school account from device running Windows.
ms.date: 2024-04-30T00:00:00.0000000Z
ms.reviewer: jieyang
locale: en-us
document_id: e8186a91-73b1-1276-9710-70ee92a491e5
document_version_independent_id: b8210dcf-6694-e920-1ea7-9761ad02f810
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/unenrollment/unenroll-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/unenrollment/unenroll-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/unenrollment/unenroll-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 239b6f4e-b0f6-c18d-1616-48a0021a8f21
---

# Remove your Windows device from Intune management - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

Remove a registered, Windows device from management when you no longer want or need to:

- Use your device for work or school.
- Access work or school email, apps, or other resources.

After you unregister the device, you lose device access to school or work resources.

Make sure to read [What happens if you remove device from Intune](unenroll-windows#what-happens-if-you-remove-device-from-intune) before unenrolling your device.

## What happens if you remove device from Intune

This section describes how your device and access to work or school will change after you remove your device from Intune.

After you unenroll a device running Windows:

- Your device is removed from Company Portal.
- You can't install apps from the Company Portal.
- Intune client software (if installed) will be removed from your computer.
- Intune Endpoint Protection software is removed from your computer. If your computer has other virus protection software installed that's disabled, be sure to re-enable it after Intune Endpoint Protection is removed. Otherwise, your computer is vulnerable to viruses and malware.
- Changes to device settings (for example, disabling the camera or requiring a certain password length) are no longer required.
- Your computer no longer receives automatic software updates or antivirus software updates from the Intune service. But, depending on how it is set up, your computer might still receive updates from the Windows Server Update Services, Windows Update, or Microsoft Update.

In addition, for Windows 8.1:

- You lose access to work apps and data on your device.
- Email apps, such as Windows Mail, can't open work email that's stored on your device.
- You might not be able to connect to your org's network via Wi-Fi or virtual private network (VPN).
- You could lose access to internal file shares and websites from your device.

After you unenroll a device running Windows 8.1 RT:

- The Company Portal app is uninstalled from your device. Your device is removed from Company Portal and the app is uninstalled from your device.
- You can't install apps from Company Portal.
- You lose access to work apps and data on your device.
- Changes to device settings (for example, disabling the camera or requiring a certain password length) are no longer required.
- You might not be able to connect to your org's network via Wi-Fi or virtual private network (VPN).
- You could lose access to internal file shares and websites from your device.
- Email apps, such as Windows Mail, can't open work email that's stored on your device.

## Remove Windows devices

This section describes how to remove a Windows device from Intune.

### Remove in device Settings app

1. Open the Settings app.
2. Go to **Accounts** &gt; **Access work or school**.
3. Select the connected account that you want to remove &gt; **Disconnect**.
4. To confirm device removal, select **Yes**.

## Remove Windows 8.1 PC

Complete the following steps to remove a Windows 8.1 computer from Intune.

1. Go to **PC Settings** &gt; **Network** &gt; **Workplace**.
2. Under **Workplace Join**, select **Leave**.
3. Under **Turn on device management,** select **Turn off**.
4. On the popup window that opens, select **Turn off**.

## Removing your personal information after removing the Company Portal

There are two kinds of data that the Company Portal stores on your Windows device:

- **Diagnostic logs**: Standard app activity data that Microsoft collects. This is automatically erased when you uninstall the Company Portal app. App activity data is, for example, data about how long the app was open or if the app crashed.
- **Application cache**: Support files that are required for the app to work, such as icons and settings.

To delete the stored logs and cache, complete one of the following steps:

- [Uninstall the Company Portal app](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs)
- Reset the Company Portal app. Open the **Settings** app and select &gt; **Apps** &gt; **Installed apps** &gt; **Company Portal** &gt; **Advanced options** &gt; **Reset**.