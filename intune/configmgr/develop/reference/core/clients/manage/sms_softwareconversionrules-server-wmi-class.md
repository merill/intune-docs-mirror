---
layout: Conceptual
title: SMS_SoftwareConversionRules Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class
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
description: Learn how to use SMS_SoftwareConversionRules to describe rules to convert the company or product name resource string into a standard name.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ae0eab92-97aa-3130-66f8-0312923881f7
document_version_independent_id: 44aef38e-a4be-54d9-1869-d33fa5f646e2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 37e8b4db-3bbd-d857-3238-10db3937d0aa
---

# SMS_SoftwareConversionRules Class - Configuration Manager | Microsoft Learn

The `SMS_SoftwareConversionRules` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that describes the rules to convert the company or product name resource string into a standard name for software inventory. For example, different Microsoft products might contain variations of the Microsoft company name, for example, "Microsoft Corporation" or "Microsoft."

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SoftwareConversionRules : SMS_BaseClass
{
     String ConvertType;
     String NewName;
     String OriginalName;
     UInt32 RuleId;
};
```

## Methods

The `SMS_SoftwareConversionRules` class doesn't define any methods.

## Properties

`ConvertType` Data type: **String**

Access type: Read/Write

Type of resource string to convert. Possible values are:

- Manufacturer (default)
- Product

    `NewName` Data type: **String**

    Access type: Read/Write

    Qualifiers: [Not\_Null]

    Name reported to software inventory. The default value is "".

    `OriginalName` Data type: **String**

    Access type: Read/Write

    Qualifiers: [Not\_Null]

    Original company or product name. The default value is "".

    The original name can contain SQL wildcard characters (&, \_, [], and [^]), but the `OriginalName` and `ConvertType`combination must be unique.

    `RuleId` Data type: **UInt32**

    Access type: Read-only

    Qualifiers: [key, read, Not\_Null]

    Unique ID of the rule. The default value is 0.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).