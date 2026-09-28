---
layout: Conceptual
title: Report problems in Company Portal app for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-logs-company-portal-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Share app diagnostics with your support person to diagnose a problem with the Company Portal app for Windows.
ms.date: 2025-12-02T00:00:00.0000000Z
ms.reviewer: scottduf
locale: en-us
document_id: 3b41d899-4acd-19e9-760f-d7a7446d13fc
document_version_independent_id: 3b41d899-4acd-19e9-760f-d7a7446d13fc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/diagnostics/collect-logs-company-portal-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/diagnostics/collect-logs-company-portal-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/diagnostics/collect-logs-company-portal-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d6dd6e98-185f-20e3-e2ea-8972b731af3b
---

# Report problems in Company Portal app for Windows - Microsoft Intune | Microsoft Learn

**Applies to Intune Company Portal for Windows**

Report a problem or error that occurs in the Intune Company Portal app for Windows. This article describes how to share app diagnostic logs with your support person.

Note

App logs are also shared with Microsoft Support in case the problem requires additional help. Your support person will reach out to Microsoft Support with your incident ID to work with them.

## Report problem to support person

Complete the following steps to upload Company Portal app logs.

1. Open the **Company Portal** app.
2. Go to **Help & support**.
3. Select **Upload logs**.

    Note

    After you select **Upload logs**, the Company Portal sends your logs to Microsoft's support team. This step is a proactive one that makes it easier to troubleshoot and resolve problems that are escalated to Microsoft support.
4. When prompted to choose a program, select the Mail app or another preferred email app.
5. The email app opens an email template for you to fill in. Describe the problem and the steps you took leading up to the problem. Then send the email to your IT support person so that they can follow up on the issue.
6. Follow up with your support person as needed.

### Collect logs manually

Or, you can use the following steps to download the Company Portal app logs manually.

1. Go to the following folder:

    `%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState`

    The `%localappdata%` variable resolves to your local application data folder. By default, this corresponds to `C:\Users\<UserName>\AppData\Local`, where `UserName` is the signed-in user account name.
2. The application logs are stored in files following the `Log_<n>.log` pattern. Attach these logs to the support ticket.

## Report problem to Microsoft

Complete the following steps to report a problem directly to Microsoft in the Feedback Hub app. Microsoft doesn't respond to this type of report but uses it to improve upon the products. You can include screenshots and diagnostic details, but the report should remain anonymous, so don't include information like name, email address, or phone number.

1. Open the **Company Portal** app.
2. Go to **Help & support**.
3. Select **Report problem to Microsoft**.
4. Select **Report problem**. Alternatively, you can send a suggestion or leave a review of the app.

## What is a diagnostic log?

Events and errors that occur in the Company Portal app are saved on your device in a special document called a *diagnostic log*. Logs can reveal:

- When the problem happened.
- The steps leading up to the problem.
- The state of the app when the problem appeared.