---
layout: Conceptual
title: Schema views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/schema-views-configuration-manager
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
description: Information about the schema that can be used when creating reports.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 329e9d64-7254-fa9c-4025-e921314deb8a
document_version_independent_id: 9193643e-362f-0704-faf9-4ae4f7bd8ad2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/schema-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/schema-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/schema-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 39913821-00d2-4acf-b601-e4a7a6c31a04
---

# Schema views - Configuration Manager | Microsoft Learn

The Configuration�Manager schema views provide information about the schema that can be used when creating reports, as well as the discovery schema views, inventory schema views, and the compliance settings schema view.

## View schema views

The Configuration Manager view schema views can be joined together and used to retrieve specific data. They provide information about all of the views in a Configuration Manager site that are in the Configuration Manager view schema family. The view schema views are described in this section.

### v\_SchemaViews

Lists all the SQL views and SQL view types in the view schema family. The view can be joined to the **v\_ReportViewSchema** view by using the **ViewName** column.

### v\_ReportViewSchema

Lists all the Configuration Manager SQL views in the view schema family and the column names for each view. The view can be joined to the **v\_ReportViewSchema** view by using the **ViewName** column.

The following query uses the **v\_SchemaViews** view to retrieve a list of all the view schema family views and their associated view category:

```sql
SELECT Type, ViewName

FROM v_SchemaViews

ORDER BY Type, ViewName
```

Each of the Configuration Manager views has multiple columns, and determining which of these columns to use when building queries for the required data can be difficult. The following query joins the **v\_SchemaViews** and **v\_ReportViewSchema** views to list all of the views in the Configuration Manager view schema family, each of the columns within each view, and the view category:

```sql

SELECT RVS.ViewName, RVS.ViewColumnName, SV.Type

FROM v_SchemaViews as SV INNER JOIN v_ReportViewSchema as RVS

��ON SV.ViewName = RVS.ViewName

ORDER BY SV.Type, RVS.ViewName, RVS.ViewColumnName
```

The output from this query and the information provided throughout this document provide information to help you use the correct view and view column to build queries for effective reporting.

## Discovery schema views

The discovery schema views provide information about all resources in a Configuration Manager site and are described in this section. The two resource schema information views are **v\_ResourceMap** and **v\_ResourceAttributeMap**. The **v\_ResourceMap** view contains a list of all the resource types for discovered data. By default, Configuration Manager has the **Unknown System**, **User Group**, **User**, and **System Resource** types, each of which has its own resource type number and individual view. The view can be joined to other views by using the **ResourceType** column. his section represents the default data contained in the **v\_ResourceMap** view.

| Resource type | Display name | Resource class name |
| --- | --- | --- |
| 2 | Unknown System | **v\_R\_UnknownSystem** |
| 3 | User Group | **v\_R\_UserGroup** |
| 4 | User | **v\_R\_User** |
| 5 | System | **v\_R\_System** |
| 6 | IP Network | **V\_R\_IPNetwork** |

The **v\_ResourceAttributeMap** view contains all of the attributes that will be discovered for each of the resource types, such as NetBIOS name, operating system, user name, user group name, domain name, and so forth. The **v\_ResourceAttributeMap** view can be joined to other views by using the **ResourceType** column. For more information about the discovery views, see [Discovery Views in Configuration Manager](discovery-views-configuration-manager).

## Hardware inventory schema views

The hardware inventory schema is important to understand when creating queries for Configuration Manager reports that contain hardware inventory information. Most of the client data within Configuration Manager is contained in one of the two hardware inventory schema views: **v\_GroupMap** and **v\_GroupAttributeMap**. The **v\_GroupMap** view contains a list of all the hardware inventory groups and the associated view for each of the groups. The **v\_GroupAttributeMap** view contains all of the attributes that are inventoried for each of the groups. Both views can be joined together by using the **GroupID** column and joined to the **v\_ResourceMap** discovery schema view by using the **ResourceType** column.

Because hardware inventory can be modified and extended, one Configuration Manager site's SQL Server database might have different hardware inventory views and schema when compared to another site. The following query joins the **v\_GroupMap** and **v\_GroupAttributeMap** views to generate the hardware inventory view schema, based on the specific settings for the site:

```sql
SELECT DISTINCT GM.DisplayName, GM.InvClassName,

��GM.InvHistoryClassName, GAM.AttributeName,

��GAM.ColumnName, GM.MIFClass

FROM v_GroupMap GM INNER JOIN v_GroupAttributeMap GAM

��ON GM.GroupID = GAM.GroupID
```

For more information about the hardware inventory views, see [Hardware Inventory Views in Configuration Manager](hardware-inventory-views-configuration-manager).

## Software inventory view schema

There is not a specific software inventory schema view, but the following query joins the **v\_GS\_SoftwareProduct** and **v\_FullCollectionMembership** software inventory views to generate the software inventory view schema by product name for the **All Systems** collection:

```sql
SELECT MIN(PRD.ProductID) AS ProductID, PRD.ProductName,

PRD.ProductVersion, COUNT(DISTINCT PRD.ResourceID) AS 'Count'

FROM v_GS_SoftwareProduct PRD INNER JOIN v_FullCollectionMembership FCM

ON PRD.ResourceID = FCM.ResourceID

WHERE FCM.CollectionID = 'SMS00001'

GROUP BY PRD.ProductName, PRD.ProductVersion

ORDER BY PRD.ProductName
```

For more information about the software inventory views, see [Software Inventory Views in Configuration Manager](software-inventory-views-configuration-manager).

## Compliance settings schema view

There is one compliance settings schema view, **v\_CIRelationTypeMapping**, that lists the configuration item elements, such as configuration baselines and software updates, the relation type value, and a description for the relation type. The view can be joined to other compliance settings views by using the **RelationType** column. For more information about the desired configuration management views, see [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager).