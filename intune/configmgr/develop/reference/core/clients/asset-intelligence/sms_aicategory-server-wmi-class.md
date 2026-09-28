---
layout: Conceptual
title: SMS_AICategory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aicategory-server-wmi-class
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
description: In Configuration Manager, the SMS_AICategory Windows Management Instrumentation class categorizes the software entries in the SMS_AISoftwareList Server WMI class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b6106c6c-0c4b-2034-a907-41e6d71df986
document_version_independent_id: 8995a527-0093-635b-4333-00c4236297bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aicategory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/asset-intelligence/sms_aicategory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aicategory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ff8ba438-bc12-c9ce-4d0d-a8b08698a0e1
---

# SMS_AICategory Class - Configuration Manager | Microsoft Learn

The `SMS_AICategory` Windows Management Instrumentation (WMI) class, in Configuration Manager, categorizes the software entries in the `SMS_AISoftwareList` Server WMI class.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AICategory : SMS_BaseClass
{
      uint32 CategoryID;
      string CategoryName;
      string Description;
      boolean IsLocal;
      uint32 LanguageID;
      uint32 State;
      uint32 Type;
};
```

## Methods

The following table lists the methods in the `SMS_AICategory` class.

| Method | Description |
| --- | --- |
| [GetSummary Method in Class SMS_AICategory](getsummary-method-in-class-sms_aicategory) | Returns a summary of all defined categories. |

## Properties

`CategoryID` Data type: `UInt32`

Access type: Read Only

Qualifiers: key

Unique value for the record.

`CategoryName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Category display name.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Supplemental information that describes what this category is used for.

`IsLocal` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if this category instance was created locally. Categories that are created locally can be changed. When `false`, the `CategoryName` and `Description` properties are not editable.

`LanguageID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Language the category is written in.

`State` Data type: `UInt32`

Access type: Read Only

Qualifiers: enumeration("STATE\_VALIDATED(0), STATE\_USER\_DEFINED(1)")

Source of the category.

| Value | Description |
| --- | --- |
| 0 | Validated: Created by Microsoft. |
| 1 | User Defined: Created by a user. |

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Describes the way this category record is used.

| Value | Description |
| --- | --- |
| 0 | Category: Category this software fits into.Example: Antivirus. |
| 1 | Family: Family this software belongs in.Example: Microsoft Office. |
| 2 | Tag: User defined tags which are assigned to the software entries.Example: Installed on a receptionist's computer. |

## Remarks

Class qualifiers for this class include:

- DisplayName("AI Category Table")
- Dynamic
- Provider("ExtnProv")
- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).