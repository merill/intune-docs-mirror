---
layout: Conceptual
title: Turn on iOS/iPadOS supervised mode with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/enable-supervised-mode
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: annovich
ms.subservice: enrollment
description: Learn how to turn on iOS/iPadOS supervised mode with Intune.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: adbae1aa-d890-90fd-3ada-f881d9991b8f
document_version_independent_id: adbae1aa-d890-90fd-3ada-f881d9991b8f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/enable-supervised-mode.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/enable-supervised-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/enable-supervised-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 52100a12-031d-8a43-5e5f-86b3c3454c03
---

# Turn on iOS/iPadOS supervised mode with Microsoft Intune - Microsoft Intune | Microsoft Learn

Apple iOS/iPadOS supervised mode gives administrators more options when managing Apple devices, making it useful for corporate-owned devices deployed at scale. For example, you can restrict AirDrop or prevent users from changing the name of the device. For a list of settings which require supervised mode, see [iOS device restriction settings in Intune](../../device-configuration/templates/ref-device-restrictions-apple).

Intune supports supervised mode as part of the Apple [Device Enrollment Program (DEP)](setup-automated-ios).

For a list of Apple controls that require supervision, see Apple's [Payload settings reference](https://support.apple.com/guide/deployment/dep2c1b2a43a/web).

## Turn on supervised mode after enrollment

After enrollment, the only way to turn on supervised mode is to connect an iOS/iPadOS device to a Mac and [use the Apple Configurator](setup-configurator-ios) (which will reset the device). You can't configure a device for supervised mode in Intune after enrollment.

Apple Configurator for iPhone can also be used to supervise devices. For more information, see the [Apple support doc](https://support.apple.com/apple-configurator).

## Identify a supervised device

To determine if a device is supervised, check the **Settings** app.

Users are notified that their devices are supervised in the **Settings** app. In the app at the top of the screen, a static message shows the message **This iPhone is supervised and managed by *`<your organization>`***.