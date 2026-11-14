---
layout: Conceptual
title: Troubleshoot Windows Device Access for School or Work - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/troubleshooting/troubleshoot-device-access-windows
author: iceorbital
ms.author: acabello
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.subservice: end-user
ms.topic: end-user-help
description: Troubleshoot Windows device access for work or school. Learn how to fix Wi-Fi, account connection, and enrollment errors.
ms.date: 2026-11-04T00:00:00.0000000Z
ms.reviewer: amanh
locale: en-us
document_id: 612813e1-a6dd-5240-1c58-57ef6ea7b6ad
document_version_independent_id: 612813e1-a6dd-5240-1c58-57ef6ea7b6ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/troubleshooting/troubleshoot-device-access-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/troubleshooting/troubleshoot-device-access-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/troubleshooting/troubleshoot-device-access-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 126b54c3-147b-96a2-9cd9-604c1bb723bb
---

# Troubleshoot Windows Device Access for School or Work - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

This article describes how to resolve access issues for an enrolled Windows device.

## Check Wi-Fi connection

You need a connection to Wi-Fi to access work or school resources. Verify that you're connected to Wi-Fi and then try accessing the resources again.

## Add work or school account in Settings app

If your account doesn't appear in the **Settings** app, go through the setup steps in the **Settings** app again.

1. Open the **Settings** app.
2. Select **Accounts**.
3. Identify the version of Windows you run, and then select **Access work or school**.
4. Check for your account. If it's not listed, select **Connect** to add it.
5. Sign in with your work or school account, and follow the onscreen prompts to finish connecting.

When complete, your account appears as a connection, and you have access to any resources your organization makes available.

## Contact IT support for access problems

If you see your work or school account listed in the **Settings** app, your device and account are already connected. Contact your IT support person for further help. They might have put restrictions or requirements in place that prevent you from accessing certain resources. Sign in the Company Portal app or [website](https://go.microsoft.com/fwlink/?linkid=2010980) for your organization's helpdesk details.

## Error messages

### We couldn't auto-discover a management endpoint matching the username you entered. Check your username and try again. If you know the URL to your management endpoint, enter it.

**Cause**: Your account couldn't be verified with the provided URL, also referred to as the *management endpoint*.

#### Resolution

1. Enter your username and password again.
2. If it still doesn't work, contact your IT support person to get the correct URL (for example: `www.yourcompany.onmicrosoft.com`).
3. When prompted, enter the provided URL.

### It looks like you're not connected. Ensure you're connected to the network.

**Cause**: Your device isn't connected to Wi-Fi and a connection is required to add a work or school account.

#### Resolution

Connect to a Wi-Fi network and then try adding your account again.

### Your device is already being managed by an organization.

**Cause**: Your device is already enrolled in Intune or another mobile device management (MDM) provider.

#### Resolution

Contact your IT support person to find out how they want you to proceed.