---
layout: Conceptual
title: SMS provider WMI schema reference - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sms-provider-wmi-schema-reference-configuration-manager
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
description: How Configuration�Manager uses Windows Management Instrumentation (WMI) to manage its objects.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 058a2494-6d31-eeb5-2aef-33d3ea35d38a
document_version_independent_id: 8a544518-86f8-be71-dd7f-cb70a4f35ce0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sms-provider-wmi-schema-reference-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sms-provider-wmi-schema-reference-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sms-provider-wmi-schema-reference-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: f62e5275-58be-483d-e796-01251453586a
---

# SMS provider WMI schema reference - Configuration Manager | Microsoft Learn

Configuration�Manager uses Windows Management Instrumentation (WMI) to manage its objects. Any managed object, such as a disk drive or a collection of computers, can be represented by an instance of a Configuration Manager class. Configuration Manager also includes classes that represent features, such as software deployment or software updates. Collectively, these Configuration Manager classes comprise the SMS Provider WMI schema.

Configuration Manager uses a SQL Server database to store managed object data. Both SQL Server and WMI can be used to view Configuration Manager managed data. A new query or collection created in the Configuration Manager console uses a WMI Query Language (WQL) query to request the Configuration Manager object data from the SMS Provider WMI Schema, which in turn retrieves the data from the site database. When creating a custom report in Configuration Manager, report SQL statements retrieve the Configuration Manager object data from SQL views in the site database, which in turn retrieve the data from one or more SQL views or tables.

## SQL view and SMS provider WMI schema relationship

Many of the SQL view and view column names used by Configuration Manager are designed to be as close to the SMS Provider WMI schema as possible. Other SQL views retrieve data from other views or from multiple tables or views, and there is no direct mapping to the SMS Provider WMI schema. Also, because the SQL view and view column names must be valid SQL identifiers, there are some discrepancies between WMI and SQL names when there is a mapping. In most cases, the following general rules can be applied to convert a WMI class name to its corresponding SQL view:

- At the start of the view name, **v\_** replaces **SMS\_**.
- If a view name is longer than 30 characters, it is truncated.
- WMI property names are the same in the views for inventory or discovery classes.

For example, if you wanted to convert the WMI class **SMS\_Advertisement** to the associated SQL view, you would remove the **SMS\_** and replace it with **v\_**, resulting in the appropriate view name of **v\_Advertisement**.

## SQL view query

```sql
    SELECT AdvertisementID, PackageID, CollectionID, SourceSite 
    FROM v_Advertisement 
```

In this example, the query returns the following rows.

| AdvertismentID | PackageID | CollectionID | SourceSite |
| --- | --- | --- | --- |
| MCM20000 | MCM00003 | SMS00001 | MCM |
| MCM20001 | MCM00002 | SMS00004 | MCM |
| MCM20002 | MCM00006 | SMS00001 | MCM |

## WQL query

```sql
    SELECT AdvertisementID, PackageID, CollectionID, SourceSite 
    FROM SMS_Advertisement 
```

In this example, the query returns identical rows to the SQL view query above.

## Configuration Manager SQL view design

When there is no direct mapping for a SQL view and the SMS Provider WMI schema class and you want to determine where the data in the SQL view comes from, you can look at the SQL view design. This helps determine whether a SQL view is retrieving data from a single SQL table, from another SQL view, or from more than one table or view. When the SQL view retrieves data from more than one table or view, the SQL view will most likely map to more than one class in the SMS Provider WMI schema. Use the following procedure to display the SQL view design.

Warning

Do not modify the design of built-in Configuration Manager SQL views as this might result in errors in reporting and in your site functionality.

### To display the SQL view design

1. Start Microsoft SQL Server Management Studio on the server that hosts the Configuration Manager site database.
2. Navigate to *&lt;Computer Name&gt;�*\ Databases \*�&lt;Configuration Manager database name&gt;***\ Views**.
3. Right-click the SQL view in which you want to see the design, and then select **Design**. The **SQL** pane displays the SQL statement. Look at the table or view name just after the FROM clause to figure out where the view is retrieving its data. When the view retrieves data from more than one source, the table or views will use JOINS.