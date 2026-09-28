---
layout: Conceptual
title: IntuneManagementExtension Entity - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-intune-management-extension
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
description: Reference topic for the IntuneManagementExtension Entity category of entity collections in the Intune Data Warehouse API.
ms.date: 2024-10-30T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: a6453b7b-8ca0-12f4-0c6d-608bf6e479d3
document_version_independent_id: a6453b7b-8ca0-12f4-0c6d-608bf6e479d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/data-warehouse/ref-intune-management-extension.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/data-warehouse/ref-intune-management-extension
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/data-warehouse/ref-intune-management-extension.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: eae796d3-1509-9c32-dc3f-d320c2674981
---

# IntuneManagementExtension Entity - Microsoft Intune | Microsoft Learn

The **intuneManagementExtensions** category contains entities for mobile devices that track information such as:

- Versions of an IntuneManagementExtension
- Installation status of an IntuneManagementExtension

## intuneManagementExtensionVersions

The **intuneManagementExtensionVersion** entity lists all the versions used by intuneManagementExtensions.

| Property | Description | Example |
| --- | --- | --- |
| extensionVersionKey | Unique identifier of the intuneManagementExtensions version. | 1 |
| extensionVersion | The 4 digit version number. | 1.0.2.0 |

## intuneManagementExtensionHealthStates

The **intuneManagementExtensionHealthState** lists all possible health states of the intuneManagementExtensions.

| Property | Description | Example |
| --- | --- | --- |
| extensionStateKey | Unique identifier of health state. | 2 |
| extensionState | Health state of a IntuneManagementExtension. | Healthy |

## intuneManagementExtensions

The **intuneManagementExtension** lists the IntuneManagementExtensions health on each Windows 10 device per day. The data is retained for the last 60 days.

| Property | Description | Example |
| --- | --- | --- |
| dateKey | Unique identifier of the Date. | 123 |
| tenantKey | Unique identifier of the Tenant. | 456 |
| deviceKey | Unique identifier of the Device. | 789 |
| extensionVersionKey | Unique identifier of the intuneManagementExtension version. | 1 |
| extensionStateKey | Unique identifier of health state. | 2 |