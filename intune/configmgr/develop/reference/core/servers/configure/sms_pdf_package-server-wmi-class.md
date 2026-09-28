---
layout: Conceptual
title: SMS_PDF_Package Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class
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
description: In Configuration Manager, the SMS_PDF_Package Windows Management Instrumentation class is an SMS Provider server class that represents a package definition file template from which to create an initialized package.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4413095f-44a0-eddd-4531-57a28486fbdb
document_version_independent_id: 14ba92e1-5d10-45ca-f60e-84f925d649f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 9796dd89-20e7-0cec-6630-6094f569140c
---

# SMS_PDF_Package Class - Configuration Manager | Microsoft Learn

The `SMS_PDF_Package` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a package definition file (PDF) template from which to create an initialized package.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PDF_Package : SMS_BaseClass
{
      UInt8 Icon[];
      UInt32 IconSize;
      String Language;
      String Name;
      String PDFFileName;
      UInt32 PDFID;
      String Publisher;
    String RequiredIconNames[];
      UInt32 Status;
      String Version;
};
```

## Methods

The following table lists the methods in the `SMS_PDF_Package` class.

| Method | Description |
| --- | --- |
| [GetPDFData Method in Class SMS_PDF_Package](getpdfdata-method-in-class-sms_pdf_package) | Gets `SMS_Package` and `SMS_Program` objects for a loaded package definition file. |
| [LoadIconForPDF Method in Class SMS_PDF_Package](loadiconforpdf-method-in-class-sms_pdf_package) | Imports a required icon for a package definition file. |
| [LoadPDF Method in Class SMS_PDF_Package](loadpdf-method-in-class-sms_pdf_package) | Imports a package definition file into the package definition file store. |
| [ProcessInBox Method in Class SMS_PDF_Package](processinbox-method-in-class-sms_pdf_package) | Imports package definition files from the package definition file inbox. |

## Properties

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [lazy, large]

Icon to associate with the package in the Configuration Manager console.

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

Size, in bytes, of the icon. The default value is 0.

`Language` Data type: `String`

Access type: Read/Write

Qualifiers: None

Language for the package, for example, English.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the package.

`PDFFileName` Data type: `String`

Access type: Read/Write

Qualifiers: [SizeLimit("100")]

File name of the package definition file. The file name does not include the .sms file name extension.

`PDFID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique auto-generated ID for the package definition file.

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

Manufacturer of the package.

`RequiredIconNames` Data type: `String` Array

Access type: Read/Write

Qualifiers: [lazy]

Icons still required to be loaded.

`Status` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy, Enumeration]

Load status of the package definition file. Possible values are:

| Value | Load status |
| --- | --- |
| 0 | Loaded |
| 1 | RequiresIcon |

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version number of the package.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

    This class contains methods that store the package definition file template in the package definition file store and that produce [SMS_Package Server WMI Class](sms_package-server-wmi-class) objects and [SMS_Program Server WMI Class](sms_program-server-wmi-class) objects from the template.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).