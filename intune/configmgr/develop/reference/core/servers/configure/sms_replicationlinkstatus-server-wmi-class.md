---
layout: Conceptual
title: SMS_ReplicationLinkStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinkstatus-server-wmi-class
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
description: Learn how to represent the database link status between the child and parent site for each replication group with SMS_ReplicationLinkStatus.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 92dad64d-8a9d-c6d6-9b5c-59b2ab851d8d
document_version_independent_id: 490e789c-c1a3-95fe-a221-8439b6b6d906
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinkstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_replicationlinkstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinkstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9b2cdc25-669b-d215-c6e7-a26d13e38174
---

# SMS_ReplicationLinkStatus Class - Configuration Manager | Microsoft Learn

The `SMS_ReplicationLinkStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents the database link status between the child and parent site for each replication group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ReplicationLinkStatus : SMS_BaseClass
{
    DateTime ChildLastReceived;
    DateTime ChildLastSent;
    String ChildSite;
    UInt32 DegradedSyncs;
    UInt32 FailedSyncs;
    UInt32 InitializationPercent;
    UInt32 InitializationStatus;
    DateTime ParentLastReceived;
    DateTime ParentLastSent;
    String ParentSite;
    UInt32 RecoveryStatus;
    String ReplicationGroup;
    String ReplicationPattern;
    UInt32 SyncInterval;
};
```

## Methods

The `SMS_ReplicationLinkStatus` class doesn't define any methods.

## Properties

`ChildLastReceived` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time of last received message for this replication group on the child site.

`ChildLastSent` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

The time of last message for this replication group sent from the child site.

`ChildSite` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Site code of the child site.

`DegradedSyncs` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

If the link status is degraded, this will show the synchronization intervals from the last synchronization finish time.

`FailedSyncs` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

If the link status is failed, this will show the synchronization intervals from last synchronization finish time.

`InitializationPercent` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Reinitialization progress for this replication group.

`InitializationStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Reinitialization status.

`ParentLastReceived` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time of the last received message for this replication group on the parent site.

`ParentLastSent` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time of the last message for this replication group sent from the parent site.

`ParentSite` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Site code of the parent site.

`RecoveryStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Recovery status.

`ReplicationGroup` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Name of the replication group. See [SMS_ReplicationGroup Server WMI Class](sms_replicationgroup-server-wmi-class).

`ReplicationPattern` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Replication pattern. See [SMS_ReplicationGroup Server WMI Class](sms_replicationgroup-server-wmi-class).

`SyncInterval` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Synchronization interval, in minutes, for the replication group.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).