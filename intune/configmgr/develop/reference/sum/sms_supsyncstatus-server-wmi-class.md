---
layout: Conceptual
title: SMS_SUPSyncStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_supsyncstatus-server-wmi-class
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
description: Learn how to use the SMS_SUPSyncStatus class in Configuration Manager to list sync and replication status for SUM data for participating site/SUP.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b7cdf1c6-fc12-201d-1231-adf3bbe25d07
document_version_independent_id: b24a78b9-397f-896c-2be5-f0e4c4f24e3a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_supsyncstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_supsyncstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_supsyncstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2624a017-7337-44fa-9494-a407bb0e59fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a438284e-c3c3-4c36-ab0b-aa7c244b912c
platformId: a3f1fde9-233d-e2fe-1fea-0a189acd0fac
---

# SMS_SUPSyncStatus Class - Configuration Manager | Microsoft Learn

The `SMS_SUPSyncStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists sync and replication status for SUM data for participating site/SUP.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SUPSyncStatus : SMS_BaseClass  
{  
    DateTime LastReplicationLinkCheckTime;  
    DateTime LastSuccessfulSyncTime;  
    UInt32 LastSyncErrorCode;  
    UInt32 LastSyncState;  
    DateTime LastSyncStateTime;  
    UInt32 ReplicationLinkStatus;  
    String SiteCode;  
    UInt32 SyncCatalogVersion;  
    String WSUSServerName;  
    String WSUSSourceServer;  
};  
```

## Methods

The `SMS_SUPSyncStatus` class does not define any methods.

## Properties

`LastReplicationLinkCheckTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time the replication link status was checked.

`LastSuccessfulSyncTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last synchronization success time.

`LastSyncErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Last synchronization error code.

`LastSyncState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Last synchronization state. Possible values are:

| Value | Status |
| --- | --- |
| 6702 | WSUS Synchronization done (Success) |
| 6703 | WSUS Synchronization failed |
| 6704 | WSUS Synchronization in progress. Current phase: Synchronizing WSUS Server |
| 6705 | WSUS Synchronization in progress. Current phase: Synchronizing site database |
| 6706 | WSUS Synchronization in progress. Current phase: Synchronizing Internet facing WSUS Server |
| 6707 | Content of WSUS server is out of sync with upstream server |
| 6708 | WSUS synchronization complete, with pending license terms downloads |

`LastSyncStateTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time the synchronization state was reported.

`ReplicationLinkStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Replication link status.

| Value | Status |
| --- | --- |
| 0 | Healthy |
| 1 | Degraded |
| 2 | Error |

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

Site code.

`SyncCatalogVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Synchronization catalog version.

`WSUSServerName` Data type: `String`

Access type: Read-only

Qualifiers: [key, not\_null, read]

WSUS server name.

`WSUSSourceServer` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

WSUS source server.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).