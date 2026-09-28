---
layout: Conceptual
title: User - Intune Data Warehouse - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user
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
description: Reference topic for the User category of entity collections in the Intune Data Warehouse API.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 709be28e-6883-8627-79f8-4a8ff1057b53
document_version_independent_id: 709be28e-6883-8627-79f8-4a8ff1057b53
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-user.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: fc498252-3432-f651-090a-0c3575445d08
---

# User - Intune Data Warehouse - Microsoft Intune | Microsoft Learn

The **Users** category contains the **user** entity that defines user properties in the data model.

## users

The **user** entity lists all the Microsoft Entra users with assigned licenses in your enterprise.

The **user** entity collection contains user data. These records include user states during the data collection period, even if the user has been removed. For example, a user may be added to Intune and then removed during the course of the last month. While this user is not present at the time of the report, the user and state are present in the data from the prior month. You could create a report that would show the duration of the user's historic presence in your data.

| Property | Description | Example |
| --- | --- | --- |
| userKey | Unique identifier of the user in the data warehouse - surrogate key. | 123 |
| userId | Unique identifier of the user - similar to UserKey, but is a natural key. | 00aa00aa-bb11-cc22-dd33-44ee44ee44ee |
| userEmail | Email address of the user. | John@contoso.com |
| userPrincipalName | User principal name of the user. | John@contoso.com |
| displayName | Display name of the user. | John |
| intuneLicensed | Specifies if this user is Intune licensed or not. | True/False |
| isDeleted | Indicates whether all of the user's licenses have expired and whether the user was therefore removed from Intune. For a single record, this flag does not change. Instead, a new record is created for a new user state. | True/False |
| RowLastModifiedDateTimeUTC | Date and time in UTC when the record was last modified in the data warehouse | 11/23/2016 0:00 |