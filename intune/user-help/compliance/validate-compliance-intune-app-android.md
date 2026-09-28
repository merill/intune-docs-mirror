---
layout: Conceptual
title: Check status in Microsoft Intune app for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-compliance-intune-app-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Start a status check to confirm that a device meets requirements for access, or to resolve access issues after you've made required changes.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: shthilla
locale: en-us
document_id: a72d3cf2-07fd-4c25-d116-a44c9a61cdf5
document_version_independent_id: a72d3cf2-07fd-4c25-d116-a44c9a61cdf5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-compliance-intune-app-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-compliance-intune-app-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-compliance-intune-app-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: cf03929d-48ce-b5e2-1ac0-6e172b8c2f9f
---

# Check status in Microsoft Intune app for Android - Microsoft Intune | Microsoft Learn

*Applies to Microsoft Intune app for Android*

Use the Microsoft Intune app for Android to remotely check the status of a device, and confirm or resolve access issues caused by noncompliant settings.

During a status check, the Intune app assesses the *device settings status* on an enrolled device, and reports whether or not the settings are compliant with your organization's requirements. If your device doesn't meet requirements, your organization may limit or restrict it from accessing internal resources. When applicable, the status provides information about how to maintain or regain access.

## Check status

To check the status of a device:

1. Open the Microsoft Intune app for Android.
2. Tap **Devices**, and then select your device.

The status is shown under **Device settings status**. The **Last checked** timestamp shows the date and time the last check occurred.

## Status descriptions

The Intune app reports the following status:

- **Compliant**: Your device is allowed to access work or school resources.
- **This device will soon be unable to access company resources**: Your device is allowed to access work or school resources, but one or more settings don't meet your organization's requirements. Update your device settings by the date shown to keep your access.
- **Noncompliant**: Your device isn't allowed to access work or school resources. Make the required changes to gain access.