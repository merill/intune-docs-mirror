---
layout: Conceptual
title: What's new in version 2503 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2503
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
description: Get details about changes and new capabilities introduced in version 2503 of Configuration Manager current branch.
ms.date: 2025-03-31T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: e23cf638-79e7-fdfe-1061-1a6e7573d5a5
document_version_independent_id: e23cf638-79e7-fdfe-1061-1a6e7573d5a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2503.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2503
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2503.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 6e33b015-3557-c2a8-68bb-283bcee1ebcd
---

# What's new in version 2503 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2503 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2309 or later.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2503](../../servers/manage/checklist-for-installing-update-2503). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2503#post-update-checklist).

To take full advantage of new Configuration Manager changes, after you update the site, also update clients to the latest version. New functionality appears in the Configuration Manager console when you update the site and console, but the complete scenario isn't functional until the client version is also the latest.

## General enhancements

As part of Microsoft's Secure Future Initiative (SFI) the 2503 version of Configuration Manager focuses on security and quality updates. For more information, see the [Microsoft Trust Center](https://www.microsoft.com/trust-center/security/secure-future-initiative). For a list of significant customer-reported issues resolved in this release, see the [Summary of changes in Configuration Manager version 2503](../../../hotfix/2503/31909343) knowledge base article.

## Known Issues

- Upgrade SQL 2012 or 2014 Express, Standard, Enterprise edition to SQL 2016 or latest version. **VC++ Redistributable Version** needs to be upgraded to latest version on **Secondary sites**. [Download Latest Microsoft Visual C++ Redistributable Version](https://aka.ms/vs/17/release/vc_redist.x64.exe).

### Microsoft ODBC redistributable

- The Microsoft ODBC redistributable component is updated to version **18.4.1.1** on all Site servers and Management Points.
- ConfigMgrPreReq will throw an error stalling the upgrade if it detects a version lower than that.

> 
> INFO: Microsoft ODBC Driver 18 for SQL Server is installed but it is older than the required version. SQL client prerequisite missing for Configuration Manager setup.; Error; Install the Microsoft ODBC driver 18 for SQL setup from https://go.microsoft.com/fwlink/?linkid=2299909. More information https://go.microsoft.com/fwlink/?linkid=2226618