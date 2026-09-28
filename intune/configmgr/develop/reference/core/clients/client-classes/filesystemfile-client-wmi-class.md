---
layout: Conceptual
title: FileSystemFile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/filesystemfile-client-wmi-class
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
description: Learn how to use the FileSystemFile Class to represent local file information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8dc4006b-649e-5b64-e166-d0ca33411b9e
document_version_independent_id: b9bb42b8-d0ae-78db-d159-de5780577568
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/filesystemfile-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/filesystemfile-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/filesystemfile-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 0a9bb388-f902-e7d3-e600-a752f29d7f0f
---

# FileSystemFile Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `FileSystemFile` class is a client Windows Management Instrumentation (WMI) class that represents local file information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class FileSystemFile
{
      String AgentCreatedWMIPath;
      String CompanyName;
      DateTime CreationDate;
      DateTime FileBuildDate;
      String FileDescription;
      UInt32 FileFunctionType;
      UInt32 FileGeneralType;
      String FileInternalName;
      String FileOriginalName;
      UInt32 FileOSFlags;
      String FileVersion;
      UInt32 FileVersionFlags;
      Boolean IsArchived;
      Boolean IsCompressed;
      Boolean IsEncrypted;
      Boolean IsHidden;
      Boolean IsNormal;
      Boolean IsOffline;
      Boolean IsReadOnly;
      Boolean IsReparsePoint;
      Boolean IsSparseFile;
      Boolean IsSystem;
      Boolean IsTemporary;
      DateTime LastAccessDate;
      DateTime LastWriteDate;
      String Name;
      String Path;
      UInt32 ProductLanguage;
      String ProductName;
      String ProductVersion;
      UInt32 ReservedFlags0;
      UInt32 ReservedFlags1;
      String ShortName;
      UInt64 Size;
      UInt32 Type;
};
```

## Methods

The `FileSystemFile` class does not define any methods.

## Properties

`AgentCreatedWMIPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

The WMI path created by the agent.

`CompanyName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Company name stored in the file resource header.

`CreationDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Time the file was created according to the operating system.

`FileBuildDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Time stamp, from the file resource header, of the files creation.

`FileDescription` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

File description stored in the file resource header.

`FileFunctionType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Function type of the file, dependent on the general type (such as DRV + PRINTER). For more information, see VS\_FIXEDFILEINFO in the Platform SDK.

`FileGeneralType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

General type of the file (such as APP, DLL, and DRV). For more information, see VS\_FIXEDFILEINFOin the Platform SDK.

`FileInternalName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Internal file name stored in the file resource header.

`FileOriginalName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Original file name stored in the file resource header.

`FileOSFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Bitmask with the operating system values that the file was designed for (such as Windows NT and WIN32). For more information, see VS\_FIXEDFILEINFO in the Platform SDK.

`FileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

File version stored in the files resource header.

`FileVersionFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Bitmask specifying various version attributes of the file (such as DEBUG, PATCHED, and PRIVATE). For more information, see VS\_FIXEDFILEINFO in the Platform SDK.

`IsArchived` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file archive bit is set.

`IsCompressed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file is compressed.

`IsEncrypted` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file is encrypted.

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file is hidden.

`IsNormal` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if no other file attributes are set.

`IsOffline` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file data is not immediately available.

`IsReadOnly` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file is read-only. An application cannot write to or delete the file.

`IsReparsePoint` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file has an associated reparse point.

`IsSparseFile` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`True` if the file is a sparse file.

`IsSystem` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`True` if the file is a system file.

`IsTemporary` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the file is being used for temporary storage.

`LastAccessDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Time, according to the operating system, when the file was last accessed.

`LastWriteDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Time when the file was last written to, according to the operating system.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the file, with wildcards that are supported in the query (such as drv\*.sys). This string is the long file name (if different from the 8.3 representation).

`Path` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

File path, not including the file name. The provider supports limited wildcards and directory vs. single directory scan syntax for querying based on this property. The provider also supports path queries with unexpanded environment variables, such as %*windir*%.

`ProductLanguage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Product language stored in the file resource header.

`ProductName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Product name stored in the file resource header.

`ProductVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Product version stored in the file resource header.

`ReservedFlags0` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Provided for completeness. For more information, see WIN32\_FIND\_DATA.

`ReservedFlags1` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Provided for completeness. For more information, see WIN32\_FIND\_DATA.

`ShortName` Data type: `String`

Access type: Read/Write

Qualifiers: None

8.3 representation of the file name.

`Size` Data type: `UInt64`

Access type: Read/Write

Qualifiers: [key]

File size, in bytes (a 64-bit value).

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

File attribute bitmask, which matches the attribute bitmask returned by the Win32 `GetFileAttributes` function. The individual bits are also broken out into separate Boolean values for ease of querying and filtering.

## Remarks

This class is used primarily for software inventory, file collection, and IDMIF collection.

To convert properties of this class to their WIN32\_FIND\_DATA equivalent, consult the WMI SDK.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).