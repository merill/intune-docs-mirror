---
layout: Conceptual
title: SMS Provider Field Length Restrictions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions
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
description: Learn about the SMS Provider Field Length Restrictions on the width of character fields for schema classes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 27db24c4-20b7-4376-936a-eeec6121e830
document_version_independent_id: 271a50bc-c1fe-f586-a9da-eb50755fdceb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sms-provider-field-length-restrictions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 8ad528ec-2894-ccf9-5f78-018c30e3fd41
---

# SMS Provider Field Length Restrictions - Configuration Manager | Microsoft Learn

The SMS Provider places restrictions on the width of character fields for schema classes. If you write a program that writes to these classes, you should take these field widths into account. Where they are used in the user interface, the SMS online Help provides the maximum character widths. You can also determine the width by dividing the corresponding schema class table column width by two to give the field width in characters.

You can determine the schema class table column width from the corresponding SQL Server views. For information about mapping schema classes to SQL Server views, see SMS Schema View Mapping. The steps for obtaining the table column width from the SQL Server view in SQL Server are:

- Open the SQL Server view's properties to see which table and table columns it uses.
- Open the corresponding table in the database Tables view to discover the column width.

    Classes that are commonly affected by this restriction are:
- SMS\_Package
- SMS\_Advertisement
- SMS\_Program
- SMS\_DistributionPoint
- SMS\_PDF\_Package
- SMS\_PDF\_Program
- SMS\_Query
- SMS\_Report
- SMS\_ReportDashboard
- SMS\_ReportViewSchema
- SMS\_CollectionRuleQuery
- SMS\_Collection
- SMS\_UserInstancePermissions
- SMS\_UserClassPermissions
- SMS\_UserInstancePermissionNames
- SMS\_UserClassPermissionNames