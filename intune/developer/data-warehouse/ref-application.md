---
layout: Conceptual
title: Reference for Application Entities - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-application
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
description: Reference topic for the Application category of entity collections in the Intune Data Warehouse API.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 6a7e82e9-3253-716f-deaf-8d6b9a4ba94e
document_version_independent_id: 6a7e82e9-3253-716f-deaf-8d6b9a4ba94e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-application.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/60932d05-feee-4685-a73b-595e25dd9318
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/c43bb58b-1190-419b-8d18-e6052371b599
platformId: 7baadba9-3efd-70e7-2099-945603ef60e4
---

# Reference for Application Entities - Microsoft Intune | Microsoft Learn

The **Application** category contains entities for devices that track information such as:

- Versions of an app
- Installation source of an app
- Type of developers who created an app
- Managed software types for an app, for example **sidecar** or **desktop**
- Volume Purchasing Program (VPP) state of an app

## appRevisions

The **appRevision** entity lists all the versions of apps.

| Property | Description | Example |
| --- | --- | --- |
| appKey | Unique identifier of the App. | 123 |
| applicationId | Unique identifier of the App - similar to AppKey, but this key is a natural. | 00001111-aaaa-2222-bbbb-3333cccc4444 |
| revision | The version as mentioned by admin during uploading of the binary. | 2 |
| title | Title of the app. | Excel |
| publisher | Publisher of the app. | Microsoft |
| uploadState | Upload state of the app. | 1 |
| appTypeKey | Reference to AppType described in the following section. |  |
| vppProgramTypeKey | Reference to VppProgramType described below. |  |
| creationTime | The time when this revision was created. | 11/23/2016 12:00:00 AM |
| modifiedTime | Last time anything related to this revision was changed. | 11/23/2016 12:00:00 AM |
| size | Size of the binary. |  |
| startDateInclusiveUTC | Date and time in UTC when this App revision was created in the data warehouse. | 11/23/2016 12:00:00 AM |
| endDateExclusiveUTC | Date and time in UTC when this app revision became obsolete. | 11/23/2016 12:00:00 AM |
| isCurrent | Indicates whether this App version is current or not in the data warehouse. | True/False |
| rowLastModifiedDateTimeUTC | Date and time in UTC when this app version was last modified in the data warehouse. | 11/23/2016 12:00:00 AM |

## appTypes

The **appType** entity lists the installation source of an app.

| Property | Description |
| --- | --- |
| appTypeID | ID for the type |
| appTypeKey | Surrogate key for the key |
| appTypeName | App type |

### Example

| AppTypeID | Name | Description |
| --- | --- | --- |
| 0 | Android store app | An Android store app. |
| 1 | Android LOB app | An Android line-of-business app. |
| 2 | Managed Android store app (MAM) | An Android store app that has management enabled. |
| 3 | iOS store app | An iOS store app. |
| 4 | iOS LOB app | An iOS line-of-business app. |
| 5 | Managed iOS store app (MAM?) | An iOSstore app that is management enabled. |
| 6 | Microsoft 365 Apps for enterprise | The Microsoft 365 Apps for Windows 10. |
| 7 | Web app | A web app. |
| 8 | Windows Phone 8.1 store app | A Windows phone 8.1 store app. |
| 9 | Windows store app | A Windows store app. |
| 10 | Windows LOB apps | A Windows AppX line-of-business app. |
| 11 | Windows Mobile MSI | An MSI line-of-business app. |
| 12 | Windows Phone LOB app | A Windows phone line-of-business app. |

## vppProgramTypes

The **vppProgramType** entity lists possible VPP program types for an app.

| Property | Description |
| --- | --- |
| vppProgramTypeID | ID for the type. |
| vppProgramTypeKey | Surrogate key for the key. |
| vppProgramTypeName | VPP Program type. |

### Example

| VppProgramID | Name | Description |
| --- | --- | --- |
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft's VPP program. |
| 00000000-0000-0000-0000-000000000000 | Not Yet Available | Default value, No VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple's VPP program. |

## mobileAppInstallStates

The **mobileAppInstallState** entity represents the install state for a mobile application after it has been assigned to a group containing devices, users or both.

| Property | Description |
| --- | --- |
| appInstallStateKey | The unique ID of the app install state for your account. |
| appInstallState | Enum value of the app install state. |
| appInstallStateName | Name of the app install state. |