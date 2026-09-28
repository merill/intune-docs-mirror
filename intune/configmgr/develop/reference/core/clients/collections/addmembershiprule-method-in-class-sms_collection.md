---
layout: Conceptual
title: AddMembershipRule Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/addmembershiprule-method-in-class-sms_collection
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
description: Learn how to add a new rule to the CollectionRules property of the SMS_Collection Server WMI Class in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6691bd9e-c37a-d3ee-6b18-c4036c0e027c
document_version_independent_id: 4c7881b6-d27c-6ccd-d6e5-e023123c0e88
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/addmembershiprule-method-in-class-sms_collection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/addmembershiprule-method-in-class-sms_collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/addmembershiprule-method-in-class-sms_collection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b3a5eb83-a523-011d-9447-78f3abff1648
---

# AddMembershipRule Method - Configuration Manager | Microsoft Learn

The `AddMembershipRule` Windows Management Instrumentation (WMI) class method, in Configuration Manager, adds a new rule to the `CollectionRules` property of the [SMS_Collection Server WMI Class](sms_collection-server-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 AddMembershipRule(
     SMS_CollectionRule collectionRule,
     UInt32 QueryID
);
```

#### Parameters

`collectionRule` Data type: `SMS_CollectionRule`

Qualifiers: [in]

[SMS_CollectionRule Server WMI Class](sms_collectionrule-server-wmi-class) object to add.

`QueryID` Data type: `UInt32`

Qualifiers: `[out]`

Configuration Manager-generated query ID if the rule is a query rule. If the rule is direct, this ID is 0. Use `QueryID` to modify or delete a query membership rule.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](../../../../core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).