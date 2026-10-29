---
layout: Conceptual
title: Security and privacy for power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/security-and-privacy-for-power-management
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
description: Get security and privacy information for power management in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a442a0db-cf7e-b12b-b137-f087672a741a
document_version_independent_id: a65bb76e-0538-7d03-7c5e-ad212cb111da
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/security-and-privacy-for-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/security-and-privacy-for-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/security-and-privacy-for-power-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 938a2f55-307c-b62e-d38d-8c4c33d043a0
---

# Security and privacy for power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This section contains security and privacy information for power management in Configuration Manager.

## Security best practices for power management

There are no security-related best practices for power management.

## Privacy information for power management

Power management uses features that are built into Windows to monitor power usage and to apply power settings to computers during business hours and nonbusiness hours. Configuration Manager collects power usage information from computers, which includes data about when a user is using a computer. Although Configuration Manager monitors power usage for a collection rather than for each computer, a collection can contain just one computer. Power management is not enabled by default and must be configured by an administrator.

The power usage information is stored in the Configuration Manager database and is not sent to Microsoft. Detailed information is retained in the database for 31 days and summarized information is retained for 13 months. You cannot configure the deletion interval.

Before you configure power management, consider your privacy requirements.