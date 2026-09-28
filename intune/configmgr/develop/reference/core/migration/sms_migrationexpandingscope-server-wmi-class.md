---
layout: Conceptual
title: SMS_MigrationExpandingScope Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationexpandingscope-server-wmi-class
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
description: The SMS_MigrationExpandingScope class represents collections that have the expanding scope problem when migrated to System Center 2012 Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf501ccd-5900-bc10-606d-6f0daac4678f
document_version_independent_id: 7a0e58c8-086a-e201-4f23-39cc77e4a1d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationexpandingscope-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationexpandingscope-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationexpandingscope-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 59c80140-facc-fd89-9342-bfb82a3a3bf1
---

# SMS_MigrationExpandingScope Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationExpandingScope` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the collections that have the problem of expanding scope when migrated to System Center 2012 Configuration Manager.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationExpandingScope : SMS_BaseClass
{
    UInt32 CollectionEntityID;
    String CollectionEntityName;
    String CollectionWMIObjectPath;
    UInt32 TargetingEntityID;
    String TargetingEntityName;
    String TargetingWMIObjectPath;
};
```

## Methods

The `SMS_MigrationExpandingScope` class does not define any methods.

## Properties

`CollectionEntityID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Unique identifier for the collection.

`CollectionEntityName` Data type: `String`

Access type: Read-only

Qualifiers: none

The collection entity display name.

`CollectionWMIObjectPath` Data type: `String`

Access type: Read-only

Qualifiers: none

The collection entity WMI path.

`TargetingEntityID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Unique identifier for the targeting entity.

`TargetingEntityName` Data type: `String`

Access type: Read-only

Qualifiers: none

The targeting entity display name.

`TargetingWMIObjectPath` Data type: `String`

Access type: Read-only

Qualifiers: none

The targeting entity WMI path.

## Remarks

When you create a migration job, consider whether to specify a new limit to the collection to restrict the scope for each of such collections.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).