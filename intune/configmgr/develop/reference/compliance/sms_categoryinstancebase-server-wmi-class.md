---
layout: Conceptual
title: SMS_CategoryInstanceBase Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class
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
description: Learn how to use the SMS_CategoryInstanceBase class which is an SMS Provider server class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9589a3f6-6a5f-79c0-62d1-5a53aee71849
document_version_independent_id: 137bd0cc-644b-d09e-779a-7ba8df55d9bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1c817a8c-c339-980c-a424-dd85aab19819
---

# SMS_CategoryInstanceBase Class - Configuration Manager | Microsoft Learn

The `SMS_CategoryInstanceBase` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class for the [SMS_CategoryInstance Server WMI Class](sms_categoryinstance-server-wmi-class) and [SMS_UpdateCategoryInstance Server WMI Class](../sum/sms_updatecategoryinstance-server-wmi-class) classes.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CategoryInstanceBase : SMS_BaseClass
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

The `SMS_CategoryInstanceBase` class does not define any methods.

## Properties

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, SizeLimit("512")

Unique ID of the category instance. This ID is unique across sites. The string length can be up to 512 characters.

`CategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

ID of the category instance. This ID is not unique across sites.

`CategoryTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The type of category represented by the category instance. Possible values are:

- Product
- Locale
- Classification
- Company
- Product Family
- User

    `LocalizedCategoryInstanceName` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    The localized name of the category instance.

    `LocalizedInformation` Data type: `SMS_Category_LocalizedProperties` Array

    Access type: Read/Write

    Qualifiers: [lazy]

    Localized properties associated with the category instance.

    `LocalizedPropertyLocaleID` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    ID of the locale applying to the localized properties.

    `ParentCategoryInstanceID` Data type: `UInt32`

    Access type: Read-only

    Qualifiers: [read]

    ID of the parent for the category instance.

    `SourceSite` Data type: `String`

    Access type: Read-only

    Qualifiers: [read]

    The site code for the site where the category instance is created.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).