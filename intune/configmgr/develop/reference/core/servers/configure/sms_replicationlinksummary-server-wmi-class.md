---
layout: Conceptual
title: SMS_ReplicationLinkSummary Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinksummary-server-wmi-class
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
description: Learn how to use the SMS_ReplicationLinkSummary class to represent summaries of database replication link statuses.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bab16ba8-5ef6-353d-48ad-14c06036f036
document_version_independent_id: 959214ad-9789-da1e-8830-27d0bdbfb949
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinksummary-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_replicationlinksummary-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_replicationlinksummary-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: acd5474e-0147-b142-f6f2-90aa851c1ebe
---

# SMS_ReplicationLinkSummary Class - Configuration Manager | Microsoft Learn

The `SMS_ReplicationLinkSummary` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the summary of database replication link status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ReplicationLinkSummary : SMS_BaseClass
{
    String GlobalInitPercentage;
    UInt32 LinkStatus;
    UInt32 LinkStatusDescription;
    String Site1;
    UInt32 Site1Status;
    UInt32 Site1ToSite2GlobalState;
    DateTime Site1ToSite2GlobalSyncTime;
    String Site2;
    UInt32 Site2Status;
    UInt32 Site2ToSite1GlobalState;
    DateTime Site2ToSite1GlobalSyncTime;
    UInt32 Site2ToSite1SiteState;
    DateTime Site2ToSite1SiteSyncTime;
    String SiteName1;
    String SiteName2;
    UInt32 SiteType1;
    UInt32 SiteType2;
};
```

## Methods

The `SMS_ReplicationLinkSummary` class does not define any methods.

## Properties

`GlobalInitPercentage` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Progress of the re-initialization of the global data.

`LinkStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Overall link status.

`LinkStatusDescription` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Overall link status.

`Site1` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Parent site for the link.

`Site1Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Site status for the parent site. See [SMS_Site Server WMI Class](sms_site-server-wmi-class).

`Site1ToSite2GlobalState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Overall link status for global data sent from the parent site to the child site.

`Site1ToSite2GlobalSyncTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time that the parent site sent a message to the child site for global data synchronization.

`Site2` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Child site.

`Site2Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Site status for the child site. See [SMS_Site Server WMI Class](sms_site-server-wmi-class).

`Site2ToSite1GlobalState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Overall link status for global data sent from the child site to the parent site.

`Site2ToSite1GlobalSyncTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time that the child site sent a message to the parent site for global data synchronization.

`Site2ToSite1SiteState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Overall link status for site data send from the child site to the parent site.

`Site2ToSite1SiteSyncTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last time that the child site sent a message to the parent site for data synchronization.

`SiteName1` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the parent site.

`SiteName2` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the child site.

`SiteType1` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Type of the parent site. Possible values are:

| Value | Parent site type |
| --- | --- |
| 1 | SECONDARY |
| 2 | PRIMARY |
| 4 | CAS |

`SiteType2` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Type of the child site. Possible values are:

| Value | Child site type |
| --- | --- |
| 1 | SECONDARY |
| 2 | PRIMARY |
| 4 | CAS |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).