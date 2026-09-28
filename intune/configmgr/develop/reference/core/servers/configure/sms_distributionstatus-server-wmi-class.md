---
layout: Conceptual
title: SMS_DistributionStatus Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionstatus-server-wmi-class
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
description: The SMS_DistributionStatus WMI class is an SMS Provider server class, in Configuration Manager, that represents the status of a package that has been assigned to a distribution point.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dbd77a87-7d30-c110-c84c-c9ea44b1b3b5
document_version_independent_id: 67457801-bea3-67a1-8eb5-198aeba7b592
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_distributionstatus-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_distributionstatus-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_distributionstatus-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bc389936-1e09-4638-b76c-bcd7e670aa5c
---

# SMS_DistributionStatus Class - Configuration Manager | Microsoft Learn

The `SMS_DistributionStatus` Windows Management Instrumentation (WMI) class is an SMS Provider server class in Configuration Manager that represents the status of a package that has been assigned to a distribution point.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionStatus : SMS_BaseClass
{
    UInt32 Assets;
    DateTime LastUpdateDate;
    UInt32 MessageCategory;
    String ObjectID;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 Type;
};
```

## Methods

The `SMS_DistributionStatus` class doesn't define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Number of distribution points in this status.

`LastUpdateDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Last status update date.

`MessageCategory` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Status message category.

`ObjectID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

PackageID or ModelName.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object class ID.

| Value | Object type |
| --- | --- |
| 2 | SMS\_DistributionStatus |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 21 | SMS\_DeviceSettingPackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

PackageID.

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Status Type.

| Value | Status type |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).