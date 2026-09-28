---
layout: Conceptual
title: SMS_MigrationSiteMapping class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationsitemapping-server-wmi-class
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
description: The technical details of the SMS_MigrationSiteMapping server WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8d9b9d10-0c38-ca80-fa9e-c12b3bf2b3e7
document_version_independent_id: ab7b65d0-fb44-fa5b-f611-9119114c356a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationsitemapping-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationsitemapping-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationsitemapping-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: a4f814c3-5f45-3dd4-31a3-76ea982917d5
---

# SMS_MigrationSiteMapping class - Configuration Manager | Microsoft Learn

The `SMS_MigrationSiteMapping` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents a mapping between the Configuration Manager source site and the Configuration Manager top site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationSiteMapping : SMS_BaseClass
{
    String Account;
    String AccountForSql;
    String ContentDestination;
    DateTime DateLastBegin;
    DateTime DateLastSynced;
    DateTime DateLastUpdated;
    DateTime DateNextRun;
    String DestinationSiteCode;
    String DestinationSiteFQDN;
    Boolean EnableDPSharing;
    Boolean IsCentral;
    Boolean IsDecommissioned;
    Boolean IsDeleted;
    UInt32 JobIDs[];
    UInt32 MigratedClientNumber;
    UInt32 MigratedObjectNumber;
    String ModifiedBy;
    String ParentSiteCode;
    String ParentSiteServer;
    String ScheduleToken;
    UInt32 SiteMappingID;
    String SourceSiteCode;
    String SourceSiteFQDN;
    UInt32 Status;
    UInt32 SyncedEntities[];
    UInt32 TotalClientNumber;
    UInt32 TotalObjectNumber;
};
```

## Methods

The following table lists the methods in the `SMS_MigrationSiteMapping` class.

| Method | Description |
| --- | --- |
| [ActivateHierarchy Method in Class SMS_MigrationSiteMapping](activatehierarchy-method-in-class-sms_migrationsitemapping) | Activates the hierarchy. |
| [CleanupHierarchyData Method in Class SMS_MigrationSiteMapping](cleanuphierarchydata-method-in-class-sms_migrationsitemapping) | Cleans up hierarchy data. |
| [CheckDecommissionState Method in Class SMS_MigrationSiteMapping](checkdecommissionstate-method-in-class-sms_migrationsitemapping) | Checks to see if site mapping can be decommissioned. |
| [Decommission Method in Class SMS_MigrationSiteMapping](decommission-method-in-class-sms_migrationsitemapping) | Decommissions site mapping. |
| [Resuscitate Method in Class SMS_MigrationSiteMapping](resuscitate-method-in-class-sms_migrationsitemapping) | Resuscitates site mapping. |
| [Sync Method in Class SMS_MigrationSiteMapping](sync-method-in-class-sms_migrationsitemapping) | Synchronizes the entities on the source site. |

## Properties

`Account` Data type: `String`

Access type: Read/Write

Qualifiers: none

SDK Account used for migration.

`AccountForSql` Data type: `String`

Access type: Read/Write

Qualifiers: none

SQL Server account used for migration.

`ContentDestination` Data type: `String`

Access type: Read/Write

Qualifiers: none

The destination of the content of the packages from this site..

`DateLastBegin` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last begin time.

`DateLastSynced` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last sync time.

`DateLastUpdated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Updated time.

`DateNextRun` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Next run time.

`DestinationSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Destination site code.

`DestinationSiteFQDN` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Destination site FQDN.

`EnableDPSharing` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if it should gather distribution point information.

`IsCentral` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the source site is a central site.

`IsDecommissioned` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the site has stopped gathering data.

`IsDeleted` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the site mapping has been deleted.

`JobIDs` Data type: `UInt32 Array`

Access type: Read-only

Qualifiers: [lazy, read]

Jobs associated with this site mapping.

`MigratedClientNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total number of migrated clients.

`MigratedObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total number of migrated objects.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Modified by.

`ParentSiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Parent site code for source site.

`ParentSiteServer` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Parent site server for source site.

`ScheduleToken` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule token for the site mapping synchronization.

`SiteMappingID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Primary site mapping ID.

`SourceSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site code.

`SourceSiteFQDN` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site FQDN.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Site mapping synchronization status.

| Value | Site mapping status |
| --- | --- |
| 0 | Have not gathered data |
| 1 | Ready for next data gathering process |
| 2 | Gathering data |
| 3 | Failed |
| 4 | Stopped |
| 258 | Gathering hierarchy data |
| 259 | Failed (Unauthorized Access) |
| 514 | Gathering object data |
| 515 | Failed (Network Timeout) |
| 770 | Gathering client data |
| 771 | Failed (No Permission to Source Site WMI) |
| 1026 | Gathering package status data |
| 1027 | Failed (SQL Error) |
| 1283 | Failed (Child Primary Site) |
| 1539 | Failed (Same Hierarchy) |
| 1795 | Failed (Unsupported Site Version) |
| 2051 | Failed (No Permission to fnSCCMMultiByteToWideChar) |
| 2307 | Failed (Duplicated site code with current hierarchy) |
| 4099 | Failed (Duplicated site code with another source hierarchy) |

`SyncedEntities` Data type: `UInt32 Array`

Access type: Read-only

Qualifiers: [lazy, read]

Entities synchronized from this site mapping.

`TotalClientNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total number of clients.

`TotalObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Total number of objects.

## Remarks

Once a source site is configured for data gathering, it should appear as an instance of this class. This instance controls many aspects of the data gathering, such as the schedule, whether distribution point sharing is enabled, and so on. It also has some monitoring data such as status, the total object number and the total client number.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).