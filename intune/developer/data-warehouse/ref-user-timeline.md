---
layout: Conceptual
title: Data Warehouse User Entity Timeline - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user-timeline
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
description: Learn how the Microsoft Intune Data Warehouse represents Users in a timeline.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 9e220dff-1735-c3ee-d44d-f5af3c746995
document_version_independent_id: 9e220dff-1735-c3ee-d44d-f5af3c746995
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-user-timeline.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-user-timeline
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-user-timeline.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7d0e4840-ac94-945c-430e-1276a7910964
---

# Data Warehouse User Entity Timeline - Microsoft Intune | Microsoft Learn

You can use the month of data snapshots stored in the Intune Data Warehouse to answer questions about time-based trends. For example, you can look at the number of users being added over a month. You might also ask about the number of users who have been removed from the system.

To provide this type insight, the data warehouse stores historical information. The data warehouse can track the lifetime of an entity. The warehouse records when an entity was created, when the state of the entity changes, and when an entity is deleted. With the history captured with daily snapshots of quantitative measurements, you can compare one day to the previous day, and so on.

Working with entity lifetimes can be confusing since your entities are changing state. That means if you look at a snapshot on day 30, a user record may not exist in an active state in the data. On day 29 the entity record may exist as active. And then before day 28, the user didn't exist at all.

This scenario may be clearer if you walk through the lifetime of an entity.

Assume a user, **John Smith**, gets assigned a license on 06/01/2017, then the **User** table would have the following entry:

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent |
| --- | --- | --- | --- | --- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE |

John Smith gives up his license on 07/25/2017. The **User** table has the following entries. Changes in existing records are `marked`.

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent |
| --- | --- | --- | --- | --- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` |
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE |

The first row indicates John Smith existed in Intune from 06/01/2017 to 07/25/2017. The second record indicates that the user was deleted on 07/25/2017 and is no longer present in Intune.

Now let assume John Smith gets a new license assigned on 08/31/2017, then the User table would have the following entries:

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent |
| --- | --- | --- | --- | --- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE |
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` |
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE |

A person wanting to see the current state of all users would want to apply a filter where `IsCurrent = TRUE`.

A person wanting to see only existing users would want to apply a filter where `IsCurrent = TRUE AND IsDeleted = FALSE`.

## Dimension tables in the entity lifetime

In order to store the history of state changes in entities, Intune doesn't delete records. Instead it marks the record as deleted. This is called a soft-delete. The dimension tables use various metadata columns to track the lifetime of records.

The most commonly used metadata columns are:

| Metadata Property Name | Interpretation of Values |
| --- | --- |
| IsDeleted | Indicates whether the entity was deleted in Intune. |
| StartDateInclusiveUTC | The UTC date the entity was loaded into the Intune Data Warehouse. The entity may have been created before it was imported into the Intune Data Warehouse. |
| DeletedDateUTC | The UTC date that the entity was deleted in Intune. |

Any metadata column starting with the prefix **Row**, such as **RowLastModifiedDateTimeUTC**, indicates when a record was created or modified in the Intune Data Warehouse. The warehouse is downstream from the data in Intune. This value has no relationship to the lifetime of the entity in Intune.

Any person wanting to see only those dimension entities that currently exist would want to apply a filter where **IsDeleted = FALSE**.