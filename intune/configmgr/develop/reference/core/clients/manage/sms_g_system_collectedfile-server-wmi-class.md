---
layout: Conceptual
title: SMS_G_System_CollectedFile Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_collectedfile-server-wmi-class
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
description: Learn how to use SMS_G_System_CollectedFile class which contains information about a file copied from the client computer to the site server.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bcecc4d8-b791-f777-4a1b-8aadf61f4378
document_version_independent_id: 51014475-a2e6-aee6-9c6b-0936232bbfb9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_collectedfile-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_collectedfile-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_collectedfile-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 1928d9d9-b6b5-7d55-3354-dc5b45eb808b
---

# SMS_G_System_CollectedFile Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_CollectedFile` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains information about a file copied from the client computer to the site server.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_CollectedFile : SMS_G_System
{
     DateTime CollectionDate;
     UInt8 FileData[];
     String FileName;
     String FilePath;
     UInt32 FileSize;
     DateTime FileModifyDate;
     String LocalFilePath;
     DateTime ModifiedDate;
     UInt32 ResourceID;
     UInt32 RevisionID;
};
```

## Methods

The `SMS_G_System_CollectedFile` class does not define any methods.

## Properties

`CollectionDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was collected from the client computer.

`FileData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: [lazy]

Contents of the file.

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: [DefaultOrder("ASC")]

Name and file name extension of the file.

`FilePath` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Path to the file on the client computer.

`FileSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size of the file, in bytes.

`LocalFilePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Path to the file on the site server.

`ModifiedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was last modified.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Revision ID that increments each time an inventory is taken to identify the number of times the file has been inventoried. The file is only inventoried when it has changed.

`FileModifyDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was last modified.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

The Software Inventory Agent collects files identified in the site control file. To identify the files to collect, the agent:

1. Queries the site control [SMS_SCI_ClientComp Server WMI Class](../../servers/configure/sms_sci_clientcomp-server-wmi-class) objects for items having the value "Software Inventory Agent" for the `ClientComponentName` property.
2. Loops through the embedded property list. When the value for `PropertyName` is "Collectable Files", the agent updates the comma-delimited list of file names (including extensions) in the `Value2` property. When the value for `PropertyName` is "Max Collected File Size", the agent sets a maximum size, in megabytes, for the files that Configuration Manager collects from the client, for that query, during each software inventory cycle.
3. For any new collectable file added, adds an entry to each of the embedded property lists Collectable File Path, Collectable File Subdirectories, Collectable File Exclude, and Collectable File Max Size.
4. Updates the site control file. For more information, see [About the site control file](../../../../core/understand/about-the-configuration-manager-site-control-file).

Note

Collecting files from clients can generate a large volume of network traffic and require extensive storage space. For this reason, you should test any changes you make in a test environment before implementing them in a production environment.

Collected files are deleted on a schedule if the Delete Aged Collected Files database maintenance task is set to `true` in the Configuration Manager console. You can also enable this task and set the schedule by updating the site control file. The site control item is an instance of [SMS_SCI_SQLTask Server WMI Class](../../servers/configure/sms_sci_sqltask-server-wmi-class) and the `TaskName` value is "Delete Aged Collected Files".

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).