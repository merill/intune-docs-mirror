---
layout: Conceptual
title: SMS_MigrationCollectionInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationcollectioninfo-server-wmi-class
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
description: The SMS_MigrationCollectionInfo WMI class is an SMS Provider server class that represents the collections created on the current active 2007 hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a270371b-6c0a-7955-2647-5688086c17d4
document_version_independent_id: 2fa4b123-f566-30d1-3234-447a428e6120
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationcollectioninfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationcollectioninfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationcollectioninfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e13de6c5-dc62-d8bd-07b8-9b46e70956ab
---

# SMS_MigrationCollectionInfo Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationCollectionInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the collections created on the current active Configuration Manager 2007 hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationCollectionInfo : SMS_BaseClass
{
    UInt32 ChildCount;
    String Children;
    UInt32 CollectionEntityID;
    String CollectionName;
    UInt32 CollectionType;
    UInt32 Count;
    Boolean IsTop;
    UInt32 LimitToCount;
    String LimitTos;
    UInt32 SiteCodeCount;
    String SiteCodes;
    String SourceSiteCollectionID;
    UInt32 SourceSiteID;
    UInt32 Status;
};
```

## Methods

The following table lists the methods in the `SMS_MigrationCollectionInfo` class.

| Method | Description |
| --- | --- |
| [GetClientsCountByCollections Method in Class SMS_MigrationCollectionInfo](getclientscountbycollections-method-in-class-sms_migrationcollectioninfo) | Retrieves the number of clients in the specified collection. **Warning:** This method is reserved for future use. |

## Properties

`ChildCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The count of child collections.

`Children` Data type: `String`

Access type: Read-only

Qualifiers: none

The child collection Ids, separated by ','.

`CollectionEntityID` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Entity ID of this collection.

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: none

Display name of the collection.

`CollectionType` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The type of the collection.

| Value | Collection type |
| --- | --- |
| 0 | Mixed |
| 1 | User |
| 2 | Device |
| 3 | UnknownArchitecture |
| 4 | UnknownQuery |
| 5 | Folder |

`Count` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The total number of devices or users in this collection.

`IsTop` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if the collection is a top collection which linked to the root.

`LimitToCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The total number of collections that the collection is limited to.

`LimitTos` Data type: `String`

Access type: Read-only

Qualifiers: none

The string that concatenate all ID of collections that the collection is limit to, separated by ','.

`SiteCodeCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The count of site codes embedded in the query.

`SiteCodes` Data type: `String`

Access type: Read-only

Qualifiers: none

The string that concatenate all site codes that embedded in the collection query string, separated by ','.

`SourceSiteCollectionID` Data type: `String`

Access type: Read-only

Qualifiers: [key]

Unique identifier for the collection in the source site.

`SourceSiteID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Unique identifier for the source site in `SMS_MigrationSourceSite`.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Status of the collection.

## Remarks

Each instance of this class represents a collection.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).