---
layout: Conceptual
title: Manage Specialty devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/specialty-devices
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: This article provides information about specialty devices and how can you manage them with Microsoft Intune
ms.date: 2026-05-12T00:00:00.0000000Z
ms.topic: article
ms.reviewer: priyar
ms.subservice: suite
locale: en-us
document_id: bf9adb21-94a1-495f-73c9-6c4fb3781980
document_version_independent_id: bf9adb21-94a1-495f-73c9-6c4fb3781980
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/specialty-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/specialty-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/specialty-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 369da1be-fdc4-d6e1-a809-b3e253009522
---

# Manage Specialty devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Specialty device management provides a range of management, configuration, and protection capabilities for specialized devices, such as AR/VR headsets, large smart-screen devices, and select conference room meeting devices.

## Prerequisites

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> This feature requires Microsoft Intune Plan 2 or an additional subscription. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

![](../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Specialty device management is supported in the following cloud environments:
> 
> - Public cloud
> - Sovereign cloud environments:
>     - U.S. Government Community Cloud (GCC) High
>     - U.S. Department of Defense (DoD)
> 

### Licensing considerations

For specialty devices such as headsets and AR/VR devices, for example **Apple Vision Pro**, **RealWear**, and **HTC** devices, organizations must assign a required license to the users of these devices.

For **Microsoft Teams Rooms** devices including Microsoft Surface Hub, organizations need to have sufficient [Microsoft Teams Rooms Pro licenses](/en-us/microsoftteams/rooms/rooms-licensing), conference area phone [Teams Shared Device license](/en-us/microsoftteams/set-up-common-area-phones) or a Teams license plan that includes Microsoft Intune Plan 1, to cover the users of these devices.

For **Microsoft HoloLens**, subscribers of Microsoft Intune (Plan 1) aren't required to add more licenses to manage HoloLens devices.

For specialty devices that run in Microsoft Entra shared device Mode (SDM), organizations need to have the same volume of required licenses as their core Intune license (Intune Plan 1 for either Microsoft E or F plans) for those users. For example, if 10 frontline workers are sharing one device and they're all covered by Intune Plan 1 core licenses, the organization should also have 10 of the required specialty device licenses to cover those users.