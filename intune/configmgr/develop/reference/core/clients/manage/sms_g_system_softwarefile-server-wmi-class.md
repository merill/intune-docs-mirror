---
layout: Conceptual
title: SMS_G_System_SoftwareFile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class
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
description: The SMS_G_System_SoftwareFile class is an SMS Provider server class that contains information about all software files that were inventoried on the client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 89d6fadb-a1b4-e990-c857-53b31fc3bea9
document_version_independent_id: 7ad5c273-5c4d-cfcc-766e-6cbbfda6783e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 303c9181-6fa6-00fa-38ef-f568ec2a6b92
---

# SMS_G_System_SoftwareFile Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_SoftwareFile` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains information about all software files that were inventoried on the client computer.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_SoftwareFile : SMS_G_System
{
     DateTime CreationDate;
     UInt32 FileCount;
     String FileDescription;
     SInt64 FileID;
     String FileName;
     String FilePath;
     SInt64 FileSize;
     String FileVersion;
     DateTime ModifiedDate;
     DateTime FileModifiedDate;
     UInt32 ProductId;
     UInt32 ResourceID;
};
```

## Methods

The `SMS_G_System_SoftwareFile` class doesn't define any methods.

## Properties

`CreationDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

Deprecated. The value is always `null`.

`FileCount` Data type: **UInt32**

Access type: Read/Write

Qualifiers: v

Value indicating the file count. This value is always 1 because Configuration Manager tracks individual file paths.

`FileDescription` Data type: **String**

Access type: Read/Write

Qualifiers: None

Description from the description resource string. This value is blank for unknown files.

`FileID` Data type: **SInt64**

Access type: Read/Write

Qualifiers: [key]

Configuration Manager-supplied ID that uniquely identifies the file.

`FileName` Data type: **String**

Access type: Read/Write

Qualifiers:

[DefaultOrder("ASC")]

Name of the file.

`FilePath` Data type: **String**

Access type: Read/Write

Qualifiers: None

Path to the software file location on the client computer.

`FileSize` Data type: **SInt64**

Access type: Read/Write

Qualifiers: None

Size of the file, in bytes.

`FileVersion` Data type: **String**

Access type: Read/Write

Qualifiers: None

Version from the version resource string. This value is blank for unknown files.

`ModifiedDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

The date and time when the record in the database was last modified.

`FileModifiedDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

The date and time when the file was last modified.

`ProductId` Data type: **UInt32**

Access type: Read/Write

Qualifiers: None

Value that associates the software file with a software product represented by an [SMS_G_System_SoftwareProduct Server WMI Class](sms_g_system_softwareproduct-server-wmi-class) object. A value of 0 indicates that the software file isn't associated with a known software product, that is, it's an unknown file. Files with a `ProductId` value is 0 are identical to [SMS_G_System_UnknownFile Server WMI Class](sms_g_system_unknownfile-server-wmi-class) objects.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key, ResID(6301), ResDLL("SMS\_RXPL.dll")]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

This class represents both known product files and unknown product files. Known product files contain company and product resource information or are related to known product files. Although you can use this class for queries involving inventoried files, it's preferred to use [SMS_ProductFileInfo Server WMI Class](../../../apps/sms_productfileinfo-server-wmi-class).

Although [SMS_G_System_UnknownFile Server WMI Class](sms_g_system_unknownfile-server-wmi-class) defines the same unknown file information that is found in this class, there's no advantage to querying against `SMS_G_System_UnknownFile` for unknown product files. The following query returns all unknown product files from `SMS_G_System_SoftwareFile`.

```
SELECT * FROM SMS_G_System_SoftwareFile
WHERE ProductId = 0
```

The following query returns all known product files and their product information.

```
SELECT * FROM SMS_G_System_SoftwareFile swf
JOIN SMS_G_System_SoftwareProduct swp ON swf.ProductId = swp.ProductId
AND swf.ResourceID = swp.ResourceID
```

The Software Inventory Agent collects files identified in the site control file. To identify the files to collect, the agent:

1. Queries the site control [SMS_SCI_ClientComp Server WMI Class](../../servers/configure/sms_sci_clientcomp-server-wmi-class) objects for items having the value "Software Inventory Agent" for the `ClientComponentName` property.
2. Loops through the embedded property list. When the value for `PropertyName` is "Inventoriable Types", the agent updates the comma-delimited list of file names (including extensions) in the `Value2` property. When the value for `PropertyName` is "Inventory Schedule", the agent updates the interval string in the `Value2` property. For information about creating an interval string, see the example for the [WriteToString Method in Class SMS_ScheduleMethods](../../servers/configure/writetostring-method-in-class-sms_schedulemethods) method. When the value for `PropertyName` is "Report Options", the agent updates the reporting options value in the `Value` property, specifying at least one reporting option for the software inventory to be collected. The following table lists the reporting options.

    | Reporting option | Description |
    | --- | --- |
    | Product version information. Bit 0. | Inventories products that contain company and product resource information. |
    | Files associated with known products. Bit 1. | Inventories files associated with products that contain company and product resource information. For example, Wwintl32.dll is inventoried because it's associated with Microsoft Word. Set this bit only if the product version information reporting option is selected. |
    | Files not associated with known products. Bit 2. | Inventories files that don't include company and product resource information (unknown files). |
3. For newly added inventory types, adds entries to the following `Path`, `Subdirectories`, and `Exclude` embedded property lists.
4. Updates the site control file. For more information, see [About the site control file](../../../../core/understand/about-the-configuration-manager-site-control-file).

Note

Collecting inventory information for some files, for example, DLL files, can generate a large volume of network traffic and substantially increase the size of the Configuration Manager database. For this reason, test any changes you make in a test environment before implementing them in a production environment.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).