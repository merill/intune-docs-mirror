---
layout: Conceptual
title: SMS_CIAllCategories Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_ciallcategories-server-wmi-class
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
description: Lists all SMS_CategoryInstance Server WMI Class or SMS_UpdateCategoryInstance Server WMI Class object instances for a given SMS_ConfigurationItem object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b75d0636-b84e-5066-06b5-61823441b3e0
document_version_independent_id: c6aba225-dd93-26fd-789e-517b85c8f240
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_ciallcategories-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_ciallcategories-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_ciallcategories-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 78d67a74-0f3e-4da3-094d-78a935211cd2
---

# SMS_CIAllCategories Class - Configuration Manager | Microsoft Learn

The `SMS_CIAllCategories` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that lists all of the SMS\_CategoryInstance Server WMI Class or [SMS_UpdateCategoryInstance Server WMI Class](sms_updatecategoryinstance-server-wmi-class) object instances for a given SMS\_ConfigurationItem object.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CIAllCategories : SMS_BaseClass
{
    UInt32 CategoryInstanceID;
    String CategoryInstance_UniqueID;
    String CategoryTypeName;
    UInt32 CI_ID;
    String CI_UniqueID;
    String LocalizedCategoryInstanceName;
    UInt32 LocalizedPropertyLocaleID;
    String ModelName;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_CIAllCategories` class does not define any methods.

## Properties

`CategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read, Not\_null]

Configuration Manager-generated, site-specific ID for the category instance. This ID is defined by the `CategoryInstanceID` property of SMS\_CategoryInstanceBase Server WMI Class for the specific configuration item.

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, SizeLimit("512")]

The unique ID for the category instance. This string can have a maximum of 512 characters. This ID is defined by the `CategoryInstance_UniqueID` property of SMS\_CategoryInstanceBase Server WMI Class for the specific configuration item.

`CategoryTypeName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read, Not\_null]

The unique ID of the configuration item. This ID is unique only for the site. The ID is defined by the `CI_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class for the specific configuration item.

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_ConfigurationItemLatestBaseClass Server WMI Class](../compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

    Use this class to query for all categories associated with a configuration item, or all configuration items associated with a category.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).