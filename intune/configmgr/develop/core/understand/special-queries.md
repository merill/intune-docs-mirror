---
layout: Conceptual
title: Special Queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries
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
description: Extended WMI Query Language (WQL) supports queries that are specific to Configuration Manager needs.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 29e77b5d-284e-719a-6162-cc4ee0e13d68
document_version_independent_id: 0e08398e-c2ce-9025-ccdc-b9f3d7dd7518
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/special-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/special-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/special-queries.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 77207e9e-073c-005c-1f3e-244a333f6a45
---

# Special Queries - Configuration Manager | Microsoft Learn

Extended WMI Query Language (WQL) supports queries that are specific to Configuration Manager needs. The following table describes the additional queries that are supported.

Array property Particular values in an array property.

Base class Property values that exist in a base class.

Prototype A class definition rather than class data.

Collection-limiting Data that is specific to a particular collection.

## Array Property Queries

Due to the nature of array properties, including them in an extended WQL query can be somewhat complex. For example, consider the `SMS_R_System` class that includes the `IPAddresses` property. The `IPAddresses` property is an array that contains one or more individual addresses. To query for computers with IP addresses, you can specify one of the following two queries.

SELECT \* FROM SMS\_R\_System WHERE IPAddresses = "2.2.2.2"

SELECT \* FROM SMS\_R\_System WHERE IPAddresses IN ("1.1.1.1", "2.2.2.2")

## Base Class Queries

Extended WQL queries on a base class return instances from all the subclasses. For abstract base class queries, the instances that are returned are always instances of the derived classes. For example, the following query returns instances from classes such as `SMS_SCI_Component` and `SMS_SCI_Address`, which inherit properties from `SMS_SiteControlItem`.

`SELECT * FROM SMS_SiteControlItem WHERE Sitecode="ABC"`

## Prototype Queries

Extended WQL allows you to request that the result set contains a definition of the class to be returned rather than the actual instances of the class. There are two possible results from this type of query. For most cases, a prototype query returns a class object that contains the definition. If the query is a JOIN operation with multiple classes in the SELECT statement, the prototype query returns an instance of the \_\_Generic class.

Although prototype queries are most useful in processing the results of JOIN operations, they are supported for all queries. To request a class definition as the result set, set the `lFlags` parameter in `IWbemServices::ExecQuery` or `IWbemServices::ExecQueryAsync` to WBEM\_FLAG\_PROTOTYPE.

## Collection-limiting Queries

A Configuration Manager collection is a grouping of resources such as computers and users. Extended WQL supports queries against particular collections. There are two approaches that you can use to limit a query to a particular collection:

Set the LimitToCollectionIDs context value to the required CollectionID value. This context value is made available through the IWbemContext pointer in the `IWbemServices::ExecQuery` method to the name of the collection.

Specify an inner JOIN operation by using the `SMS_CollectionMember`-derived classes in the query that is passed to ExecQuery.

The second approach is slower, but it is the only possible approach if you use an application that uses the WMI ODBC Adapter.