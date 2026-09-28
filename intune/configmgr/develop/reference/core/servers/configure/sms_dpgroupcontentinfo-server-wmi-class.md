---
layout: Conceptual
title: SMS_DPGroupContentInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcontentinfo-server-wmi-class
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
description: An SMS Provider server class that describes package information for a given distribution point group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 00d5c07d-92da-7c1f-f8f4-bb0447d8a5af
document_version_independent_id: d7a545ff-135e-41b6-e861-6d6a15ef1088
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcontentinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_dpgroupcontentinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcontentinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bc5c2406-0da7-01e1-b3f0-64b9231d1d3f
---

# SMS_DPGroupContentInfo Class - Configuration Manager | Microsoft Learn

The `SMS_DPGroupContentInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes package information for a given distribution point group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupContentInfo : SMS_BaseClass
{
    String Description;
    String GroupID;
    Boolean IsPredefinedPackage;
    String Name;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 SourceSize;
};
```

## Methods

The `SMS_DPGroupContentInfo` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for the package or application.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique identifier for the distribution point group.

`IsPredefinedPackage` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`True` if this package is a predefined package.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The identifier of the package or the unique identifier of the configuration item.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

Object type.

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

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Secured object class ID.

| Value | Object type |
| --- | --- |
| Value | Description |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier for the package.

`SourceSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Source size of the package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).