---
layout: Conceptual
title: Schema view mapping - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping
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
description: Learn how the SQL Server schema of the Configuration Manager site database maps to the WMI schema.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 66cf9349-96a5-add2-a75d-6b22b03cf31d
document_version_independent_id: 4f8a50a4-2d12-d683-a0b3-79aad165dd7e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-schema-view-mapping
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 5aeca177-3bda-6935-6eb8-b15d6e83c46a
---

# Schema view mapping - Configuration Manager | Microsoft Learn

In Configuration Manager, the names of views and columns are designed to be as close to the SMS Provider Windows Management Instrumentation (WMI) schema as possible. Because the views names and view column names must be valid SQL Server identifiers, there are some discrepancies between WMI and SQL Server names. However, in most cases the following rules can be applied to convert a WMI class name to its corresponding SQL Server view:

- Replace SMS\_ with v\_ for the start of the view name.
- If a view name is longer than 30 characters, it's truncated.
- WMI property names are the same in the SQL Server views for non-inventory or discovery classes.

    Beyond this, the following class families have a differing nomenclature for their view equivalents:

## System Inventory Views

The syntax for the current inventory group is v\_GS*\_&lt;group name&gt;* (for example, v\_GS\_Tape\_Drive).

The syntax for the history inventory group is v\_HS*\_&lt;group name&gt;*(for example, v\_HS\_Tape\_Drive).

Note

There is no equivalent Extended History view (WMI class SMS\_GEH\_System*\_&lt;group name&gt;*) because it is implemented as a stored procedure.

## Custom Architecture Views

The syntax for the current groups is v\_G*&lt;resource type number&gt;\_&lt;group name&gt;* (for example, v\_G6\_VendorData).

In the previous example, it's assumed that a new inventory architecture, for example VendingMachine, has been added to the system and assigned the resource type number 6 and VendorData is an inventory group that is associated with the architecture. The resource type number might be related to the resource type name and its group's classes using the schema information views.

The corresponding history inventory classes will use the suffix H in place of G.

## Discovery Views

The views for discovery data differ from their WMI counterparts in that array properties in WMI are represented as separate views. For example, for the System resource, all the scalar properties are contained in the view v\_R\_System. There are many view tables for the array values, such as v\_RA\_System\_IPAddresses and v\_RA\_System\_MACAddresses. The general rules for the syntax of these views are:

- Scalar class: v\_R*\_&lt;resource type name&gt;*
- Array class: v\_RA*&lt;architecture name&gt;\&lt;group name&gt;*

    Each array property view has just two columns: ResourceID and a column that contains the actual data. For example, for the view v\_RA\_System\_IPAddresses the data column is v\_RA\_System\_IPAddresses. As with inventory groups for the discovery view, column names differ from those of WMI classes. Each column ends with a zero character, ensuring uniqueness with SQL Server reserved words. In general, this is the only difference between the WMI and view column names although there are exceptions.

    For more information about the classes that Configuration Manager supports, see [Configuration Manager Reference](../../reference/configuration-manager-reference).