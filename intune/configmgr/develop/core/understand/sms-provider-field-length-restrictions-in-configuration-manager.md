---
layout: Conceptual
title: SMS Provider Field Length Restrictions in Configuration Manager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions-in-configuration-manager
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: Places restrictions on the width of character fields for schema classes.
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b0438fee-a212-2ba8-b914-3b0aa7c7d76c
document_version_independent_id: b231b3bc-1d55-eddf-6068-f13ae11efec5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions-in-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sms-provider-field-length-restrictions-in-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions-in-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 25a0094d-8434-1908-4fad-6ba25fdd2679
---

# SMS Provider Field Length Restrictions in Configuration Manager - Configuration Manager | Microsoft Learn

The SMS Provider, in Configuration Manager, places restrictions on the width of character fields for schema classes. If you write a program that writes to these classes, you should take these field widths into account. Where they are used in the user interface, the Configuration Manager online Help provides the maximum character widths. You can also determine the width by dividing the corresponding schema class table column width by two to give the field width in characters.

You can determine the schema class table column width from the corresponding SQL Server views. For information about mapping schema classes to SQL Server views, see [Configuration Manager Schema View Mapping](configuration-manager-schema-view-mapping). The steps for obtaining the table column width from the SQL Server view in Microsoft SQL Server are:

1. Open the properties of the SQL Server view to see which table and table columns it uses.
2. Open the corresponding table in the database tables view to discover the column width.

    Classes that are commonly affected by this restriction are:

- `SMS_Package`
- `SMS_Advertisement`
- `SMS_Program`
- `SMS_DistributionPoint`
- `SMS_PDF_Package`
- `SMS_PDF_Program`
- `SMS_Query`
- `SMS_Report`
- `SMS_ReportDashboard`
- `SMS_ReportViewSchema`
- `SMS_CollectionRuleQuery`
- `SMS_Collection`
- `SMS_UserInstancePermissions`
- `SMS_UserClassPermissions`
- `SMS_UserInstancePermissionNames`
- `SMS_UserClassPermissionNames`