---
layout: Conceptual
title: SMS_TaskSequence_PartitionSettings Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_partitionsettings-server-wmi-class
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
description: The SMS_TaskSequence_PartitionSettings WMI class is an SMS Provider server class, in Configuration Manager, that specifies the settings to use when creating and formatting a partition on a hard drive.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3ddfeb39-0642-b9f9-cbb1-7ee74691f66b
document_version_independent_id: d15ceda9-d350-74b5-6485-2ce6d0efeb20
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_partitionsettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_partitionsettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_partitionsettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c3c123bf-cf3d-ac3c-4a53-8affb938f5e9
---

# SMS_TaskSequence_PartitionSettings Class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_PartitionSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies the settings to use when creating and formatting a partition on a hard disk drive.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_PartitionSettings
{
      Boolean AssignVolumeLetter;
      Boolean Bootable;
      String FileSystem;
      Boolean QuickFormat;
      UInt32 Size;
      String SizeUnits;
      String Type;
      String VolumeLetterVariable;
      String VolumeName;
};
```

## Methods

The `SMS_TaskSequence_PartitionSettings` class does not define any methods.

## Properties

`AssignVolumeLetter` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if a volume letter will be assigned to the partition. The default value is `true`.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`Bootable` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to set the partition as the active partition. The default value is `false`.

`FileSystem` Data type: `String`

Access type: Read/Write

Qualifiers: None

File system to use when formatting the partition. Possible values are:

- FAT32
- NTFS

    `QuickFormat` Data type: `Boolean`

    Access type: Read/Write

    Qualifiers: [not\_null]

    `true` to perform a quick format. Set this property to `false` to perform a full format.

    `Size` Data type: `UInt32`

    Access type: Read/Write

    Qualifiers: None

    Size of the partition to create. The units are defined by the `SizeUnits` property.

    `SizeUnits` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Units in which the `Size` property is specified. Possible values are:

| Value | Size units |
| --- | --- |
| MB | Megabytes |
| GB | Gigabytes |
| Percent | Percentage of free space remaining on disk |

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Type of partition to create. Possible values are:

- Primary
- Extended
- Logical
- Hidden
- EFI
- MSR

    `VolumeLetterVariable` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Name of a task sequence variable that receives the drive letter of the newly created partition.

    `VolumeName` Data type: `String`

    Access type: Read/Write

    Qualifiers: None

    Name to assign to the volume when it is formatted.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).