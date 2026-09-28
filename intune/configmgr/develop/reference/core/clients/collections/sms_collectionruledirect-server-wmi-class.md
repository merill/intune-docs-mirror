---
layout: Conceptual
title: SMS_CollectionRuleDirect Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class
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
description: An SMS Provider server class that represents a resource. The resource is to be made an unconditional member of the collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0a819bbc-9714-eff0-06e3-6c4c0c529c69
document_version_independent_id: 4b18b656-8ff4-bb9c-d86e-c7c501915fc8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cdc838e4-e845-71c7-9c5c-b21be59d6580
---

# SMS_CollectionRuleDirect Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionRuleDirect` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a resource that is to be made an unconditional member of the collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRuleDirect : SMS_CollectionRule
{
      String ResourceClassName;
      UInt32 ResourceID;
      String RuleName;
};
```

## Methods

The `SMS_CollectionRuleDirect` class does not define any methods.

## Properties

`ResourceClassName` Data type: `Strin``g`

Access type: Read/Write

Qualifiers: None

Name of the resource class to which the resource belongs, for example, [SMS_R_System Server WMI Class](../manage/sms_r_system-server-wmi-class). The default value is "".

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the resource that is to become a member of the collection. The default value is 0.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CollectionRule Server WMI Class](sms_collectionrule-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Embedded

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).