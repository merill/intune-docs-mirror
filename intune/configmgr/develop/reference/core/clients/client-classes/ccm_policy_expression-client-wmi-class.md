---
layout: Conceptual
title: CCM_Policy_Expression Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class
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
description: A client Windows Management Instrumentation class that represents a policy expression, which evaluates to either true or false.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 49418a34-4956-950b-1961-698d44006b9a
document_version_independent_id: 04a7f9b7-ea15-e904-bb5a-23b3da8bd224
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f65a0868-31d9-b0bf-b031-b0aa2d3981c0
---

# CCM_Policy_Expression Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Expression` class is a client Windows Management Instrumentation (WMI) class that represents a policy expression that evaluates to either `true` or `false`.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Expression : CCM_Policy_Config
{
      String ExpressionData;
      String ExpressionLanguage;
      Boolean ExpressionState;
      String ExpressionType;
};
```

## Methods

The `CCM_Policy_Expression` class doesn't define any methods.

## Properties

`ExpressionData` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Data representing the expression to evaluate. The actual format is specific to the expression type. For more information, see `ExpressionType`.

`ExpressionLanguage` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

The type of expression, which must map to an object that contains information about the handler responsible for evaluating this expression type.

`ExpressionState` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Current state of the expression. This value indicates the result of the last expression evaluation, or `null` if the expression has never been evaluated.

`ExpressionType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Type that determines how the expression is evaluated. Possible values are:

| Value | Description |
| --- | --- |
| Once | The expression is evaluated only once. |
| Until-true | The expression continues to be reevaluated until evaluation returns `true`. |
| Continuous | The expression is always reevaluated. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).