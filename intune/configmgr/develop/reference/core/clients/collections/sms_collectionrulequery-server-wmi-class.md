---
layout: Conceptual
title: SMS_CollectionRuleQuery Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class
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
description: In Configuration Manager, the SMS_CollectionRuleQuery Windows Management Instrumentation class is an SMS Provider server class that represents a member of a collection based on the results of a query.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c9a11feb-96fb-54e0-b21a-b0f733f94a28
document_version_independent_id: 5e3a00d9-03f7-929e-8078-a6d7e76f645c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3000cc85-0299-af12-b20b-b180f982b9d9
---

# SMS_CollectionRuleQuery Class - Configuration Manager | Microsoft Learn

The `SMS_CollectionRuleQuery` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a member of a collection based on the results of a query.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionRuleQuery : SMS_CollectionRule
{
      String QueryExpression;
      UInt32 QueryID;
      String RuleName;
};
```

## Methods

The following table lists the methods in the `SMS_CollectionRuleQuery` class.

| Method | Description |
| --- | --- |
| [ValidateQuery Method in Class SMS_CollectionRuleQuery](validatequery-method-in-class-sms_collectionrulequery) | Validates the collection rule query. |

## Properties

`QueryExpression` Data type: `String`

Access type: Read/Write

Qualifiers: None

WQL SELECT statement having results that are used to populate the collection. The statement must specify a resource class name. The default value is "".

Your application can use the `LimitToCollectionID` property to further limit the results. Note that the SMS Provider might alter the text of the query to make it more amenable to collection evaluation.

`QueryID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Auto-generated ID that is only useful when deleting a rule.

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