---
layout: Conceptual
title: SMS_UpdateCategoryInstance Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class
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
description: The SMS_UpdateCategoryInstance class is an SMS Provider server class that represents a software-update-specific SMS_CategoryInstance Server WMI Class object available on the site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6db0873b-41d5-1116-3936-e5d950f865d4
document_version_independent_id: dccf5d7d-33b5-c0d4-43ff-6e5d582f9218
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fb1bd166-a0b1-e642-c565-ae559931e415
---

# SMS_UpdateCategoryInstance Class - Configuration Manager | Microsoft Learn

The `SMS_UpdateCategoryInstance` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a software-update-specific `SMS_CategoryInstance Server WMI Class` object available on the site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UpdateCategoryInstance : SMS_CategoryInstanceBase  
{  
      Boolean AllowSubscription;  
      String CategoryInstance_UniqueID;  
      UInt32 CategoryInstanceID;  
      String CategoryTypeName;  
      Boolean IsSubscribed;  
      String LocalizedCategoryInstanceName;  
      SMS_Category_LocalizedProperties LocalizedInformation[];  
      UInt32 LocalizedPropertyLocaleID;  
      UInt32 ParentCategoryInstanceID;  
      String SourceSite;  
};  
```

## Methods

The `SMS_UpdateCategoryInstance` class does not define any methods.

Warning

The `ResendObjectToAllSites Method in Class SMS_UpdateCategoryInstance` has been deprecated in Configuration Manager.

## Properties

`AllowSubscription` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the category instance is enabled for subscription to the category metadata from the software update source. The default value is `false`. For more information, see [SMS_SoftwareUpdateSource Server WMI Class](sms_softwareupdatesource-server-wmi-class).

Note

Not all categories can be marked for subscription.

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: [unique, SizeLimit("512")

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`CategoryInstanceID` Data type: `UInt``3``2`

Access type: Read-only

Qualifiers: [key, read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`CategoryTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`IsSubscribed` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [read]

`true` if the category instance allows subscription. The default value is `false`. Set this property to `true` only if the `AllowSubscription` property is set to `true`.

`LocalizedCategoryInstanceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_Category_LocalizedProperties Array` Access type: Read/Write

Qualifiers: [lazy]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`ParentCategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read]

See [SMS_CategoryInstanceBase Server WMI Class](../compliance/sms_categoryinstancebase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Your application uses the `SMS_UpdateCategoryInstance` class after creating or modifying a software update deployment using [SMS_UpdatesAssignment Server WMI Class](sms_updatesassignment-server-wmi-class). The application can use [SMS_CIAllCategories Server WMI Class](sms_ciallcategories-server-wmi-class) to query for all categories associated with the software updates configuration item or for all configuration items associated with a category.

    To use this class, the application obtains an `SMS_SoftwareUpdateSource` object and sets the properties as required for the particular software update and the source.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).