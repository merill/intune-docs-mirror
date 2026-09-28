---
layout: Conceptual
title: Report problems in Company Portal app for iOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/diagnostics/collect-logs-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Share app diagnostics with your support person to diagnose a problem with the Company Portal app for iOS.
ms.date: 2025-02-18T00:00:00.0000000Z
ms.reviewer: annovich
locale: en-us
document_id: 7f8d45f6-7c15-779f-eedc-fa06eb4b7186
document_version_independent_id: dc6662b6-dab5-e57f-b38a-2afb1f5b1ca6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/diagnostics/collect-logs-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/diagnostics/collect-logs-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/diagnostics/collect-logs-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
platformId: 51fd1503-4b85-8fa9-8864-903791a3e87f
---

# Report problems in Company Portal app for iOS - Microsoft Intune | Microsoft Learn

*Applies to Intune Company Portal app for iOS/iPadOS*

Report a problem or error that occurs in the Intune Company Portal app for iOS/iPadOS. This article describes how to share app diagnostic logs with your support person.

Tip

To make it easier for your support person and app developers to figure out a problem, turn on *verbose logging*. Verbose logging records all details about an error and includes these details in the report. For more information, see [Configure logging settings](enable-verbose-logging-android).

## Access help and support in app

You can access the reporting feature in Company Portal using any of these methods:

- When you receive an error message or alert, tap **Report**.
- Under the **More** tab of the Company Portal app, tap **Send Logs**.
- In the Company Portal app, shake your device, then tap **Send Diagnostic Report**. If the diagnostics report prompt doesn't appear when you shake the device, open the **Settings** and go to **Apps**. Then go to **Company Portal**, and turn on **Shake Gesture**.

## Share diagnostic logs

1. Open the Company Portal app for iOS/iPadOS.
2. Try to reproduce the event you experienced. This step is optional but ensures that the Company Portal details appear at the top of the logs when uploaded.
3. Use one of the following methods to initiate the upload:

    - When you receive an error message, tap **Report**.
    - Shake your device. Then tap **Send diagnostic report**.
4. Wait while Company Portal uploads the logs from Company Portal. When that's done, tap **Open Authenticator** to collect logs from the Microsoft Authenticator app.
5. Save the incident ID for your records and to share with your support person. The incident ID is unique to your report.
6. Select **Email Logs** to follow up with your support person with more details so they can get started with your case. In the body of the email, explain what you experienced and include your incident ID. Your support person may use the incident ID to enlist help from Microsoft about your case.

Still need help? Contact your support person. For contact information, check the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).