---
layout: Conceptual
title: SMS_PackageToContent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class
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
description: The SMS_PackageToContent WMI class is an SMS Provider server class, in Configuration Manager, that relates a Configuration Manager package to its content.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e125b355-34cb-39c7-e59c-8ed4d74f7f44
document_version_independent_id: b25bea6a-fde5-4cdb-c600-913af29dc57e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6c22e060-27db-a83d-0041-ae9b462573a0
---

# SMS_PackageToContent Class - Configuration Manager | Microsoft Learn

The `SMS_PackageToContent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that relates a Configuration Manager package to its content.

## Syntax

```
Class SMS_PackageToContent : SMS_BaseClass
{
      SInt32 ContentID;
      String ContentSubFolder;
      String ContentUniqueID;
      SInt32 ContentVersionInPkg;
      SInt32 MinPackageVersion;
      String PackageID;
      UInt32 PackageType;
      UInt32 SecuredTypeID;
      String SecureObjectID;
};
```

## Methods

The following table lists the methods in `SMS_PackageToContent`.

| Method | Description |
| --- | --- |
| [IsContentValid Method in Class SMS_PackageToContent](iscontentvalid-method-in-class-sms_packagetocontent) | Determines if the package content is valid. |

## Properties

`ContentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, Not\_null]

The value of the `ContentID` property of the package.

`ContentSubFolder` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

The name of the subfolder in the package source folder that contains the files for the content.

`ContentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, Not\_null]

The unique ID for the content.

`ContentVersionInPkg` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [Not\_null]

The version of the content in the package.

`MinPackageVersion` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [Not\_null]

The minimum package version in which the content appears.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Configuration Manager-specific ID of the package.

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

The type of the package. Possible values are:

| Value | Description |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |

`SecuredTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Secured type of related package.

`SecureObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Secure object ID. For app, it is model name. For others, it is package ID.

## Remarks

Class qualifiers for this class include:

- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Your application can query this class to get the list of contents contained by a package or the list of packages that contain specified content.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).