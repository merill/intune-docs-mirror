---
layout: Conceptual
title: Apple School Manager Program enrollment for iOS/iPadOS devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager
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
description: Learn how to set up Microsoft Intune with Apple School Manager for corporate-owned iOS/iPadOS devices.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5ea4558e-ac5e-ab07-4c6d-e9fcf7056ada
document_version_independent_id: 5ea4558e-ac5e-ab07-4c6d-e9fcf7056ada
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/school-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/school-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/school-manager.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a5415c40-62a6-c08b-faf5-6cf8bdc0a159
---

# Apple School Manager Program enrollment for iOS/iPadOS devices - Microsoft Intune | Microsoft Learn

Set up Microsoft Intune to enroll Apple mobile devices purchased through [Apple School Manager](https://school.apple.com/). Using Intune with Apple School Manager, you can enroll large numbers of devices without ever touching them. When a student or teacher turns on the device, Apple Setup Assistant runs with preconfigured settings and the device enrolls into management.

## Prerequisites

To enable Apple School Manager enrollment, you use both the Microsoft Intune admin center and Apple School Manager portal.

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - iOS/iPadOS
> - tvOS
> - visionOS
> 
> 
> Devices must be added to [Apple School Manager](http://school.apple.com). You need a list of serial numbers or a purchase order number to assign devices in Apple School Manager. tvOS and visionOS devices enroll without user affinity and are enrolled as corporate-owned devices with configuration delivered through custom configuration profiles.

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - Get an [Apple mobile device management (MDM) push certificate](create-mdm-push-certificate).
> - Set up the [MDM Authority](../../fundamentals/setup-mdm-authority).
> - If using Active Directory Federation Services (AD FS), user affinity requires [WS-Trust 1.3 Username/Mixed endpoint](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff608241%28v=ws.10%29). For more information, see [Get ADFS endpoint](/en-us/powershell/module/adfs/get-adfsendpoint).
> 

Apple School Manager enrollment can't be used with the [device enrollment manager](../setup-enrollment-manager) account.