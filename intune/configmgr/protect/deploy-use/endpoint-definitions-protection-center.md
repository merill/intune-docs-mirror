---
layout: Conceptual
title: Download definitions from MMPC - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-definitions-protection-center
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
description: Configure Configuration Manager clients to download Endpoint Protection definition updates from the Microsoft Malware Protection Center (MMPC).
ms.date: 2017-02-14T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 883b574a-a571-bd63-1d43-8550eb70a3f1
document_version_independent_id: 5a93a665-9532-3a18-eb00-997e2f390ea5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-definitions-protection-center.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-definitions-protection-center
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-definitions-protection-center.md
cmProducts: []
platformId: 7a696b1d-6fdc-c602-cd00-9e44118c6227
---

# Download definitions from MMPC - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can configure clients to download definition updates from the Microsoft Malware Protection Center. This option is used by Endpoint Protection clients to download definition updates if they have not been able to download updates from another source. This update method can be useful if there is a problem with your Configuration Manager infrastructure that prevents the delivery of updates.

Important

Clients must have access to Microsoft Update on the Internet to be able use this method to download definition updates.

[Next step &gt;](endpoint-antimalware-policies)

[Back &gt;](endpoint-configure-alerts)