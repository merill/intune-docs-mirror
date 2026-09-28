---
layout: Conceptual
title: Data Google sends to Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-google-to-intune
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
description: List of data that Google sends to Intune when Android enterprise device management is enabled with Intune.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: 
locale: en-us
document_id: cde3d1ae-e0fb-7412-3e99-b4082250b845
document_version_independent_id: cde3d1ae-e0fb-7412-3e99-b4082250b845
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/data-sharing/ref-google-to-intune.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/data-sharing/ref-google-to-intune
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/data-sharing/ref-google-to-intune.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cf8f81d-2989-4e5d-aa91-5191d10a3323
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/1cb9c90f-9a3f-4389-8367-0a20c542621f
platformId: 8a2a85e4-49a0-4348-b19a-a3be0dd5cc71
---

# Data Google sends to Intune - Microsoft Intune | Microsoft Learn

When Android enterprise device management is enabled on a device, Microsoft Intune establishes a connection with Google and user and device information is shared between Intune and Google. Before Microsoft Intune can establish a connection, you must create a Google account.

The following table lists the data that Google sends to Intune when device management is enabled on an Android device:

| Data Google sends to Intune | Details | Used for | Example |
| --- | --- | --- | --- |
| Enterprise data | Customer's enterprise identifiers in Google. | Links the customer's information between Intune and Google. | **enterpriseId** example: LC04eik8a6.**Name**. The Administrator name as entered when configuring Android enterprise. Example: Joe Smith.**Admin email**. YourAdmin@gmail.com that was used when configuring Android enterprise. |
| Application data | Data for managed Play Store applications. | Targeting the application to users or devices as available or required. | **Application Name** example: Contoso Warehouse Inventory Application.**Unique Identifier to represent application** example: app:com.Contoso.Warehouse.InventoryTracking |
| Service account | Unique internal Google service account for use with specific customer calls. | Used for making calls into Google on the customer behalf (to view apps, devices, and more) | **Name** example: InternalAccount@InternalService.com.**Keys** example: ServiceAccountPassword |

To stop using Android enterprise device management with Microsoft Intune and delete the data, you must both disable the Microsoft Intune Android enterprise device management and also delete your Google account. Refer to Google account how to perform account management.