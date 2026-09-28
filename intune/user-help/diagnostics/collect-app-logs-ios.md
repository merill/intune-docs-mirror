---
layout: Conceptual
title: Retrieve iOS app logs - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-app-logs-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to retrieve Intune Company Portal app logs off your device for troubleshooting purposes.
ms.date: 2025-03-05T00:00:00.0000000Z
ms.reviewer: annovich
locale: en-us
document_id: 031ee845-6884-f9d6-9bfa-7a0dbb430f05
document_version_independent_id: 031ee845-6884-f9d6-9bfa-7a0dbb430f05
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/diagnostics/collect-app-logs-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/diagnostics/collect-app-logs-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/diagnostics/collect-app-logs-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 0f05f8c9-54b0-4747-7114-3956b429b009
---

# Retrieve iOS app logs - Microsoft Intune | Microsoft Learn

Whenever you experience a problem in Company Portal, the details of that problem are recorded and stored on your device in a *diagnostic log*. This article describes how to upload those logs from your device to your computer. This process is useful for when you need to troubleshoot, because you can save the logs in a file and email it to your IT support person.

## Retrieve logs via Console app

To retrieve logs via the native Console app, you need your iOS device, a Mac running macOS 10.12 or later, and a cable to connect both devices.

1. Connect your iOS device to your Mac with the cable.
2. On your Mac, press **command + Space** and search for Console. Open Console.
3. On your iOS device, you'll be prompted to trust the computer. Select **Trust**.
4. In Console, select your iOS device from the **Devices** list &gt; **Start**. Console begins to gather your logs.
5. From the Console menu, select **Action** &gt; **Include Info Messages** and **Include Debug Messages**.
6. Select **Clear** and remove any search queries you may have in Console.
7. Open Company Portal on your iOS device and try to reproduce the problem by repeating the steps or actions you took leading up to the problem.
8. From the Console menu, select **Edit** &gt; **Select All**, and then select **Edit** &gt; **Copy**.
9. Paste the log contents in TextEdit.
10. From the TextEdit menu, select **Format** &gt; **Make Plain Text**.
11. Save the file as a .log file. Example: Contosologs.log