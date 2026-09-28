---
layout: Conceptual
title: Extended WMI Query Language - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language
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
description: A superset of the Windows Management Instrumentation (WMI) Query Language (WQL) known as Extended WQL. Configuration Manager supports both WQL and Extended WQL.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 7b51dd84-d3fb-d946-cbcd-ca6753591174
document_version_independent_id: d218cf35-9bda-fa88-3ffc-640685e550f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/extended-wmi-query-language.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/extended-wmi-query-language
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/extended-wmi-query-language.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9d0c20c-d325-71e5-2ab1-eb9852c12423
---

# Extended WMI Query Language - Configuration Manager | Microsoft Learn

Configuration Manager supports a superset of the Windows Management Instrumentation (WMI) Query Language (WQL) known as Extended WQL. Both WQL and Extended WQL are retrieval-only languages that are used to create queries. Neither language can be used to create, modify, or delete classes or instances.

WQL and Extended WQL are based on the American National Standards Institute (ANSI) Structured Query Language (SQL) standard. However, they differ from standard SQL in that they retrieve from classes rather than tables and return instances rather than rows.

Extended WQL supports elements from two versions of ANSI SQL:

ANSI-92, which is the recommended version for most operations.

ANSI-89, which is primarily used only for `JOIN` operations by Open Database Connectivity (ODBC) applications requiring the services of the WMI ODBC Adapter.

Extended WQL includes a much broader range of operations than WQL. The following list shows the `SELECT` clauses that Extended WQL supports:

`DISTINCT`

`COUNT`

`JOIN`

`WHERE`

`SUBSTRING`

`ORDER BY`

`UPPER, LOWER`, and `DATEPART` functions

Because Extended WQL is fully case-insensitive, the UPPER and LOWER functions are not useful. Extended WQL supports the standard comparison operators (including LIKE and IN) and sub queries.

The SMS Provider does not support querying on system properties. System properties are those preceded by a double underscore prefix, for example `__path`.

Association queries are limited to the WQL syntax.

The use of `COUNT` and `DISTINCT` keywords together in a statement is not supported.

in Configuration Manager the `WHERE` clause supports `GetDate()`, `DateDiff()`, `and DateAdd()`.

The `ORDER BY` clause does not work with the collection-limiting context qualifier.