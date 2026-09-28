---
layout: Conceptual
title: SQL View Security - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sql-view-security
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
description: Facilitate instance (or row) level security on core object classes. Using the Configuration Manager schema views, an application or user is operating outside of this security mechanism.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e3f1f16d-2859-32f1-9f43-7c359900aa65
document_version_independent_id: 0bf4da0e-1b8a-fa7e-3147-288fe1d8dedc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sql-view-security.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sql-view-security
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sql-view-security.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: f9d20cae-cb1f-4dc7-a220-71601ceadeac
---

# SQL View Security - Configuration Manager | Microsoft Learn

The Configuration Manager object security mechanism, implemented in the SMS Provider, facilitates instance (or row) level security on core object classes. By using the Configuration Manager schema views, an application or user is operating outside of this security mechanism. This doesn't mean that the views can't be secured from unauthorized data access; however, security must be configured separately and is less precise than standard Configuration Manager object security. You can give a user read-only permission to access only the views and deny access to any internal Configuration Manager tables. The main security functionality that is lost in the view approach is the ability to secure specific object instances (such as packages and collections) separately for members of groups.