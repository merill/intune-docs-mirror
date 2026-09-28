---
layout: Conceptual
title: Data Warehouse Data Model - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-data-model
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
description: The Microsoft Intune Data Warehouse samples data daily to provide a historical view of your continually changing mobile environment.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 9e5bb52c-af95-d224-7600-2459dddb20bd
document_version_independent_id: 9e5bb52c-af95-d224-7600-2459dddb20bd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-data-model.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-data-model
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-data-model.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
platformId: c084fb30-fc97-3f3c-a397-bf44a238fe9c
---

# Data Warehouse Data Model - Microsoft Intune | Microsoft Learn

The Intune Data Warehouse samples data daily to provide a historical view of your continually changing environment of mobile devices. The view is composed of related entities in time.

## Entities: Entity sets

The warehouse exposes data in the following high-level areas:

- App protection enabled apps and usage
- Enrolled devices, properties, and inventory
- Apps and software inventory
- Device configuration and compliance policies

These areas contain the entities that are meaningful to your Intune environment. You find details about the entity sets in the following topics:

- [Application](ref-application)
- [Date](ref-date)
- [Devices](ref-devices)
- [Intune Management Extension](ref-intune-management-extension)
- [Policy](ref-policy)
- [Mobile App Management (MAM)](../../app-management/overview)
- [User](ref-user)
- [User Device Associations](ref-user-device)

## Relationships: Star-schema model

The warehouse organizes the entities in relationships that are meaningful to the type of questions you want to ask. For example, you can review the number of installations of an in-house developed Android application. The structure of the data warehouse enables you to gain insight into your mobile environment. In turn, analytics tools, such as Microsoft Power BI, can use the Data Warehouse data model to create visualizations and dynamic dashboards.

The entities and relationships use a star-schema model. A star-schema correlates facts over the dimension of time. A *fact* in the context of the model is a quantitative measurement such as the number of devices, number of apps, or time of enrollment. Fact tables store a lot of data. They can get very large, and so they typically limit information to 30 days. A *dimension* provides context to the facts. Where the fact measures what happened, the dimensions indicate to whom it happened. Dimension tables, such as the **User** table, are smaller and can retrain data for longer periods of time than fact tables.

A star-schema model is optimized for flexibility and data analysis so that you can create the reports needed to understand your evolving mobile environment.

## Time: Daily snapshots

The warehouse is downstream from your Intune data. Intune takes a daily snapshot at Midnight UTC and stores the snapshot in the warehouse. The duration of held snapshots vary from fact table to fact table. Some may hold seven days, others 30 days, and some even longer durations.

Note

The Data Warehouse does not sync Jamf devices. For more information about Jamf, see [Troubleshooting Jamf Pro integration with Microsoft Intune](/en-us/troubleshoot/mem/intune/troubleshoot-jamf) and [Data Jamf Pro sends to Intune](../../privacy/data-sharing/ref-jamf-to-intune).