---
layout: Conceptual
title: SMS_DistributionPointDriveInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointdriveinfo-server-wmi-class
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
description: The SMS_DistributionPointDriveInfo WMI class is an SMS Provider server class that represents the basic information about the drives on a distribution point site system role.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0fe55c0a-0f45-acc2-10fc-62800160217e
document_version_independent_id: 3edea56d-1f1c-48e6-d762-f76bc70df84c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointdriveinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_distributionpointdriveinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointdriveinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 51103595-16e0-ddd5-54ca-b599454f1c6b
---

# SMS_DistributionPointDriveInfo Class - Configuration Manager | Microsoft Learn

The `SMS_DistributionPointDriveInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the basic information about the drives on a distribution point site system role.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionPointDriveInfo : SMS_BaseClass
{
    SInt64 BytesFree;
    SInt64 BytesTotal;
    SInt32 ConttentLibPriority;
    String Drive;
    String NALPath;
    SInt32 ObjectType;
    SInt32 PercentFree;
    SInt32 PkgSharePriority;
    String SiteCode;
    SInt32 Status;
};
```

## Methods

The `SMS_DistributionPointDriveInfo` class does not define any methods.

## Properties

`BytesFree` Data type: `SInt64`

Access type: Read/Write

Qualifiers: none

Amount of free, unused storage space, in kilobytes, for the storage object.

`BytesTotal` Data type: `SInt64`

Access type: Read/Write

Qualifiers: none

Maximum amount of storage space, in kilobytes, of the storage object. A negative value indicates that information is currently unavailable.

`ConttentLibPriority` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The order of preference for distributing content to this drive when copying packages to the Configuration Manager content library on the distribution point system. Lower values are preferred over higher values.

`Drive` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Drive that is used by the distribution point.

`NALPath` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Network abstraction layer (NAL) path to the distribution point.

`ObjectType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Object type. Possible values are:

| Value | Object type |
| --- | --- |
| Value | Description |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`PercentFree` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Percentage of free storage space available on the storage object.

`PkgSharePriority` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The order of preference for distributing packages to this drive when coping packages to package share location. Lower values are preferred over higher values.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Site code of the role.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The last returned error code from attempts to copy content to this drive. A status of 0 indicates success.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).