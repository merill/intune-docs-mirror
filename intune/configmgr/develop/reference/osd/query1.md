---
layout: Conceptual
title: Query1 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query1
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
description: Query1 specifies a query, in Configuration Manager, that is used to identify the platform that a client computer is running.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 05baa06c-4633-a673-cdb8-82a5c2f6cc0e
document_version_independent_id: 8f13b247-3b1a-c1a0-33c9-fbccd3f66898
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/query1.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/query1
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/query1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: ba4d1d20-7059-f6da-f64a-03acb20e3957
---

# Query1 - Configuration Manager | Microsoft Learn

**Query1** specifies a query, in Configuration Manager, that is used to identify the platform that a client computer is running.

Note

This information should come from `SMS_SupportedPlatforms Server WMI Class` objects and match the platform information specified in the PlatformApplicabilityCondition node.

The query is run on the client computer and typically inspects Windows Management Instrumentation (WMI) to determine the client platform. For example, `SELECT * FROM Win32_OperatingSystem WHERE BuildNumber = '3790' AND OSType=18 AND ProductType=1`.

**Type**: Element.

**Instances**: One.

## Attributes

None