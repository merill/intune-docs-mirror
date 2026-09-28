---
layout: Conceptual
title: CCM_Policy_Condition Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class
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
description: Learn how to represent a policy condition in Configuration Manager using CCM_Policy_Condition.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c3431494-7be7-bb1f-c346-bb220f703883
document_version_independent_id: 2a1ff1d1-fdf1-218e-8bd7-b6668d6df8c6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: 72e95487-aafc-7323-bd7f-8ac763aa36c9
---

# CCM_Policy_Condition Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Condition` class is a client Windows Management Instrumentation (WMI) class that represents a policy condition.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Condition : CCM_Policy_Config
{
      String ConditionID;
      Boolean ConditionState;
      Object ConditionExpression;
};
```

## Properties

`ConditionID` Data type: `Boolean`

Access type: Read-only

Qualifiers: [key]

Condition ID.

`ConditionState` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Current state of the condition. This value indicates the result of the last condition evaluation, or it is `null` if the condition has never been evaluated.

`ConditionExpression` Data type: `Object`

Access type: Read-only

Qualifiers: [read]

Actual expression to evaluate. The value is a [CCM_Policy_Expression Client WMI Class](ccm_policy_expression-client-wmi-class) object for a simple expression or a [CCM_Policy_Operator Client WMI Class](ccm_policy_operator-client-wmi-class) object for a compound expression.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).