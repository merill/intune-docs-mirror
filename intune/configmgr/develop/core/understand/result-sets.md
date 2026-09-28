---
layout: Conceptual
title: Configuration Manager Result Sets - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/result-sets
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
description: Result sets of a query contain one or more instances that match the specified criteria of the SELECT statement in Configuration Manager. The result instances are either Generic class instances or instances of the class specified in the FROM clause.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b160ef20-2743-dea1-b308-72949b2dd38f
document_version_independent_id: 9d743340-3573-d155-558c-a68c56bc28cd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/result-sets.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/result-sets
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/result-sets.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/000aaee4-f890-4b0a-bd33-24fb2aefa882
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57828563-e363-48c1-ac42-c4d23fb7ba52
platformId: 2ce8e0ef-c873-281f-980a-95a12a9692ee
---

# Configuration Manager Result Sets - Configuration Manager | Microsoft Learn

In Configuration Manager, the result set of a query contains one or more instances that match the specified criteria of the`SELECT` statement. The result instances are either `Generic` class instances or instances of the class that is specified in the FROM clause.

## \_\_Generic Class Results

The results of a `JOIN` operation are returned in either an instance of a class specified in the query or an instance of the \_\_`Generic` class. If a single class is implied by the property list in the SELECT statement, the results are returned as instances of that class. If there are multiple classes, the results are returned as instances of the **\_\_Generic** class.

The \_\_`Generic` class is a generic container for the results of `JOIN` operations and `COUNT` operations. This class has no set definition. Its properties depend on its use at the time. For `JOIN` results, the properties are embedded objects representing the classes specified in the query, as the following example shows.

`SELECT * FROM SMS_Package AS Pack`

`INNER JOIN SMS_Program AS Prog`

`ON Pack.PackageID = Prog.PackageID`

The following example shows the \_\_Generic class result of the above query.

`Class __Generic`

`{`

`SMS_Package  Pack;`

`SMS_Program  Prog;`

`}`

For COUNT results, the instance includes a Count property, as the following class shows.

`Class __Generic`

`{`

`uint32  Count;`

`}`

## Actual Class Instance Results

The class instances that are returned in a result set contain both system and class properties. However, embedded and lazy properties are not returned.

The system properties include those for the specified class and its derived classes. Because not all system properties are relevant to all queries, the value of a particular system property can be `null`.

The class properties that are returned depend on whether you specify a property list or the asterisk. If you specify a property list containing one or more class properties, the returned instance contains only the properties in the list. The property list should include the key properties for the class. When you invoke a query that does not specify key properties in the property list, the result set contains incomplete and therefore incorrect values for the system properties, `__Path` and `__Relpath`.