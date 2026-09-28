---
layout: Conceptual
title: Enroll AOSP device with Microsoft Intune app - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-aosp
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to enroll a corporate-owned AOSP device in Intune.
ms.date: 2024-09-24T00:00:00.0000000Z
ms.reviewer: jieyang
locale: en-us
document_id: 3d9253db-0005-54d6-77b9-ffb40c9c0da9
document_version_independent_id: 3d9253db-0005-54d6-77b9-ffb40c9c0da9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-aosp.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-aosp
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-aosp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 81e83f8d-7b03-0f57-5377-6e3a3e663ce8
---

# Enroll AOSP device with Microsoft Intune app - Microsoft Intune | Microsoft Learn

Enroll your corporate-owned AOSP device to get secure, mobile access to your organization's internal resources. This article describes the enrollment requirements and steps for AOSP devices.

## Prerequisites

AOSP devices must meet the following requirements to enroll:

- New or factory-reset
- Running Android 10.0 or later
- Corporate-owned (not a personal device)
- [A supported device](../../fundamentals/ref-supported-platforms#android)

Additionally, you need the enrollment QR code that's provided by your organization.

## Enroll device

Complete these steps to set up and enroll your device.

1. Turn on your new or factory-reset device.
2. If prompted to, connect to Wi-Fi. Then tap **NEXT**.
3. When you receive the QR code, stop. Then make sure that:

    - The QR code comes from a trusted source, via a trusted channel.
    - You're enrolling your device into the right organization.
4. Scan the QR code.
5. Follow the onscreen prompts to enroll your device.
6. If prompted to, review the device terms and conditions. Then select **ACCEPT & CONTINUE**.
7. The Microsoft Intune app opens. The next step depends on the type of device you're using. Complete the step that matches the screen shown on your device:

    - Tap **START** to begin enrollment.
    - Sign in with your work account.
        1. Enter your email, and then tap **NEXT**.
        2. Enter your password, and then tap **SIGN IN** to begin enrollment.
8. When you see the message that your device is ready, tap **DONE**.

If after enrolling you have trouble accessing your organization's resources, go to the Microsoft Intune app to verify that all of your device settings meet your organization's requirements. For more information about checking compliance, see [Check compliance on your AOSP device](../compliance/validate-compliance-aosp).