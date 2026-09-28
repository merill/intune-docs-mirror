---
layout: Conceptual
title: SMS_MigrationDP Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationdp-server-wmi-class
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
description: The SMS_MigrationDP WMI class is an SMS Provider server class that represents the shared distribution points between the current active Configuration Manager 2007 hierarchy and the System Center 2012 Configuration Manager hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 94ec0780-ffb4-6849-83e8-39c0f568eb30
document_version_independent_id: fcda85f0-660b-1d43-1f90-9488799e7fdb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationdp-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationdp-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationdp-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 37518c07-a762-9d51-7965-4ad7dfaabb33
---

# SMS_MigrationDP Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationDP` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the shared distribution points between the current active Configuration Manager 2007 hierarchy and the System Center 2012 Configuration Manager hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationDP : SMS_DistributionPointInfoBase
{
    Boolean AdditionalRoleInstalled;
    Boolean AddressScheduleEnabled;
    String AttachingSite;
    String AttachingSitecode;
    String BindExcept;
    Boolean BindPolicy;
    Boolean BitsEnabled;
    Boolean CertificateType;
    UInt32 Communication;
    String Description;
    UInt32 DPFlags;
    String Drive;
    Boolean EligibleForUpgrade;
    UInt32 GroupCount;
    Boolean HasRelationship;
    Boolean HealthCheckEnabled;
    UInt32 HealthCheckPriority;
    String HealthCheckSchedule;
    UInt32 HostedPackageNum;
    UInt32 ID;
    String IdentityGUID;
    Boolean InternetFacing;
    Boolean IsActive;
    Boolean IsMulticast;
    Boolean IsPeerDP;
    Boolean IsPullDP;
    Boolean IsProtected;
    Boolean IsPXE;
    UInt32 MBytesFree;
    UInt32 MBytesPackageSize;
    String NALPath;
    String Name;
    String OperatingSystem;
    String OSVersion;
    Boolean PreStagingAllowed;
    UInt32 Priority;
    String PXEPassword;
    Boolean RateLimitsEnabled;
    String ResourceType;
    UInt32 ResponseDelay;
    String ServerName;
    String ShareName;
    String SiteCode;
    String SiteName;
    Boolean SupportUnknownMachines;
    UInt32 TransferRate;
    UInt32 UdaSetting;
};
```

## Methods

The `SMS_MigrationDP` class does not define any methods.

## Properties

`AdditionalRoleInstalled` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if there is any additional site role installed.

`AddressScheduleEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if a schedule on an address is configured.

`AttachingSite` Data type: `String`

Access type: Read-only

Qualifiers: none

The site server name of the source primary site that this distribution point is reporting to in the source hierarchy.

`AttachingSitecode` Data type: `String`

Access type: Read-only

Qualifiers: none

The site code of the source primary site that this distribution point is reporting to in the source hierarchy.

`BindExcept` Data type: `String`

Access type: Read-only

Qualifiers: none

PXE Bind Exception.

`BindPolicy` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if PXE bind policy exists.

`BitsEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if BITS is enabled on the distribution point.

`CertificateType` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

PXE certificate type.

`Communication` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

HTTP or HTTPS.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the distribution point.

`DPFlags` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Distribution point flags.

| Value | Distribution point flags |
| --- | --- |
| 0 | DP\_TYPE\_READONLY |

`Drive` Data type: `String`

Access type: Read-only

Qualifiers: none

The default drive.

`EligibleForUpgrade` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the distribution point is eligible for upgrade.

`GroupCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

The number of distribution point groups that contain this distribution point.

`HasRelationship` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this distribution point is assigned to a distribution point group.

`HealthCheckEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if health check on this distribution point is enabled.

`HealthCheckPriority` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Distribution point health manager thread priority.

`HealthCheckSchedule` Data type: `String`

Access type: Read-only

Qualifiers: none

Schedule for health check.

`HostedPackageNum` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Total number of packages stored on the distribution point.

`ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Distribution point id in the database.

`IdentityGUID` Data type: `String`

Access type: Read-only

Qualifiers: none

Identity GUID.

`InternetFacing` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this distribution point is internet facing.

`IsActive` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if PXE is active.

`IsMulticast` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this distribution point is multicast enabled.

`IsPeerDP` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this distribution point is a branch distribution point.

`IsProtected` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this distribution point is protected.

`IsPullDP` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the distribution point is a pull distribution point. The default value is `false`.

`IsPXE` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

PXE is enabled.

`MBytesFree` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Total MBytes of free space.

`MBytesPackageSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Total Mbytes of packages distributed on this distribution point.

`NALPath` Data type: `String`

Access type: Read-only

Qualifiers: [key, key]

Distribution point NALPath.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Network operating system path.

`OperatingSystem` Data type: `String`

Access type: Read-only

Qualifiers: none

Operating system of this computer.

`OSVersion` Data type: `String`

Access type: Read-only

Qualifiers: none

The operating system of the branch distribution point. An empty string means the operating system is undetected.

`PreStagingAllowed` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if this distribution point is allowed to pre-stage contents.

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Distribution priority. The default value is 1.

`PXEPassword` Data type: `String`

Access type: Read-only

Qualifiers: none

PXE password.

`RateLimitsEnabled` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if rate limits are configured.

`ResourceType` Data type: `String`

Access type: Read-only

Qualifiers: none

See [SMS_CollectionMember Server WMI Class](../clients/collections/sms_collectionmember-server-wmi-class).

`ResponseDelay` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

PXE response delay.

`ServerName` Data type: `String`

Access type: Read-only

Qualifiers: none

Distribution point server name.

`ShareName` Data type: `String`

Access type: Read-only

Qualifiers: none

Distribution point share name.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [sizelimit]

The site code that this distribution point is reporting to in the destination hierarchy.

`SiteName` Data type: `String`

Access type: Read-only

Qualifiers: none

The site name.

`SupportUnknownMachines` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if PXE supports unknown computers.

`TransferRate` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The average transfer rate in Kbps. The default value is 0.

`UdaSetting` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

PXE UDA setting.

## Remarks

To get the distribution points of a specific source primary site shared, set the `EnabledDPSharing` property of `SMS_MigrationSiteMapping` to true. The instance of this class carries the properties of the distribution point in the source hierarchy, so it can be used to create the distribution point upgrade job to upgrade the shared distribution point to a regular distribution point.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).