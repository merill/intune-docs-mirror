---
layout: Conceptual
title: User Device Association - Intune Data Warehouse - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user-device
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.reviewer: jamiesil
ms.subservice: developer
description: The UserDeviceAssociation entity contains user device associations in your organization.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: b104ef93-caef-71ef-1ae3-9836cc48dc2e
document_version_independent_id: b104ef93-caef-71ef-1ae3-9836cc48dc2e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-user-device.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-user-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-user-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: bd222a2d-a9f0-c0ca-597f-fea9e79d52d1
---

# User Device Association - Intune Data Warehouse - Microsoft Intune | Microsoft Learn

The **userDeviceAssociation** entity contains user device associations in your organization.

## userDeviceAssociations

| Name | Description | Example |
| --- | --- | --- |
| userKey | Unique identifier of the user in the data warehouse. (Surrogate key). | 123 |
| deviceKey | Unique identifier of the device in the data warehouse. | 123 |
| createdDateTimeUTC | Date and time when the user device association was created. Uses UTC format. | 11/23/2016 12:00:00 AM |
| isDeleted | Indicates that the user unenrolled that device, and that the association is not current anymore. | True/False |
| endedDateTimeUTC | Date and time in UTC when IsDeleted changed to **True**. | 06/23/2017 12:00:00 AM |