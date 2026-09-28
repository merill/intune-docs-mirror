---
layout: Conceptual
title: Data Intune sends to Zebra - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-intune-to-zebra
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- privacy
- sub-data-privacy
description: List of data that Intune sends to Zebra.
ms.date: 2023-12-07T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: jieyan
locale: en-us
document_id: 4260074b-5c40-0774-2d5d-589eac773764
document_version_independent_id: 4260074b-5c40-0774-2d5d-589eac773764
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/data-sharing/ref-intune-to-zebra.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/data-sharing/ref-intune-to-zebra
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/data-sharing/ref-intune-to-zebra.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cf8f81d-2989-4e5d-aa91-5191d10a3323
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/1cb9c90f-9a3f-4389-8367-0a20c542621f
platformId: beca1502-e10e-a01e-aa4f-9ab37d633773
---

# Data Intune sends to Zebra - Microsoft Intune | Microsoft Learn

When Zebra LifeGuard Over-the-Air (LG OTA) is enabled for your tenant, Microsoft Intune establishes a connection with Zebra and shares the following data with Zebra:

The following table lists the data that Microsoft Intune sends to Google when device management is enabled on a device:

| Data sent to Zebra | Used for | Example |
| --- | --- | --- |
| Serial number | Used to prove ownership of device against a known service contract with Zebra, determine current state of the device, and for the Android update process. | Unique identifier, example format: 124411614K0593 |
| Deployment settings | Used to deliver Android updates. | - Device Model: TC8300<br>- Update type: Custom Time zone offset in minutes: 300<br>- BSP (Board Support Package): 11.15.05.00<br>- OS Version: 11<br>- Patch Number: U20<br>- Schedule mode: Latest<br>- Schedule duration in days: 20<br>- Download network type: Wifi<br>- Download start date and time:<br>- 2022-03-25T15:04:51.8607086Z<br>- Installation start date and time:<br>- 2022-03-25T15:04:51.8607086Z<br>- Installation window start time: 19:00:00<br>- Installation window end time: 19:00:00<br>- Minimum Battery level percentage: 30<br>- Require device to be on charger: true |

To stop using Zebra services with Microsoft Intune and delete the data, you must both disconnect from Zebra LifeGuard OTA in Microsoft Intune, and also delete the data from your Zebra account by filing a customer request with Zebra.