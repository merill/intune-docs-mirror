---
layout: Conceptual
title: SMS_ProductFileInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_productfileinfo-server-wmi-class
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
description: The SMS_ProductFileInfo WMI class represents a combination of file and product information for inventory and metering.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: db1691ce-9af9-77ab-1260-92301acd58b9
document_version_independent_id: de7a387d-245f-3ecd-119b-50d9a4f42fe9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_productfileinfo-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_productfileinfo-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_productfileinfo-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: a65d8bff-567b-30d4-95b2-4cc189e17664
---

# SMS_ProductFileInfo Class - Configuration Manager | Microsoft Learn

The `SMS_ProductFileInfo` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a combination of file and product information for inventory and metering.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ProductFileInfo : SMS_BaseClass
{
      String CompanyName;
      String FileDescription;
      SInt64 FileID;
      String FileName;
      UInt32 FileSize;
      String FileVersion;
      UInt32 ProductLanguage;
      String ProductName;
      String ProductVersion;
};
```

## Methods

The `SMS_ProductFileInfo` class does not define any methods.

## Properties

`CompanyName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the company that made the file, taken from the `Company` property of the file version resources.

`FileDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the file, taken from the file version resources.

`FileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: [key]

Auto-incremented key.

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the file.

`FileSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size of the file.

`FileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

File version of the file, taken from the file version resources.

`ProductLanguage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Language of the product.

`ProductName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Product name.

`ProductVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Product version, taken from the file version resources.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

This class provides the source for the `FileID` foreign key property in other classes. When a file is metered, information about the file is sent with the process execution information. This is a subset of the information that is reported by software inventory. The common information that is shared between software inventory and software metering is represented by this class, which lists every file known to the operating system.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).