---
layout: Conceptual
title: SMS_G_System_SoftwareProduct Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwareproduct-server-wmi-class
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
description: The SMS_G_System_SoftwareProduct class is an SMS Provider server class that provides software product information for software files that contain resource strings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a30932e2-fe15-368e-f89a-4382779437da
document_version_independent_id: 1183d6fc-7568-62f4-ae1c-f8fdd82c3f20
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwareproduct-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_g_system_softwareproduct-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwareproduct-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: d45d4cdc-64db-3776-b7d3-7123f818d568
---

# SMS_G_System_SoftwareProduct Class - Configuration Manager | Microsoft Learn

The `SMS_G_System_SoftwareProduct` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that provides software product information for software files that contain resource strings.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_SoftwareProduct : SMS_G_System
{
     String CompanyName;
     UInt32 ProductId;
     UInt32 ProductLanguage;
     String ProductName;
     String ProductVersion;
     UInt32 ResourceID;
};
```

## Methods

The `SMS_G_System_SoftwareProduct` class doesn't define any methods.

## Properties

`CompanyName` Data type: **String**

Access type: Read/Write

Qualifiers: none

Name of the software manufacturer taken from the company name resource string. This name can be universally changed by using the rules that are defined in [SMS_SoftwareConversionRules Server WMI Class](sms_softwareconversionrules-server-wmi-class).

`ProductId` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

Configuration Manager-supplied ID that uniquely identifies the product. The property links this product with the software file information contained in an [SMS_G_System_SoftwareFile Server WMI Class](sms_g_system_softwarefile-server-wmi-class) object.

`ProductLanguage` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [Subtype("Locale ID")]

Language taken from the language resource string.

`ProductName` Data type: **String**

Access type: Read/Write

Qualifiers:[DefaultOrder("ASC")]

Value of the product name resource string.

`ProductVersion` Data type: **String**

Access type: Read/Write

Qualifiers: none

Value of the product version resource string.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

See [SMS_G_System Server WMI Class](sms_g_system-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

The Software Inventory Agent inventories files identified in the site control file. To identify the files to inventory, the agent:

1. Queries the site control [SMS_SCI_ClientComp Server WMI Class](../../servers/configure/sms_sci_clientcomp-server-wmi-class) objects for items having the value "Software Inventory Agent" for the `ClientComponentName` property.
2. Loops through the embedded property list. When the value for `PropertyName` is "Inventoriable Types", the agent updates the comma-delimited list of file names (including extensions) in the `Value2` property. When the value for `PropertyName` is "Inventory Schedule", the agent updates the interval string in the `Value2` property. For information about creating an interval string, see the example for the [WriteToString Method in Class SMS_ScheduleMethods](../../servers/configure/writetostring-method-in-class-sms_schedulemethods) method. When the value for `PropertyName` is "Report Options", the agent updates the reporting options value in the `Value` property, specifying at least one reporting option for the software inventory to be collected. The following table lists the reporting options.

    | Reporting option | Description |
    | --- | --- |
    | Product version information. Bit 0. | Inventories products that contain company and product resource information. |
    | Files associated with known products. Bit 1. | Inventories files associated with products that contain company and product resource information. For example, Wwintl32.dll is inventoried because it's associated with Microsoft Word. Set this bit only if the product version information reporting option is selected. |
    | Files not associated with known products. Bit 2. | Inventories files that don't include company and product resource information (unknown files). |
3. For newly added inventory types, adds entries to the following `Path`, `Subdirectories`, and `Exclude` embedded property lists.

    Updates the site control file. For more information, see [About the site control file](../../../../core/understand/about-the-configuration-manager-site-control-file).

Note

Collecting inventory information for some files, for example, DLL files, can generate a large volume of network traffic and substantially increase the size of the Configuration Manager database. For this reason, test any changes you make in a test environment before implementing them in a production environment.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).