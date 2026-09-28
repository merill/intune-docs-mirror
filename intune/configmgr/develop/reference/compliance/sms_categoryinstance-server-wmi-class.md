---
layout: Conceptual
title: SMS_CategoryInstance Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class
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
description: An SMS Provider server class that represents a category instance for replicating information about a category, for example, a product or a classification, to all child sites.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ea4c9bf2-2610-3190-9b8c-69989afdc73b
document_version_independent_id: d3c42fd6-8bdd-c55d-0024-877c053f3f2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 51edae46-6b30-bbad-f34e-507169b3ba9c
---

# SMS_CategoryInstance Class - Configuration Manager | Microsoft Learn

The `SMS_CategoryInstance` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a category instance used to replicate information about a category, for example, a product or a classification, to all child sites. This class is used in settings management monitoring.

## Syntax

```
Class SMS_CategoryInstance : SMS_CategoryInstanceBase
{
      String CategoryInstance_UniqueID;
      UInt32 CategoryInstanceID;
      String CategoryTypeName;
      String LocalizedCategoryInstanceName;
      SMS_Category_LocalizedProperties LocalizedInformation[];
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ParentCategoryInstanceID;
      String SourceSite;
};
```

## Methods

The `SMS_CategoryInstance` class does not define any methods.

## Properties

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, SizeLimit("512")

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`CategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`CategoryTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`LocalizedCategoryInstanceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_Category_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: [lazy]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`ParentCategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](sms_categoryinstancebase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    To use this class, the application creates an `SMS_CategoryInstance` object and sets the properties, as required, for the particular baseline configuration item.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).