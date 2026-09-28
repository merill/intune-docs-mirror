---
layout: Conceptual
title: Redo Workplace Join for Android Enterprise devices in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/android/redo-workplace-join-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Learn how to redo Workplace Join (re-WPJ) on an Android Enterprise device that's already enrolled in Intune but needs Azure AD registration completed.
ms.date: 2026-06-18T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: grwilso
locale: en-us
document_id: d8cca1a3-7963-c647-d0de-c74fd050e78f
document_version_independent_id: d8cca1a3-7963-c647-d0de-c74fd050e78f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/android/redo-workplace-join-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/android/redo-workplace-join-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/android/redo-workplace-join-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 51c4ae83-0ea5-1f5c-21f1-ef68702c78fe
---

# Redo Workplace Join for Android Enterprise devices in Intune - Microsoft Intune | Microsoft Learn

This article describes how to complete Workplace Join (WPJ) on an Android Enterprise device that's already enrolled in Microsoft Intune. Use this guide if a user lands on the **Get Started** enrollment page but their device is already enrolled and they only need to redo the Workplace Join step.

## When does this happen

This scenario can occur when enrollment and Azure AD registration become out of sync. Common situations include:

- A user began web-based enrollment but didn't complete the Workplace Join step.
- A device migrated from the legacy custom DPC management stack to Android Management API, and the registration step didn't complete.
- A user's work account was removed or re-added on the device without fully unenrolling.

## Before you begin

This edge case can affect devices enrolled in any of the following Android Enterprise management types:

- Personally owned work profile (web-based enrollment)
- Personally owned work profile (app-based enrollment)
- Corporate-owned work profile
- Fully managed
- Dedicated

Before starting, confirm that the device is already enrolled in Intune (visible in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) under **Devices** &gt; **All devices**), the user has their work account credentials available, and Microsoft Authenticator is installed on the device.

## Redo Workplace Join

If a user's device registration becomes out of sync with enrollment, have the user complete the following steps to redo Workplace Join and restore access to work resources.

1. Open the app used to enroll the device (Microsoft Intune for web-based enrollment or Intune Company Portal for app-based enrollment).
2. Select the notification to complete Workplace Join.
3. Follow the on-screen instructions to register the device.
4. Return to the work app, such as Microsoft Outlook or Microsoft Teams, and try accessing it again.

If the user can access work resources again, Workplace Join completed successfully.