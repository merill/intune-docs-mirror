---
layout: Conceptual
title: SMS_SoftwareShortcut Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwareshortcut-client-wmi-class
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
description: In Configuration Manager, the SMS_SoftwareShortcut class is a client Windows Management Instrumentation class that defines a shortcut to executable files or a shortcut in a common system location.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ac7fab1e-45c0-f6b9-a6df-0f1f38241c7f
document_version_independent_id: c8d2646c-0d45-b297-8cde-c040a75ab5ee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_softwareshortcut-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_softwareshortcut-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_softwareshortcut-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c887a37-39a4-4ffc-b882-71f35819ccf6
---

# SMS_SoftwareShortcut Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareShortcut` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that defines a shortcut to executable files or a shortcut in a common system location.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareShortcut
{
      String BinFileVersion;
      String BinProductVersion;
      String Description;
      String FilePropertiesHash;
      String FilePropertiesHashEx;
      UInt32 FileSize;
      String FileVersion;
      UInt32 Language;
      String ParentName;
      String Product;
      String ProductCode;
      String ProductVersion;
      String Publisher;
      String ShortcutKey;
      String ShortcutName;
      UInt32 ShortcutType;
      String TargetExecutable;
};
```

## Methods

The `SMS_SoftwareShortcut` class does not define any methods.

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

File description that can be presented to users, for example, "Microsoft Word for Windows".

`FilePropertiesHash` Data type: `String`

Access type: Read-only

Qualifiers: None

A unique 128-bit signature that is derived from a combination of the `Product`, `Description`, `ProductVersion`, `Publisher`, and `FileNam`e properties of the file.

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

`Language` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Language associated with the file, for example, "1033".

`ParentName` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the shortcut container, for example, "Start Menu", "Quick Launch", or "Desktop".

`Product` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the product with which the file is distributed, for example, "Microsoft Windows".

`ProductCode` Data type: `String`

Access type: Read-only

Qualifiers: None

GUID that is the principal identifier for an application or product. For more information, see the Microsoft Windows Installer documentation.

`ProductVersion` Data type: `String`

Access type: Read-only

Qualifiers: None

The version of the product with which the file is distributed, for example, "4.2.0.2623".

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: None

The company that produced the file, for example, "Microsoft Corporation" or "Standard Microsystems Corporation, Inc.".

`ShortcutKey` Data type: `String`

Access type: Read-only

Qualifiers: Key

Key for the shortcut, without the full path.

`ShortcutName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the shortcut, without the full path.

`ShortcutType` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

The type of shortcut. Possible values are:

| Value | Shortcut type |
| --- | --- |
| 1 | Shortcut to Folder |
| 2 | Shortcut to File (EXE or DLL) |
| 3 | Application Reference (.appref-ms) |

`TargetExecutable` Data type: `String`

Access type: Read-only

Qualifiers: None

The name of the executable file that is linked to the shortcut.

## Remarks

Note

This class is not currently used to support existing Asset Intelligence reports. However, it can be enabled to support custom reports.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).