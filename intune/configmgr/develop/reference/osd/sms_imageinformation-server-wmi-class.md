---
layout: Conceptual
title: SMS_ImageInformation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageinformation-server-wmi-class
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
description: Learn how to represent all image information in boot image, operating system image, and operating system installer using SMS_ImageInformation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c18ceef9-d492-685c-a800-d5d4a755e0d2
document_version_independent_id: 07f97f2f-d898-8808-e63c-605afa726638
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_imageinformation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_imageinformation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_imageinformation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 4828879d-d60d-59be-4649-b86a0bf9fe42
---

# SMS_ImageInformation Class - Configuration Manager | Microsoft Learn

The `SMS_ImageInformation` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents all image information in boot image, operating system image, and operating system installer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageInformation : SMS_BaseClass
{
    String Architecture;
    String CreatedBy;
    String CreationDate;
    String Description;
    Boolean EnableLabShell;
    String HALType;
    String ImagePath;
    String ImageOSVersion;
    UInt32 Index;
    String Language;
    String Name;
    UInt32 ObjectType;
    String OSVersion;
    String PackageID;
    UInt32 PackageType;
    String ProductType;
    SInt64 Size;
    String Version;
};
```

## Methods

The `SMS_ImageInformation` class does not define any methods.

## Properties

`Architecture` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Architecture of the boot image.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who created the image.

`CreationDate` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Date and time when the image was created.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the image.

`EnableLabShell` Data type: `Boolean`

Access type: Read-only

Qualifiers: [lazy]

`true` if command-line support is enabled. The default value is `false`.

`HALType` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Image HAL type.

`ImagePath` Data type: `String`

Access type: Read-only

Qualifiers: [read]

For internal use only.

`ImageOSVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The operating system version for the default image in the boot WIM file.

`Index` Data type: `UInt32`

Access type: Read-only

Qualifiers: [lazy, read]

A one-based number indicating which image in the source WIM file is the boot image.

The default value is 1.

`Language` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Language of the image.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the image.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object type.

| Value | Object type |
| --- | --- |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |

`OSVersion` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Image operating system version.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

A unique, auto-generated key that is used to relate programs, advertisements, and distribution points to the package.

`PackageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Image package type.

| Value | Package type |
| --- | --- |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |

`ProductType` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Image product type.

`Size` Data type: `SInt64`

Access type: Read-only

Qualifiers: [read]

Image size.

`Version` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_PackageBaseclass Server WMI Class](../core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).