---
layout: Conceptual
title: Share management logs with support person - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-logs-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Export Windows management log diagnostics to share with your support person for troubleshooting an enrolled device.
ms.date: 2025-02-20T00:00:00.0000000Z
ms.reviewer: priyar
locale: en-us
document_id: a1d5f842-ed01-7d19-8f2d-cb8628844aaf
document_version_independent_id: a1d5f842-ed01-7d19-8f2d-cb8628844aaf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/diagnostics/collect-logs-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/diagnostics/collect-logs-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/diagnostics/collect-logs-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b83e4707-78de-8e61-7288-46a036f31dd1
---

# Share management logs with support person - Microsoft Intune | Microsoft Learn

**Applies to**

- Windows

Export and share management log diagnostics with your support person to troubleshoot an error on your enrolled device. When an error or event occurs on your device, the details of it are recorded and saved to a document called a *diagnostic log*. Diagnostic logs can provide your support team with enough information to diagnose and resolve the error.

To share logs with your support person:

1. Open the **Settings** app on your device.
2. Go to **Accounts** &gt; **Access work or school**.
3. Select **Export your management log files**.

    ![The &quot;Access work or school screen&quot;, which presents the Export option underneath the &quot;Related settings&quot; heading.](media/collect-logs-settings-windows/w10-export-logs.png)
4. Email the logs to your support person. Logs are saved in **C:\Users\Public\Public Documents\MDMDiagnostics**. Two files are created for each log: one is the log itself, and the other is a document that allows your admin to review the logs in different programs, such as Microsoft Excel. Include both files in your email to your support person.

You can also [send Company Portal app logs](collect-logs-company-portal-windows) to your support person.

Still need help? Contact your support person. For contact information, sign in to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).