---
layout: Conceptual
title: Reset device from Intune Company Portal for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/device-actions/reset-device-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Reset a used, lost, or stolen device in Company Portal for Windows.
ms.date: 2024-10-16T00:00:00.0000000Z
ms.reviewer: madakeva
locale: en-us
document_id: 33c723fe-d989-7e65-d1df-409be5b55f30
document_version_independent_id: f5648275-a803-14f9-5ac0-cc29358163de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/device-actions/reset-device-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/device-actions/reset-device-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/device-actions/reset-device-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c7bb9e7a-6459-6cf8-9bc3-d33f37e05c69
---

# Reset device from Intune Company Portal for Windows - Microsoft Intune | Microsoft Learn

Use the Company Portal app for Windows to reset a used, lost, or stolen device back to factory settings. After a reset, all apps, settings, and personal data on the device are deleted, and the device no longer appears in Company Portal.

The reset option may not be available for every device that appears in Company Portal. Your organization can choose to hide the option.

## Reset device

To reset a device to its original, out-of-box settings:

1. Open the Company Portal app on any managed device and sign in with your work or school account.
2. Select **Devices**, and then select the device you want to reset.
3. Select **Actions** &gt; **Reset**.

![Example screenshot of the Company Portal app for Windows highlighting the Reset option.](media/reset-device-windows/company-portal-windows-reset.png)
4. Select **Reset** to start wiping the device.

![Example screenshot of the Company Portal app for Windows highlighting the confirmation message and final Reset button.](media/reset-device-windows/company-portal-windows-reset-confirmation.png)

## Reset limitations

Company Portal device resets aren't supported on all devices. The feasibility of a reset depends on the Windows version and how your organization configured their policies. This table lists the expected outcomes for various Windows devices and configurations.

| Device configuration and management | Device type |
| --- | --- |
| Your organization manages your mobile device | **Windows 10 or Windows 11**Your device no longer appears in Company Portal. Company Portal tries to reset the device back to the manufacturer's default settings. Your personal data, apps, and settings are removed. **Windows 10 Mobile**The only way to unenroll your device is to reset it. |
| Your device can access company email only | **Windows Phone 8.1**Your device no longer appears in Company Portal. The email that belongs to your work account, and all unsaved emails, are deleted.**Windows 7 or Windows Vista** Devices running Windows 7 or earlier, and used exclusively for email, can't be reset. **Windows 8.1 and Windows 8**Your device no longer appears in Company Portal. The email that belongs to your work account, and all unsaved emails, are deleted. |
| PCs and laptops | **Windows 8.1 and Windows 8** Devices running Windows 8 or Windows 8.1 can't be reset, unless they're used exclusively for email.**Windows 7 or Windows Vista**Devices running Windows 7 or earlier can't be reset. |

Need more help? Contact your IT support person. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).