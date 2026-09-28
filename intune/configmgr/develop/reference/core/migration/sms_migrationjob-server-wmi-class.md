---
layout: Conceptual
title: SMS_MigrationJob Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationjob-server-wmi-class
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
description: The SMS_MigrationJob WMI class is an SMS Provider server class that represents a migration job.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 806a69a7-c5d2-9d0c-6bc7-26397ced82e3
document_version_independent_id: ab99c8d1-93df-4789-5079-cf884fc66d4e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationjob-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationjob-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationjob-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2d50c600-3984-17d2-47ee-63f18ce6093b
---

# SMS_MigrationJob Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationJob` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a migration job.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationJob : SMS_BaseClass
{
    String AdditionalConfiguration;
    String CreatedBy;
    String CustomBootImagePackage_x64;
    String CustomBootImagePackage_x86;
    DateTime DateCreated;
    DateTime DateEnded;
    DateTime DateLastUpdated;
    DateTime DateNextRun;
    DateTime DateStarted;
    String Description;
    String DestinationSiteCode;
    String DestinationSiteFQDN;
    Boolean DisableAdvertisements;
    UInt32 FailedObjectNumber;
    UInt32 JobID;
    String JobName;
    UInt32 MigratedObjectNumber;
    Boolean MigrateWithFolders;
    String ModifiedBy;
    UInt32 ResolveObjectConflictOption;
    String ScheduleToken;
    String ScopeIDs[];
    UInt32 SkippedObjectNumber;
    String SourceCollectionIDs[];
    UInt32 SourceObjectIDs[];
    String SourceSiteCode;
    String SourceSiteFQDN;
    UInt32 SourceSiteID;
    UInt32 Status;
    UInt32 TotalObjectNumber;
    UInt32 Type;
};
```

## Methods

The following table lists the methods in the `SMS_MigrationJob` class.

| Method | Description |
| --- | --- |
| [Start Method in Class SMS_MigrationJob](start-method-in-class-sms_migrationjob) | Starts the migration job. |
| [Stop Method in Class SMS_MigrationJob](stop-method-in-class-sms_migrationjob) | Stops the migration job. |

## Properties

`AdditionalConfiguration` Data type: `String`

Access type: Read/Write

Qualifiers: none

Additional configuration for migration jobs.

For a collection migration job, the configuration contains the collections information included in this job. The format is like:

```
<MigrationJob>
   <Collection ID="JQX00011" Type="2" LimitTo="SMS00019" />
   <Collection ID="JQX00012" Type="2" />
   <Collection ID="JQX00018" Type="2" />
   <SiteCodeMap Old="JQX" New="CAR" />
   <SiteCodeMap Old="P5P" New="PE1" />
   </Collection>
</MigrationJob>
```

For a distribution point upgrade job, the configuration contains the settings to upgrade a shared distribution point. The format is like:

```
<DPUpgrade>
  <SourceSiteCode>CEN</SourceSiteCode>
  <SiteCode>CAS</SiteCode>
  <NALPath>...</NALPath>
  ...
  <SiteSystem>
    <NALPath>...</NALPath>
    ...
    <EmbeddedProperties>
      <EmbeddedProperty>
        <PropertyName>IsProtected</PropertyName>
        <Value>0</Value>
        <Value1 />
        <Value2 />
      </EmbeddedProperty>
      ...
    </EmbeddedProperties>
  </SiteSystem>
  <DistributionPoint>
  ...
  </DistributionPoint>
</DPUpgrade>
```

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who created this job.

`CustomBootImagePackage_x64` Data type: `String`

Access type: Read/Write

Qualifiers: none

PackageID of a boot image package to use for x64 boot images in place of the default.

`CustomBootImagePackage_x86` Data type: `String`

Access type: Read/Write

Qualifiers: none

PackageID of a boot image package to use for x86 boot images in place of the default.

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time that the job was created.

`DateEnded` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time that the job ended.

`DateLastUpdated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time that the job was last updated.

`DateNextRun` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time that the job will run next.

`DateStarted` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Time that the job started.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the job.

`DestinationSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Destination site code.

`DestinationSiteFQDN` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Destination site FQDN.

`DisableAdvertisements` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if migrated advertisements will be disabled.

`FailedObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of failed objects.

`JobID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifier of the job.

`JobName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the job.

`MigratedObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of migrated objects.

`MigrateWithFolders` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the folder structure should be migrated along with the objects.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who most recently modified this job.

`ResolveObjectConflictOption` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Resolve object conflict option.

`ScheduleToken` Data type: `String`

Access type: Read/Write

Qualifiers: none

Schedule token, writable only with the manage migration Job right..

`ScopeIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: [lazy]

Scope IDs that migrated entities should be in.

`SkippedObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of skipped objects.

`SourceCollectionIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: [lazy]

Source collection IDs selected for migration.

`SourceObjectIDs` Data type: `UInt32 Array`

Access type: Read/Write

Qualifiers: [lazy]

Source object IDs included in the job.

`SourceSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site code.

`SourceSiteFQDN` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Source site FQDN.

`SourceSiteID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Source site ID.

`Status` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Job status. Possible values are:

| Value | Job status |
| --- | --- |
| 0 | NotStarted |
| 1 | Completed |
| 2 | Running |
| 3 | Failed |
| 4 | Stopped |

`TotalObjectNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of objects.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of job. Possible values are:

| Value | Job type |
| --- | --- |
| 1 | Object |
| 2 | Client |
| 3 | ObjectandClient |

## Remarks

Migration jobs are the object used by the server components to perform a migration task. There are three types of migration jobs: 1) collection migration job, 2) object migration job and 3) distribution point upgrade job. Job types are defined using the `Type` property.

Collection migration jobs include the collections and collection related information such as the limiting collection, the source site code and the destination site code. Object migration jobs can include objects such as packages, but cannot include the collections and the targeting objects such as advertisements. Distribution point upgrade jobs can upgrade a shared distribution point to a Configuration Manager regular distribution point.

For collection migration jobs and object migration jobs, the included objects' entity ID is stored as an array of properties on the job, SourceCollectionIDs and SourceObjectIDs. For distribution point upgrade jobs, the settings for the new site system and distribution point are stored as XML in the property `AdditionalConfiguration`. All job types are scheduled by using the `ScheduleToken` property.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).