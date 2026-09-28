---
layout: Conceptual
title: Collection views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/collection-views-configuration-manager
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
description: Information about the collections, collection rules, and collection members.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ba245043-ea0c-b32b-5a77-6704a587e260
document_version_independent_id: 65611806-b368-4e91-c3c0-afa4cadcfda8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/collection-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/collection-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/collection-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: db09f2a3-c97e-8c7d-2c0f-b4a6f33d3e1f
---

# Collection views - Configuration Manager | Microsoft Learn

Collection views contain information about the collections, collection rules, and collection members. Many of the collection views are useful when creating reports on site data, software update deployments, application deployments, and compliance settings.

The two types of collection views are as follows:

- The first type lists all members of a specific collection and starts with the **v\_CM\_RES\_COLL\_** view name and ends with the collection ID, with the exception of the **v\_FullCollectionMembership** view, which lists all members of all collections. This collection type will be used most often when creating reports.
- The second type of collection view has a name that starts with **v\_** and contains general information about the collections but not the member resources within each collection.

## Collection views

The collection views are described in this section.

### v\_ClientCollectionMembers

Lists all devices, by resource ID, that are not in an obsolete or decommissioned state, what collections the device is a member of, and whether the resource is a Configuration Manager client. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_CM\_RES\_COLL\_&lt;CollectionID&gt;

Lists all devices that are members of the collection. The device ID, name, client GUID, site code, whether the computer is assigned to a site, whether the computer has been approved, whether the computer is an active client, and so on. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_Collection

Lists all collections by collection ID, collection name, and what view the collection maps to (listed in the **v\_CM\_RES\_COLL\_&lt;***CollectionID***&gt;** row), the last time the collection membership changed, as well as other collection information. The view can be joined to other views by using the **CollectionID** column.

### v\_CollectionRuleDirect

Lists the collections that contain direct membership rules. The view can be joined to other views by using the **CollectionID** or **ResourceID** columns.

### v\_CollectionRuleQuery

Lists the query statement for each query-based collection. The view can be joined to other views by using the **CollectionID** and **LimitToCollectionID** columns.

### v\_CollectionSettings

Lists the configured settings for each collection, such as restart countdown, polling interval, collection variable precedence, source site, last modification time, and more. The view can be joined to other views by using the **CollectionID** column.

### v\_CollectionVariable

Lists the collections that have associated task sequence variables. The view can be joined to other views by using the **CollectionID** column.

### v\_FullCollectionMembership

Lists the resources for all collections. Contains the collection ID, resource ID, name, domain, resource GUID, site code, and other client information. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_FullCollectionMembership\_Valid

Lists the resources that are not in an obsolete or decommissioned state for all collections and contains a subset of information from the **v\_FullCollectionMembership** view. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_ServiceWindow

Lists all collections that have a configured maintenance window and information about the maintenance window, such as the maintenance window name, description, start time, and duration. The view can be joined to other views by using the **CollectionID** column.

### v\_Collections

Lists all collections by collection ID and collection name. Also contains further information about each collection, for example:

- The last time the collection was changed (**LastChangeTime**)
- The last time the collection was re-evaluated (**LastRefreshRequest**)
- The collections limiting collection (**LimitToCollectionID**)
- Whether the collection is built-in, or was created by an administrator (**IsBuiltIn**)

The view can be joined to other views by using the **CollectionID** column.