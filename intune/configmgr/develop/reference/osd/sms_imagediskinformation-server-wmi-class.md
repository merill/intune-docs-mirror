---
layout: Conceptual
title: SMS_ImageDiskInformation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagediskinformation-server-wmi-class
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
description: The SMS_ImageDiskInformation WMI class is an SMS Provider server class, in Configuration Manager, that represents all disks and partition information in an operating system image and installer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: de4fa019-7c67-54e8-dbc5-be082cd7a3a0
document_version_independent_id: cb2a803c-dde0-8575-7be4-ef95a48a08f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_imagediskinformation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_imagediskinformation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_imagediskinformation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e6e93f29-4b2b-b7de-066c-66a8efd4c3f0
---

# SMS_ImageDiskInformation Class - Configuration Manager | Microsoft Learn

The `SMS_ImageDiskInformation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents all disks and partition information in an operating system image and operating system installer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageDiskInformation : SMS_BaseClass
{
    UInt32 DiskIndex;
    String DiskStyle;
    String PackageID;
    String PartitionFileSystem;
    UInt32 PartitionIndex;
    Boolean PartitionIsBoot;
    String PartitionLabel;
    SInt64 PartitionOffset;
    SInt64 PartitionSize;
    String PartitionStyle;
    String PartitionType;
};
```

## Methods

The `SMS_ImageDiskInformation` class does not define any methods.

## Properties

`DiskIndex` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Disk Index of this image.

`DiskStyle` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Disk style.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

ID of the image package.

`PartitionFileSystem` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Partition file system.

`PartitionIndex` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Partition index of this image.

`PartitionIsBoot` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Whether the partition is the boot partition.

`PartitionLabel` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Partition label.

`PartitionOffset` Data type: `SInt64`

Access type: Read-only

Qualifiers: [read]

Partition offset.

`PartitionSize` Data type: `SInt64`

Access type: Read-only

Qualifiers: [read]

Partition size.

`PartitionStyle` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Partition style.

`PartitionType` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Partition type.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).