---
layout: Conceptual
title: SMS_AdvertisementInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisementinfo-server-wmi-class
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
description: Learn how to use the SMS_AdvertisementInfo class in Configuration Manager to provide information about a specific advertisement.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 47a15355-beda-21f0-1175-f04d2cdb3f6a
document_version_independent_id: 353a9ecb-d03c-c18c-2487-05e322a74889
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_advertisementinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_advertisementinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_advertisementinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: dc7c8faf-2b79-3f6d-8c21-f518cfdfaa58
---

# SMS_AdvertisementInfo Class - Configuration Manager | Microsoft Learn

The `SMS_AdvertisementInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides information about a specific advertisement.

## Syntax

```
Class SMS_AdvertisementInfo : SMS_BaseClass
{
      UInt32 AdvertFlags;
      String AdvertisementID;
      String AdvertisementName;
      String AdvertisementSourceSite;
      UInt32 AssignmentID;
      String CollectionID;
      String CollectionName;
      DateTime ExpirationTime;
      UInt32 OfferType;
      String PackageID;
      String PackageLanguage;
      String PackageManufacturer;
      String PackageName;
      UInt32 PackageType;
      String PackageVersion;
      DateTime PresentTime;
      UInt32 ProgramFlags;
      String ProgramName;
      UInt32 TimeFlags;
};
```

## Methods

The `SMS_AdvertisementInfo` class does not define any methods.

## Properties

`AdvertFlags` Data type: `UInt32`

Access type: Read Only

Qualifiers: [bits]

Flags identifying the advertisement. Possible values are defined for the `AdvertFlags` property of [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class). The default value is 0.

`AdvertisementID` Data type: `String`

Access type: Read Only

Qualifiers: [key]

A unique auto-generated key.

`AdvertisementName` Data type: `String`

Access type: Read Only

Qualifiers: [Not\_null]

A plain text name of the advertisement.

`AdvertisementSourceSite` Data type: `String`

Access type: Read Only

Qualifiers: [read]

The three-letter site code of the site from which the advertisement originated.

`AssignmentID` Data type: `UInt32`

Access type: Read Only

Qualifiers: [read]

ID for the assignment associated with the advertisement.

`CollectionID` Data type: `String`

Access type: Read Only

Qualifiers: [Not\_null]

The ID that refers to the collection to which the specified advertisement will advertise.

`CollectionName` Data type: `String`

Access type: Read Only

Qualifiers: [Not\_null]

The name of the collection to which the advertisement is advertising.

`ExpirationTime` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

The date and time when the advertisement will no longer be available to clients.

`OfferType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of advertisement.

| Value | Advertisement type |
| --- | --- |
| 0 | Required Advertisement. |
| 2 | Available advertisement. |

`PackageID` Data type: `String`

Access type: Read Only

Qualifiers: [Not\_null]

The ID that refers to the package the advertisement will advertise.

`PackageLanguage` Data type: `String`

Access type: Read Only

Qualifiers: None

The language of the advertised package.

`PackageManufacturer` Data type: `String`

Access type: Read Only

Qualifiers: None

The manufacturer of the advertised package.

`PackageName` Data type: `String`

Access type: Read Only

Qualifiers: None

The name of the advertised package.

`PackageType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

[enumeration]

The type of the package. Possible values are:

| Value | Description |
| --- | --- |
| 0 | Regular software distribution package. |
| 3 | Driver package. |
| 4 | Task sequence package. |
| 5 | Software update package. |
| 6 | Device setting package. |
| 257 | Image package. |
| 258 | Boot image package. |
| 259 | Operating system install package. |

`PackageVersion` Data type: `String`

Access type: Read Only

Qualifiers: None

The version of the advertised package.

`PresentTime` Data type: `DateTime`

Access type: Read Only

Qualifiers: None

The date and time when the advertisement will be presented to clients.

`ProgramFlags` Data type: `UInt32`

Access type: Read Only

Qualifiers: [bits]

ProgramFlags define the installation characteristics of the program, such as whether this is an unattended install, the install restarts the computer, or the install runs in a minimized window. The default flags are USERCONTEXT, USEUNCPATH, and ANY\_PLATFORM.

When using SMS\_Program programmatically, ensure that no conflicting options are selected. For example, NOUSERLOGGEDIN and USERCONTEXT should not be used together.

Note

Unlisted bits are either obsolete or unused by SMS.

Possible values are:

| Hexadecimal (Bit) | Description |
| --- | --- |
| 0x00000001 (0) | Program is authorized for dynamic install |
| 0x00000002 (1) | Task sequence show custom progress user interface message |
| 0x00000010 (4) | This is a default program |
| 0x00000020 (5) | Disables MOM alerts while the program runs. Requires SMS 2003 SP1 |
| 0x00000040 (6) | Generates MOM alert if the program fails. Requires SMS 2003 SP1. |
| 0x00000080 (7) | For Advanced Client only. If set, this program's immediate dependent should always be run. |
| 0x00000100 (8) | Indicates a device program. If set, the program is not offered to desktop clients. |
| 0x00000200 (9) | This program's immediate dependent should always be run. |
| 0x00000400 (10) | The countdown dialog is not displayed. |
| 0x00000800 (11) | The command requires Add Remove Programs to be restarted—for example, APASetup.exe. |
| 0x00001000 (12) | The program is disabled. |
| 0x00002000 (13) | The program requires no user interaction. |
| 0x00004000 (14) | The program needs to run in the user context. |
| 0x00008000 (15) | The program must be run as the local Administrator account. |
| 0x00010000 (16) | The program must be run by every user for whom it is valid. Valid only for mandatory jobs. |
| 0x00020000 (17) | The program is run only when no user is logged on. |
| 0x00040000 (18) | Exit application for programs which restart the computer. |
| 0x00080000 (19) | Configuration Manager restarts the computer when the program has finished running. |
| 0x00100000 (20) | Use a UNC path (no drive letter) to access the distribution point. |
| 0x00200000 (21) | Persists the connection to the drive specified in the DriveLetter property. The USEUNCPATH bit flag must not be set. |
| 0x00400000 (22) | Run the program as a minimized window. |
| 0x00800000 (23) | Run the program as a maximized window. |
| 0x01000000 (24) | Hide the program window. |
| 0x02000000 (25) | Logoff user when program completes successfully. |
| 0x04000000 (26) | Use administrator defined account to run program. |
| x08000000 (27) | Override check for platform support. |
| 0x20000000 (29) | Run uninstall from the registry key when the advertisement expires. |
| 0x40000000 (30) | The platform is not supported. |
| 0x80000000 (31) | Display in Add Remove Programs. |

`ProgramName` Data type: `String`

Access type: Read Only

Qualifiers: [Not\_null]

The program name of the program related to the package that the advertisement will advertise.

`TimeFlags` Data type: `UInt32`

Access type: Read Only

Qualifiers: [read, bits]

Flags that duplicate the information in the time-related properties. Possible values are defined for the `TimeFlags` property of [SMS_Advertisement Server WMI Class](sms_advertisement-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (Read Only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).