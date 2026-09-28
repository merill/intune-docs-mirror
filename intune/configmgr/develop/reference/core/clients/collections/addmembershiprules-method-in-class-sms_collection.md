---
layout: Conceptual
title: AddMembershipRules Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/addmembershiprules-method-in-class-sms_collection
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
description: In Configuration Manager, the AddMembershipRules WMI class method adds multiple new rules to the CollectionRules property of the SMS_Collection Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 8646969a-4a0f-e5e0-1b63-dab02901b960
document_version_independent_id: 10c79d0b-eff8-7a07-b5a9-be93157a61f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/addmembershiprules-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/addmembershiprules-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/addmembershiprules-method-in-class-sms_collection.md
cmProducts: []
platformId: c8e9828e-4111-33fd-7072-7b6709aed71f
---

# AddMembershipRules Method - Configuration Manager | Microsoft Learn

The `AddMembershipRules` (WMI) class method, in Configuration Manager, adds multiple new rules to the `CollectionRules` property of the [SMS_Collection Server WMI Class](sms_collection-server-wmi-class) object.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddMembershipRules(
     SMS_CollectionRule collectionRules[],
     UInt32 QueryIDs[]
);
```

#### Parameters

`collectionRules` Data type: `SMS_CollectionRule` Array

Qualifiers: [in]

[SMS_CollectionRule Server WMI Class](sms_collectionrule-server-wmi-class) objects to add.

`QueryIDs` Data type: `UInt32` Array

Qualifiers: [out]

IDs corresponding to the rules. These are Configuration Manager-generated query IDs for query rules. The IDs for direct rules are set to 0. Use `QueryID` to modify or delete a query membership rule.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Remarks

The `AddMembershipRules` method does not validate a query rule, but simply adds it to the rules list. This can create debugging issues when the collection does not contain the intended membership. Your application should always validate the query rule before adding it to the collection rules by using the [ValidateQuery Method in Class SMS_CollectionRuleQuery](validatequery-method-in-class-sms_collectionrulequery).

The `AddMembershipRules` method can also be used to modify membership rules. Only query rules can be modified.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see Configuration Manager Server Development Requirements.