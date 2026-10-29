---
layout: Conceptual
title: Troubleshoot BitLocker - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/troubleshoot
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
description: Learn how to troubleshoot problems with BitLocker management in Configuration Manager
ms.date: 2019-11-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: troubleshooting
ms.collection: tier3
locale: en-us
document_id: 6b5e82cc-d641-a148-6277-ace32bf1fee3
document_version_independent_id: 7dfcf122-da46-eb5f-44f1-6ac2f307e775
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/tech-ref/bitlocker/troubleshoot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/tech-ref/bitlocker/troubleshoot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/tech-ref/bitlocker/troubleshoot.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 252ff8f1-a98a-64b7-5f23-3df282f1d486
---

# Troubleshoot BitLocker - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information in this article to help you troubleshoot issues with BitLocker management in Configuration Manager.

## Server error in self-service

When trying to open the self-service portal (`https://webserver.contoso.com/SelfService`) for the first time, you see the following error message:

```error
Configuration Error - Server Error in '/SelfService' Application

Description: An error occurred during the processing of a configuration file required to service this request. Please review the specific error details below and modify your configuration file appropriately.

Parser Error Message: Could not load file or assembly 'System.Web.Mvc, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.
```

To fix this issue, make sure you installed the [prerequisite](../../plan-design/bitlocker-management#prerequisites) for **Microsoft ASP.NET MVC 4.0** on the web server.