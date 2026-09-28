---
layout: Conceptual
title: Known issues with deployments in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/deployments/known-issues
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: wicale
ms.collection:
- M365-identity-device-management
description: Review known issues and limitations for deployments during public preview in Microsoft Intune.
ms.date: 2026-08-26T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: wicale
locale: en-us
document_id: d0ebfe60-1e21-bbff-86d6-b7bc7c4cef3a
document_version_independent_id: d0ebfe60-1e21-bbff-86d6-b7bc7c4cef3a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/deployments/known-issues.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/deployments/known-issues
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/deployments/known-issues.md
platformId: ff6f6544-bcd2-fc43-f143-d7aa967202bf
---

# Known issues with deployments in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

These known issues apply to the public preview release of deployments. This list is updated as issues are resolved or identified.

The following known issues and limitations apply to deployments during public preview:

- The Deployments page does not currently support sorting options. The list is sorted based on when a ring starts in an active deployment.
- Search in the Deployments page only searches on deployment name.
- When you create a deployment for a payload protected by a Multi Admin Approval access policy, the deployment doesn't appear in the **Deployments** list until the approval is complete.
- To view the Multi Admin Approval status for a Deployment, open the deployment or use Tenant administration: Multi Admin Approval, or Admin tasks.