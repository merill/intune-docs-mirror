---
layout: Conceptual
title: SMS_PDF_Program Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class
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
description: The SMS_PDF_Program WMI class is an SMS Provider server class that represents a package definition file (PDF) template from which to create an initialized program.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ec5584b7-103a-78e4-7ac2-988c16f94146
document_version_independent_id: 02d918e5-6182-687c-4d50-e238f9d19827
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1f68fa78-1f91-42e5-c685-a8ae5e4cf4f8
---

# SMS_PDF_Program Class - Configuration Manager | Microsoft Learn

The `SMS_PDF_Program` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a package definition file (PDF) template from which to create an initialized program.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PDF_Program : SMS_BaseClass
{
      String CommandLine;
      String Comment;
      String DependentProgram;
      String Description;
      String DiskSpaceReq;
      String DriveLetter;
      UInt32 Duration;
      UInt8 Icon[];
      UInt32 IconSize;
      UInt32 PDFID;
      UInt32 ProgramFlags;
      String ProgramName;
      String Publisher;
      String Requirements;
      String WorkingDirectory;
};
```

## Methods

The `SMS_PDF_Program` class doesn't define any methods.

## Properties

`CommandLine` Data type: `String`

Access type: Read/Write

Qualifiers: None

Command that executes when the program is launched.

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the program displayed in the Configuration Manager console.

`DependentProgram` Data type: `String`

Access type: Read/Write

Qualifiers: None

A formatted text string defining any program that should be run prior to executing the current program. The format is defined as: &lt;PackageID&gt;;; &lt;ProgramName&gt;. The default value is "".

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the program (not displayed in the Configuration Manager console).

`DiskSpaceReq` Data type: `String`

Access type: Read/Write

Qualifiers: None

Approximate disk space that the program requires.

`DriveLetter` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("1"), Range("a-z")]

Drive letter (one character in the range from a to z) that the program maps to and runs from. The default value is "".

`Duration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Approximate duration, in minutes, that the program takes to execute.

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [lazy, large]

Icon to associate with the program in the Configuration Manager console.

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

Size, in bytes, of the icon. The default value is 0.

`PDFID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the [SMS_PDF_Package Server WMI Class](sms_pdf_package-server-wmi-class) object to which the program belongs.

`ProgramFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flags defining the installation characteristics of the program. See the `ProgramFlags` property of [SMS_Program Server WMI Class](sms_program-server-wmi-class).

`ProgramName` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name that uniquely identifies the program.

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

Manufacturer of the program.

`Requirements` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of any extra requirements of the program. The default value is "".

`WorkingDirectory` Data type: `String`

Access type: Read/Write

Qualifiers: None

The location from which the program executes. This can be an absolute path on the client or a path relative to the distribution point folder that contains the package. The default value is "".

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    Your application can't delete individual programs from the package definition file store. To delete a program, the application must delete the package template and then reload the package template without the program.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).