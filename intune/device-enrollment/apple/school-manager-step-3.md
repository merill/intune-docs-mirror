---
layout: Conceptual
title: Apple School Manager - sync and distribute devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-3
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
description: Sync and distribute Apple School Manager devices enrolled in Microsoft Intune.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7e19c71a-d4de-db7b-991e-ed6d3f1fac65
document_version_independent_id: 7e19c71a-d4de-db7b-991e-ed6d3f1fac65
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/school-manager-step-3.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/school-manager-step-3
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/school-manager-step-3.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 7fbed4ac-55af-0200-15e7-e4ed13497526
---

# Apple School Manager - sync and distribute devices - Microsoft Intune | Microsoft Learn

After you assign Microsoft Intune permission to manage your Apple School Manager devices, sync Intune with the Apple service to see your managed devices in the admin center.

## Start a sync

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), return to **Enrollment program tokens**.
2. Select a token in the list.
3. Select **Devices** &gt; **Sync**.

![Screenshot of the Enrollment Program Devices node and Sync link.](media/setup-automated-ios/image06.png)

To follow Apple's terms for acceptable enrollment program traffic, Intune imposes the following restrictions:

- A full sync can run no more than once every seven days. During a full sync, Intune refreshes every Apple serial number assigned to Intune. If a full sync is attempted within seven days of the previous full sync, Intune only refreshes serial numbers that aren't already listed in Intune.
- Any sync request is given 15 minutes to finish. During this time or until the request succeeds, the **Sync** button is disabled.
- Intune syncs new and removed devices with Apple every 24 hours.

## Assign a policy to devices

Apple School Manager devices managed by Intune must be assigned an enrollment policy before they're enrolled.

1. Return to **Enrollment program tokens**.
2. Select a token in the list.
3. Select **Devices**, and then choose your devices.
4. Select **Assign policy**. Then select a policy for the devices.
5. Select **Assign**.

## Distribute devices to users

You enabled management and syncing between Apple and Intune, and assigned a policy that lets Apple School devices enroll. You can now distribute devices to users. When an Apple School Manager device is turned on, it enrolls in Microsoft Intune. Policies can't be applied to activated devices currently in use until the device is wiped.

## Connect School Data Sync

Microsoft Education is transitioning to a new School Data Sync (SDS) experience with enhanced features, starting August 2024 for the Northern Hemisphere and January 2025 for the Southern Hemisphere. The current Apple School Manager support will be retired by December 31, 2024. This new experience offers various enhancements over SDS (Classic) including:

- Decoupled data ingestion
- Faster syncs with fewer errors
- Support for larger organizations
- A modern user interface

Please contact Microsoft Education support with questions regarding the transition to the new School Data Sync experience.