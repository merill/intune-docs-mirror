---
layout: Conceptual
title: SMS_MigrationEntity Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class
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
description: Learn how to represent the gathered object entities from the Configuration Manager 2007 hierarchy using SMS_MigrationEntity.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9e5fb79e-e8f3-d3cd-fffb-5eb67e54421c
document_version_independent_id: f589eb03-bd07-5c65-da9a-548ee21783be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8586e59a-795e-f09b-3984-54ea290af76a
---

# SMS_MigrationEntity Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationEntity` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the gathered object entities from the Configuration Manager 2007 hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationEntity : SMS_BaseClass
{
    Boolean ChangedAffinity;
    UInt32 DashboardState;
    UInt32 EntityID;
    String EntityKey;
    String EntityName;
    String ExcludedBy;
    Boolean IsActive;
    UInt32 JobIDs[];
    UInt32 ObjectTypeID;
    UInt32 ReferencedEntities[];
    UInt32 ReferencingEntities[];
    UInt32 SourceSiteID;
    UInt32 Status;
    UInt32 Type;
};
```

## Methods

The following table lists the methods in the `SMS_MigrationEntity` class.

| Method | Description |
| --- | --- |
| [ExcludeAndInclude Method in Class SMS_MigrationEntity](excludeandinclude-method-in-class-sms_migrationentity) | Marks the entities as excluded or included. |
| [GetEntityReferences Method in Class SMS_MigrationEntity](getentityreferences-method-in-class-sms_migrationentity) | Gets the referenced entities of the specified entities. |

## Properties

`ChangedAffinity` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this object should be included in changed object type job.

`DashboardState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration]

Entity dashboard state. Possible values are:

| Value | Entity dashboard state |
| --- | --- |
| 0 | Remaining |
| 1 | Migrated |
| 2 | Excluded |

`EntityID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Entity ID.

`EntityKey` Data type: `String`

Access type: Read-only

Qualifiers: none

Entity key imported from a Configuration Manager 2007 site.

`EntityName` Data type: `String`

Access type: Read-only

Qualifiers: none

Name of the entity.

`ExcludedBy` Data type: `String`

Access type: Read-only

Qualifiers: none

Excluded by user.

`IsActive` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this object is from an active site.

`JobIDs` Data type: `UInt32 Array`

Access type: Read-only

Qualifiers: [lazy]

Jobs containing this entity.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Sub-type of entity.

`ReferencedEntities` Data type: `UInt32 Array`

Access type: Read-only

Qualifiers: [lazy]

Entities directly referenced by this entity.

`ReferencingEntities` Data type: `UInt32 Array`

Access type: Read-only

Qualifiers: [lazy]

Entities directly referencing this entity.

`SourceSiteID` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Source site ID.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration]

Entity migration status. Possible values are:

| Value | Entity migration status |
| --- | --- |
| 0 | AVAILABLETOMIGRATE |
| 1 | MIGRATED |
| 2 | RUNNING |
| 3 | FAILED |
| 4 | EXCLUDED |
| 6 | MODIFIED |
| 7 | REMOVED |
| 8 | PENDINGSCHEDULE |
| 9 | SCHEDULED |

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Type of entity.

## Remarks

Each instance represents an object like a collection, a package, or a configuration item, carrying the basic metadata for the entities, such as name, status, and the unique key.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).