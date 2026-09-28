---
layout: Conceptual
title: Schema Overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-overview
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
description: This article discusses the Configuration Manager Schema Overview.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 51104d8c-15bf-574e-f5e1-fef4ed66ff69
document_version_independent_id: 5b62bc71-72ce-eb2b-4d8f-673880e68299
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-schema-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-schema-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-schema-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0ce7441f-6b3c-380b-e211-0ec8564d50c6
---

# Schema Overview - Configuration Manager | Microsoft Learn

Configuration Manager uses Windows Management Instrumentation (WMI) to manage its objects. Any managed object, such as a disk drive or a collection of computers, can be represented by an instance of a Configuration Manager class. Configuration Manager also includes classes that represent Configuration Manager features, such as software distribution. Collectively, these Configuration Manager classes are known as the Configuration Manager schema.

Configuration Manager uses a Microsoft SQL Server database to store managed object data. Both SQL Server and the WMI API can be used to view and manipulate Configuration Manager managed data. The SMS Provider acts as an intermediary between Configuration Manager site information and WMI by supplying both class and instance data.

## Server

The Configuration Manager classes that represent the Configuration Manager server schema are generally declared in the SMSProv.mof file. This file contains the base classes, static classes, and methods that the SMS Provider supports. Other class definitions, notably those that support inventory, are determined at run time by the SMS Provider. When requested, these class definitions are supplied to WMI. These are called run-time classes. The SMSProv.mof file is located in the \Bin\&lt;*Platform*&gt;\ directory under the Configuration Manager install directory.

For more information about using these Configuration Manager classes by using WMI or managed code, see [Objects overview](configuration-manager-objects-overview).

You can also use SQL Views for fast, read-only access to the Configuration Manager schema data. For more information, see [Configuration Manager Schema SQL Views](configuration-manager-schema-sql-views)

## Client

A number of Managed Object Format (MOF) files represent the client Configuration Manager schema. The client includes schemas that can be used for items such as inventory, policy, and software distribution management.

For more information about using client objects with WMI or managed code, see [About client WMI programming](../clients/programming/about-configuration-manager-wmi-programming).

## Classes

For more information about the classes that Configuration Manager supports, see [Configuration Manager Reference](../../reference/configuration-manager-reference).