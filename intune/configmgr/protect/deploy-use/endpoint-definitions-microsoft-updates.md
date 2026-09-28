---
layout: Conceptual
title: Download definitions from Microsoft - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-definitions-microsoft-updates
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
description: Learn how to enable the download of Endpoint Protection malware definitions from Microsoft Updates for Configuration Manager.
ms.date: 2019-11-18T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 2a10ed59-6b4b-1e10-0cc2-845b7eb848b4
document_version_independent_id: a55cf106-8c28-d593-6d54-42cd36d183c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-definitions-microsoft-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-definitions-microsoft-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-definitions-microsoft-updates.md
cmProducts: []
platformId: 2449c40d-db5f-2391-d92d-4e52dd6f9a0f
---

# Download definitions from Microsoft - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you select to download definition updates from Microsoft Update, clients will check the Microsoft Update site at the interval defined in the **Security Intelligence updates** section of the antimalware policy dialog box.

This method can be useful when the client does not have connectivity to the Configuration Manager site or when you want users to be able to initiate definition updates.

Important

- Clients must have access to Microsoft Update on the Internet to be able to use this method to download definition updates.
- The **Definition updates** section was renamed to **Security Intelligence updates** starting in Configuration Manager version 1902.

## Using the Microsoft Malware Protection Center to Download Definitions

You can configure clients to download definition updates from the Microsoft Malware Protection Center. This option is used by Endpoint Protection clients to download definition updates if they have not been able to download updates from another source. This update method can be useful if there is a problem with your Configuration Manager infrastructure that prevents the delivery of updates.

Important

Clients must have access to Microsoft Update on the Internet to be able use this method to download definition updates.

[Next step &gt;](endpoint-antimalware-policies)

[Back &gt;](endpoint-configure-alerts)