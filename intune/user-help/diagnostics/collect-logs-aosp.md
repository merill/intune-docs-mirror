---
layout: Conceptual
title: Configure logging settings for AOSP - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-logs-aosp
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to adjust app logging levels in the Microsoft Intune app.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: de1a9434-42c9-41e6-d635-96102753b754
document_version_independent_id: de1a9434-42c9-41e6-d635-96102753b754
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/diagnostics/collect-logs-aosp.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/diagnostics/collect-logs-aosp
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/diagnostics/collect-logs-aosp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7b8bf6d6-df7d-17f5-cf80-8c96af5c190c
---

# Configure logging settings for AOSP - Microsoft Intune | Microsoft Learn

**Applies to Microsoft Intune app for AOSP**

Logging enables the Microsoft Intune app to record actions that take place in the app. If you ever experience a problem in the app, and then report it, your support team will review the app logs. Verbose logging, which is the highest level of logging, is most helpful in these cases because it provides the most details about what happened in the app.

The log detail level defaults to **Important** in the Microsoft Intune app. To adjust the level:

1. Open the Microsoft Intune app.
2. Tap **Settings**.
3. Under **Log level detail**, select **Verbose** to increase the level of details recorded. Select **Off** to turn off logging.

Note

The logs that you send to your support team will include your email address.