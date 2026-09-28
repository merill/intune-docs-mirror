---
layout: Conceptual
title: SMS_G_System_UnknownFile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_unknownfile-server-wmi-class
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
description: An SMS Provider server class that represents an unknown software file, that is, a file that doesn't contain product resource information or isn't related to a software product that contains product resource information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1433310f-cfc4-206a-18b0-6b3b8092296c
document_version_independent_id: 653e9fde-4842-3f8a-666b-f9f47a7c0c74
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_unknownfile-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_unknownfile-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_unknownfile-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 4d68afa7-f3f3-cd82-3769-884606ce5400
---

# SMS_G_System_UnknownFile Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_UnknownFile` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an unknown software file, that is, a file that doesn't contain product resource information or isn't related to a software product that contains product resource information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_UnknownFile : SMS_G_System
{
     DateTime CreationDate;
     UInt32 FileCount;
     SInt64 FileID;
     String FileDescription;
     DateTime FileModifiedDate;
     String FileName;
     String FilePath;
     SInt64 FileSize;
     String FileVersion;
     DateTime ModifiedDate;
     UInt32 ProductId;
     UInt32 ResourceID;
};
```

## Methods

The `SMS_G_System_UnknownFile` class doesn't define any methods.

## Properties

`CreationDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

Date and time when the file was created.

`FileCount` Data type: **UInt32**

Access type: Read/Write

Qualifiers: None

Number of instances of this file found on the client.

`FileDescription` Data type: **String**

Access type: Read/Write

Qualifiers: None

Description from the description resource string. This value is blank for unknown files.

`FileID` Data type: **SInt64**

Access type: Read/Write

Qualifiers: [key]

Configuration Manager-supplied ID that uniquely identifies the file.

`FileModifiedDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

Date and time the file was last modified.

`FileName` Data type: **String**

Access type: Read/Write

Qualifiers: [DefaultOrder("ASC")]

Name of the file.

`FilePath` Data type: **String**

Access type: Read/Write

Qualifiers: None

Path to the file where it was found on the client computer.

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

Date and time the file was last modified.

`ProductId` Data type: **UInt32**

Access type: Read/Write

Qualifiers: None

Not used.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

Although this class contains the same unknown file information that is found in [SMS_G_System_SoftwareFile Server WMI Class](sms_g_system_softwarefile-server-wmi-class), there's no advantage to querying against this class for unknown product files. It's recommended to use `SMS_G_System_SoftwareFile` for all queries involving inventoried files.

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