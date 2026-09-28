---
layout: Conceptual
title: SMS_DPGroupCollections Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcollections-server-wmi-class
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
description: An SMS Provider server class that describes collection association for a given distribution point group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d1e1bbc7-f683-51df-7129-9982448954ba
document_version_independent_id: 81f1b809-d979-9365-9ea2-3a4d0adf0a30
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcollections-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpgroupcollections-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcollections-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4946bc19-b9ca-6707-f4ce-ed1d036af6b7
---

# SMS_DPGroupCollections Class - Configuration Manager | Microsoft Learn

The `SMS_DPGroupCollections` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes collection association for a given distribution point group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupCollections : SMS_BaseClass
{
    String CollectionDescription;
    String CollectionID;
    UInt32 CollectionMemberCount;
    String CollectionName;
    String GroupDescription;
    String GroupID;
    String GroupName;
};
```

## Methods

The `SMS_DPGroupCollections` class does not define any methods.

## Properties

`CollectionDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the collection.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Collection associated with the distribution point group.

`CollectionMemberCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the collection members.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection.

`GroupDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the distribution point group.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier for the distribution point group.

`GroupName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the distribution point group.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).