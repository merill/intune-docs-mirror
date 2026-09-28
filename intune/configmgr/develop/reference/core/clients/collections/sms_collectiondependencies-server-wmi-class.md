---
layout: Conceptual
title: SMS_CollectionDependencies Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectiondependencies-server-wmi-class
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
description: An SMS Provider server class used to query dependency relationships between collections, specifically the composable collection rules, inclusion and exclusion, and the limiting collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 24682ee7-c62e-90c1-00d8-84f0b69301a1
document_version_independent_id: 5ea08788-e92b-72e4-f5d6-f107eae77047
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectiondependencies-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectiondependencies-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectiondependencies-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 26fd15c5-7eda-833f-5e20-cef61725b146
---

# SMS_CollectionDependencies Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionDependencies` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, is used to query dependency relationships between collections, specifically the composable collection rules (inclusion, exclusion) and the limiting collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionDependencies : SMS_BaseClass
{
      String DependentCollectionID;
      UInt32 RelationshipType;
      String SourceCollectionID;
};
```

## Methods

The `SMS_CollectionDependencies` class does not define any methods.

## Properties

`DependentCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The unique id of the dependent collection.

`RelationshipType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key, enumeration]

Dependency relationship, how the dependent collection uses the source.

| Value | Relationship type |
| --- | --- |
| 1 | LIMITING |
| 2 | INCLUDE |
| 3 | EXCLUDE |

`SourceCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

The unique id of the source collection.

## Remarks

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).