---
layout: Conceptual
title: SMS_ObjectContentInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontentinfo-server-wmi-class
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
description: Learn how to use the SMS_ObjectContentInfo class in Configuration Manager to set application or package content information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7a510ca3-398f-9773-2d83-3ea6a4d4c0ca
document_version_independent_id: 63b691be-67ce-d749-21e8-3eef4f1d6f16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/sms_objectcontentinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/sms_objectcontentinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/sms_objectcontentinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: a0d8382e-38c8-2727-7519-390288f46d68
---

# SMS_ObjectContentInfo Class - Configuration Manager | Microsoft Learn

The `SMS_ObjectContentInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents Application or Package Content Information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectContentInfo : SMS_BaseClass
{
    DateTime DateCreated;
    String Description;
    UInt32 FeatureType;
    DateTime LastUpdateDate;
    UInt32 NumberErrors;
    UInt32 NumberInProgress;
    UInt32 NumberSuccess;
    UInt32 NumberUnknown;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    String SoftwareName;
    String SourceSite;
    UInt32 SourceSize;
    UInt32 SourceVersion;
    UInt32 Targeted;
};
```

## Methods

The `SMS_ObjectContentInfo` class does not define any methods.

## Properties

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Package creation time.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description for the package or application.

`FeatureType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Feature ID property for monitoring. The default value is 8.

`LastUpdateDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Package last updated time.

`NumberErrors` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of failed distribution point.

`NumberInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of pending distribution point.

`NumberSuccess` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of distribution point which was successfully deployed.

`NumberUnknown` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of distribution point with unknown state.

`ObjectID` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

PackageID or ModelName.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Object type. Possible values are listed below.

| Value | Object type |
| --- | --- |
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

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object class ID. Possible values are listed below.

| Value | Object type ID |
| --- | --- |
| 2 | SMS\_Package |
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

Package ID.

`SoftwareName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the package or application.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The source site.

`SourceSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Package source size.

`SourceVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Package source version.

`Targeted` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of targeted distribution point.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).