---
layout: Conceptual
title: SMS_ReplicationGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_replicationgroup-server-wmi-class
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
description: Learn how to classify replication group data in Configuration Manager using SMS_ReplicationGroup WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 61cb5b03-cb19-b4f1-b9e7-6a87a27b9426
document_version_independent_id: 9ec9e0fd-b438-67ef-4a0f-868354641817
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_replicationgroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_replicationgroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_replicationgroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: f36f6770-956f-7ca3-5dc3-731b04458dd2
---

# SMS_ReplicationGroup Class - Configuration Manager | Microsoft Learn

The `SMS_ReplicationGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains replication group data.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ReplicationGroup : SMS_BaseClass
{
    UInt32 ID;
    Boolean IsPush;
    String ReplicationGroup;
    String ReplicationPattern;
    UInt16 ReplicationPriority;
    String SecurityKey;
    UInt32 Status;
    UInt32 SyncInterval;
    String TransportType;
};
```

## Methods

The following table lists the methods in the `SMS_ReplicationGroup` class.

| Method | Description |
| --- | --- |
| [InitializeData Method in Class SMS_ReplicationGroup](initializedata-method-in-class-sms_replicationgroup) | Reinitializes the data in a specific replication group between two specified sites. |

## Properties

`ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Unique identifier for the replication group.

`IsPush` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this is site data. `false` if this is global data.

`ReplicationGroup` Data type: `String`

Access type: Read-only

Qualifiers: none

Name of the replication group used in the data replication service. Each replication group contains a set of tables to be replicated together.

`ReplicationPattern` Data type: `String`

Access type: Read-only

Qualifiers: none

Replication pattern. Possible values are:

| Value | Replication pattern |
| --- | --- |
| Global | The data is replicated across all primary sites and CAS in the hierarchy. |
| Site | The data is replicated up to the CAS in the hierarchy. |
| Global\_proxy | The data is replicated to secondary sites in the hierarchy. |

`ReplicationPriority` Data type: `UInt16`

Access type: Read-only

Qualifiers: none

Priority of data replication using data replication service.

`SecurityKey` Data type: `String`

Access type: Read-only

Qualifiers: none

Security key value for RBAC to verify that the SDK user has permission to read the instance of `SMS_ReplicationGroup`.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The current status of replicating data for tables in the replication group.

`SyncInterval` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

How often the data replication service checks to see if there are any changes in the tables within the replication group to be replicated.

`TransportType` Data type: `String`

Access type: Read-only

Qualifiers: none

Type of transportation supported by data replication service.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).