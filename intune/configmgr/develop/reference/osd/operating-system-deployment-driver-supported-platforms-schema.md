---
layout: Conceptual
title: OS Deployment Driver Supported Platforms Schema - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn how to use the OS Deployment Driver Supported Platforms Schema to check which operating systems are compatible.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 15cb0843-1916-ac12-c69f-9bb997efa7aa
document_version_independent_id: e0f2b787-b828-181d-03d9-4f207e578833
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: ba931d05-cae0-29cc-75cb-95142386d2d1
---

# OS Deployment Driver Supported Platforms Schema - Configuration Manager | Microsoft Learn

The following reference section documents the XML schema that is used to specify the platforms that are supported by an operating system deployment driver in Microsoft Configuration Manager.

The schema is used in the `SMS_Driver` class `SDMPackageXML` property.

Caution

The supported platforms portion of `SDMPackageXML` is the only part of the Driver XML schema that can be edited. You should not make changes to other parts of the XML.

## Supported Platform XML

&lt;[PlatformApplicabilityConditions](platformapplicabilityconditions)&gt;

&lt;[PlatformApplicabilityCondition](platformapplicabilitycondition)&gt;

&lt;[Query1](query1)&gt;&lt;/Query1&gt;

&lt;[Query2](query2)&gt;&lt;/Query2&gt;

&lt;/PlatformApplicabilityCondition&gt;

&lt;/PlatformApplicabilityConditions&gt;