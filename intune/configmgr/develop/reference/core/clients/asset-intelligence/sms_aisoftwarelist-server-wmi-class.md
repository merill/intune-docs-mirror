---
layout: Conceptual
title: SMS_AISoftwareList Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class
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
description: Learn how to access all known software titles in the Asset Inteligence catalog using SMS_AISoftwareList.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8f42b945-caa6-abb5-764e-734deeafb150
document_version_independent_id: cfd20385-e8a3-5ef0-c828-5612e7c1f47d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 63a98d64-df30-1cc7-c391-19a4af14d7cf
---

# SMS_AISoftwareList Class - Configuration Manager | Microsoft Learn

The `SMS_AISoftwareList` Windows Management Instrumentation (WMI) class, in Configuration Manager, contains all the known software titles in the Asset Intelligence catalog.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AISoftwareList : SMS_BaseClass
{
      uint32 CategoryID;
      string CategoryName;
      string CommonName;
      string CommonPublisher;
      string CommonVersion;
      uint32 Count; (obsolete in SP1)
      uint32 FamilyID;
      string FamilyName;
      string OfficialCategoryName;
      string OfficialFamilyName;
      string SoftwareCode; (obsolete in SP1)
      uint32 SoftwareCount;
      string SoftwareID; (obsolete in SP1)
      string SoftwareKey;
      string SoftwarePropertiesHash; (obsolete in SP1)
      uint32 State;
      uint32 Tag1ID;
      string Tag1Name;
      uint32 Tag2ID;
      string Tag2Name;
      uint32 Tag3ID;
      string Tag3Name;
};
```

## Methods

The following table lists the methods in the `SMS_AISoftwareList` class.

| Method | Description |
| --- | --- |
| [AddSoftwareHashData Method in Class SMS_AISoftwareList](addsoftwarehashdata-method-in-class-sms_aisoftwarelist) | Adds the `SoftwarePropertiesHash` from `SoftwareCode` and `Title`. |
| [GetCategorizationRequestText Method in Class SMS_AISoftwareList](getcategorizationrequesttext-method-in-class-sms_aisoftwarelist) | Retrieves the categorization XML that is used in requesting categorization from System Center Online. |
| [GetSummary Method in Class SMS_AISoftwareList](getsummary-method-in-class-sms_aisoftwarelist) | Retrieves a summary of all class instances based on the `State` property of the class. |
| [ResolveConflict Method in Class SMS_AISoftwareList](resolveconflict-method-in-class-sms_aisoftwarelist) | Resolves the conflict through the Resolution parameter whose values are:1 - Keep local edit and discard latest update from Microsoft.2 - Revert local edit and replace it with latest update from Microsoft.All other values are ignored. |
| [SetCategorizationRequest Method in Class SMS_AISoftwareList](setcategorizationrequest-method-in-class-sms_aisoftwarelist) | Submits a request to System Center Online for software categorization. |

## Properties

`CategoryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Refers to a [SMS_AICategory Server WMI Class](sms_aicategory-server-wmi-class) instance.

`CategoryName` Data type: `String`

Access type: Read Only

Qualifiers: None

Category name identified by the `CategoryID` property.

`CommonName` Data type: `String`

Access type: Read Only

Qualifiers: None

Software title, as it is commonly known.

`CommonPublisher` Data type: `String`

Access type: Read Only

Qualifiers: None

Publisher of the software title, as it is commonly known.

`CommonVersion` Data type: `String`

Access type: Read Only

Qualifiers: None

Version of the software title, as it is commonly known.

`Count` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

This method/property has been removed or deprecated in Configuration Manager SP1. Use `SoftwareCount` instead.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`FamilyID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Refers to a [SMS_AICategory Server WMI Class](sms_aicategory-server-wmi-class) instance.

`FamilyName` Data type: `String`

Access type: Read Only

Qualifiers: None

Family name identified by the `FamilyID` property.

`OfficialCategoryName` Data type: `String`

Access type: Read Only

Qualifiers: None

The `CategoryID` property can be changed, which alters what the `CategoryName` property contains. This is the original name of the category before any changes have occurred.

`OfficialFamilyName` Data type: `String`

Access type: Read Only

Qualifiers: None

The `FamilyID` property can be changed, which alters what the `FamilyName` property contains. This is the original name of the family before any changes have occurred.

`SoftwareCode` Data type: `String`

Access type: Read Only

Qualifiers: None

Identifier of the software title, defined by the publisher of the software title.

`SoftwareCount` Data type: `UInt32`

Access type: Read Only

Qualifiers: [read]

Count of the software title.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`SoftwareID` Data type: `String`

Access type: Read Only

Qualifiers: None

A Microsoft generated GUID identifying this software title.

This method/property has been removed or deprecated in Configuration Manager SP1.

`SoftwareKey` Data type: `String`

Access type: Read Only

Qualifiers: [key, read]

A Microsoft generated key identifying this software title.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`SoftwarePropertiesHash` Data type: `String`

Access type: Read Only

Qualifiers: key

An automatically generated hash composed of the Name, Publisher, and Version of the software title.

This method/property has been removed or deprecated in Configuration Manager SP1.

`State` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Status of this software record.

| Value | Description |
| --- | --- |
| 0 | Validated, category is defined by Microsoft through System Center Online. |
| 1 | User-defined, category was defined or has been changed by a user. |
| 2 | Pending, the software is pending categorization by Microsoft through System Center Online. |
| 3 | Updatable, the software category can be updated by the user. |
| 4 | Uncategorized, the software has not been categorized by Microsoft or the user. |

`Tag1ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Refers to a [SMS_AICategory Server WMI Class](sms_aicategory-server-wmi-class) instance.

`Tag1Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Tag name identified by the `CategoryID` property.

`Tag2ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Refers to a [SMS_AICategory Server WMI Class](sms_aicategory-server-wmi-class) instance.

`Tag2Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Tag name identified by the `CategoryID` property.

`Tag3ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Refers to a [SMS_AICategory Server WMI Class](sms_aicategory-server-wmi-class) instance.

`Tag3Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Tag name identified by the `CategoryID` property.

## Remarks

Class qualifiers for this class include:

- DisplayName("AI Software List Table")
- Dynamic
- Provider("ExtnProv")
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).