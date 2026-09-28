---
layout: Conceptual
title: SMS_InstalledExecutable Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedexecutable-client-wmi-class
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
description: The SMS_InstalledExecutable class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that identifies executable files associated with a software installation.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 027ce101-c7b6-30a5-7496-6559a658d7fe
document_version_independent_id: fdd17edd-bdb4-9c5b-ce66-5c032bebb69f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_installedexecutable-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_installedexecutable-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_installedexecutable-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a0a2551e-64ab-e413-3524-c8a78d7e84e7
---

# SMS_InstalledExecutable Class - Configuration Manager | Microsoft Learn

The `SMS_InstalledExecutable` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that identifies executable files associated with a software installation.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InstalledExecutable
{
      String BinFileVersion;
      String BinProductVersion;
      String Description;
      String ExecutableName;
      String FilePropertiesHash;
      String FilePropertiesHashEx;
      UInt32 FileSize;
      String FileVersion;
      Boolean HasPatchAdded;
      String InstalledFilePath;
      Boolean IsSystemFile;
      Boolean IsVitalFile;
      UInt32 Language;
      String Product;
      String ProductCode;
      String ProductVersion;
      String Publisher;
};
```

## Methods

The `SMS_InstalledExecutable` class does not define any methods.

## Properties

`BinFileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`BinProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

Reserved. For internal use.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: None

File description that can be presented to users, for example, "Keyboard driver for AT-style keyboards" or "Microsoft Word for Windows".

`ExecutableName` Data type: `String`

Access type: Read-only

Qualifiers: [key]

Name of the file, including the extension but excluding the path, for example, "Notepad.exe".

`FilePropertiesHash` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, and `FileName` properties of the file.

`FilePropertiesHashEx` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, `FileName`, `FileVersion`, `BinProductVersion`, and `BinFileVersion` properties of the file.

`FileSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Size of the file, in bytes.

`FileVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the file, for example, "12.0.4518.1014".

`HasPatchAdded` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the file was added as part of an update to the product to which it belongs.

`InstalledFilePath` Data type: `String`

Access type: Read-only

Qualifiers: None

The path where the file is located, for example, "C:\Program Files\Microsoft Office".

`IsSystemFile` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the file is a system file.

`IsVitalFile` Data type: `Boolean`

Access type: Read-only

Qualifiers: None

`true` if the file is vital for the accurate operation of the product to which it belongs.

`Language` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

ID of the language for which the file is intended, for example, "1033".

`Product` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the product with which the file is distributed, for example, "Microsoft Windows".

`ProductCode` Data type: `String`

Access type: Read-only

Qualifiers: [key]

GUID that is the principal identifier for an application or product. For more information, see the Microsoft Windows Installer documentation.

`ProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the product with which the file is distributed, for example, "4.2.0.2623".

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: None

The company that produced the file, for example, "Microsoft Corporation" or "Standard Microsystems Corporation, Inc.".

## Remarks

Note

This class is not currently used to support existing Asset Intelligence reports. However, it can be enabled to support custom reports.

This class identifies executable files associated with a software installation to:

- Confirm that the application is installed by looking at Configuration Manager file inventory.
- Indicate what metering rules, based on the executable files, have to be set to meter the application.
- Perform an application impact analysis.

    Because the Windows Installer (.msi) file contains a record of the installed executable files, it can be used as the source for the mapping between installed applications and executable files.

    This class retrieves data from two sources. For each [SMS_InstalledSoftware Client WMI Class](sms_installedsoftware-client-wmi-class) object, the class identifies the .msi package by looking in the `LocalPackage` property, and queries the .msi database for all .exe and .com files.

    For any [SMS_InstalledSoftware Client WMI Class](sms_installedsoftware-client-wmi-class) object that has the `LocalPackage` property set to `null`, the `SMS_InstalledExecutable` class inventories all executable files in the directory that are identified by the `InstallLocation` property. Executable files that are installed outside of the main installation directory are not inventoried.

Note

This class does not inventory executable files located in the %*windir*% and %*systemroot*% directories.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).