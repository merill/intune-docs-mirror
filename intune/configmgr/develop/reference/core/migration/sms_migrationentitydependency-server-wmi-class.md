---
layout: Conceptual
title: SMS_MigrationEntityDependency Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationentitydependency-server-wmi-class
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
description: In Configuration Manager, the SMS_MigrationEntityDependency Windows Management Instrumentation class is an SMS Provider server class that represents the dependency relationship between objects in the Configuration Manager 2007 hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 25c3c6d3-873a-97d5-fb57-c79d38ea14b9
document_version_independent_id: 26c22393-7186-ebb2-b6bc-97d7da305eca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationentitydependency-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationentitydependency-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationentitydependency-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c4d95fce-9629-1499-235c-92e5a2a24f3e
---

# SMS_MigrationEntityDependency Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationEntityDependency` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the dependency relationship between objects in the Configuration Manager 2007 hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationEntityDependency : SMS_BaseClass
{
    UInt32 Dependant;
    UInt32 DependencyType;
    UInt32 EntityID;
};
```

## Methods

The `SMS_MigrationEntityDependency` class does not define any methods.

## Properties

`Dependant` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Dependent entity identifier.

`DependencyType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Entity dependency type.

`EntityID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Entity ID.

## Remarks

The dependency tree is flattened for performance, which means, if A depends on B, and B depends on C, by querying this class, you can get an instance representing A depends on C. By referring to this class, you can guarantee the data integrity when creating a migration job.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).