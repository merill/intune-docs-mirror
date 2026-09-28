---
layout: Conceptual
title: Check compliance in Microsoft Intune app for AOSP - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-compliance-aosp
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Use the Intune app to confirm that the settings on your device meet your organization's requirements.
ms.date: 2024-11-07T00:00:00.0000000Z
ms.reviewer: abigailstein
locale: en-us
document_id: e5314bde-1191-dc59-10ef-8a3d5d494067
document_version_independent_id: e5314bde-1191-dc59-10ef-8a3d5d494067
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-compliance-aosp.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-compliance-aosp
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-compliance-aosp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 74708b87-3616-00ce-0af6-be447486b4d5
---

# Check compliance in Microsoft Intune app for AOSP - Microsoft Intune | Microsoft Learn

*Applies to Microsoft Intune app for AOSP*

Use the Microsoft Intune app to remotely check the compliance status of an enrolled device, and confirm or resolve access issues caused by noncompliant settings. During a status check, the Intune app checks your device settings to make sure they meet your organization's requirements. If your device isn't compliant with requirements, your organization might limit or restrict it from accessing work resources until you make changes.

Tip

After you update the settings on a noncompliant device, start a compliance check to register the changes with the Intune app.

## Compliance notifications

Microsoft Intune app notifications fall into two categories:

- Device compliance: A compliance notification alerts you when your device falls out of compliance with your organization's requirements. Notifications persist until you address or resolve the issue.
- Organizational notifications: You can receive, dismiss, and delete notifications that you receive from your organization.

## Check compliance

Complete these steps to check compliance and refresh the device settings status on an enrolled device.

1. Open the Microsoft Intune app for AOSP on your device.
2. Tap **Devices** and then select your device.
3. Under **Device Settings Status**, tap **Refresh**. Wait while the Intune app checks device settings and updates the device settings status.
4. If your device is noncompliant and you're required to make changes, you receive a compliance notification in the Intune app. Tap the notification for more information.

## Device settings status

The device settings status tells you the following information about your enrolled device:

- **Compliant**: Your device is allowed to access work or school resources.
- **Can access resources, but action required**: Your device is allowed to access work or school resources, but one or more settings don't meet your organization's requirements. Update your device settings by the date shown to keep your access.
- **Not compliant**: Your device isn't allowed to access work or school resources. Make the required changes to gain access.