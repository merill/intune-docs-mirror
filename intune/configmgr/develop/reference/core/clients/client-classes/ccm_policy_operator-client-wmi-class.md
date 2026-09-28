---
layout: Conceptual
title: CCM_Policy_Operator Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class
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
description: Learn how to store a compound expression that evaluates to either true or false in Configuration Manager using CCM_Policy_Operator.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 602e90be-5e67-c23a-1ad5-046554ed1c6f
document_version_independent_id: 1330c054-8abb-9b0a-e8a7-146cc9504f54
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 39c54dee-94f1-1bd0-e675-5fcf93a9dddc
---

# CCM_Policy_Operator Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Operator` class is a client Windows Management Instrumentation (WMI) class that stores a compound expression that evaluates to either `true` or `false`.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_Policy_Operator : CCM_Policy_Config
{
      String OperatorType;
   Object Operands[];
};
```

## Properties

`OperatorType` Data type: `String`

Access type: Read-only

Qualifier: [Not\_Null:ToInstance]

The type of operator. Possible values are:

| Value | Description |
| --- | --- |
| `AND` | A logical `AND` operator. The result of the compound expression is only `true` if all of its operands evaluate to `true`. |
| `OR` | A logical `OR` operator. The result of the compound expression is `true` if any one of its operands evaluates to `true`. |
| `NOT` | A logical `NOT` operator. This operator can only have a single operand. The result of the expression is `true` only if the operand evaluates to `false`. |

`Operands` Data type: `Object`

Access type: Read-only

Qualifier: [Not\_Null:ToInstance]

Operands for the compound expression. Each operand can be a [CCM_Policy_Expression Client WMI Class](ccm_policy_expression-client-wmi-class) object or a `CCM_Policy_Operator` object if further nesting is required.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).