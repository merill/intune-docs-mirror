---
layout: Conceptual
title: Share Company Portal usage data with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/privacy/disable-usage-data-collection-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to turn off Microsoft data collection in Intune Company Portal for iOS to prevent usage and diagnostic data from automatically being shared with Intune.
ms.date: 2025-02-04T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: b450d935-a375-320e-d1dd-e5edbf4a04ef
document_version_independent_id: b450d935-a375-320e-d1dd-e5edbf4a04ef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/privacy/disable-usage-data-collection-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/privacy/disable-usage-data-collection-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/privacy/disable-usage-data-collection-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a3c4a34b-8d76-d212-53a5-d98e25e554c9
---

# Share Company Portal usage data with Microsoft Intune - Microsoft Intune | Microsoft Learn

When turned on, the Company Portal usage data feature shares your in-app performance and usage data with Microsoft. Sharing your Company Portal usage data helps to improve the reliability and performance of Microsoft products like Intune.

You can turn this feature on or off from the Settings app. Your organization can't change your usage data preference, and doesn't have any control over the collection of your data.

If you turn off Company Portal usage data:

- All optional telemetry and diagnostic data that's normally collected and sent to Intune will stop being sent.
- Proactive troubleshooting will no longer be possible, so you'll need to manually upload your logs to Intune if you have a problem with the device.

The usage data setting doesn't control the data that's required to run the Intune service. That data will continue to be sent to Intune but doesn't contain any personal information.

## Edit usage data preferences

Change your usage data preferences to turn usage data collection on or off.

1. Open the **Settings** app.
2. Go to **Apps** and tap **Company Portal**.
3. Switch the **Usage Data** toggle to the off position (to stop usage and diagnostic data from being sent to Intune), or to the on position (to allow usage and diagnostic data to be sent to Intune).

## Enable or disable advanced logging

The **Enable Advanced Logging** setting is available in the Intune Company Portal app for iOS/iPadOS devices. Device users can able to enable or disable advanced logging on a device. By turning on advanced logging, detailed log reports will be sent to Microsoft to troubleshoot issues. By default, the **Enable Advanced Logging** setting will be off. Device users should keep this setting off unless otherwise instructed by their organization's IT admin.

To modify this setting on an iOS/iPadOS device:

1. Open the **Settings** app.
2. Find **Company Portal**.
3. Under **Diagnostics**, turn on or off the **Enable Advanced Logging** toggle.