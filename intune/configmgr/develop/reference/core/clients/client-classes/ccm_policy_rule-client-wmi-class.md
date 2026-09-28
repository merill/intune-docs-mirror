---
layout: Conceptual
title: CCM_Policy_Rule Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class
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
description: Learn how to define a policy object rule used in the PolicyRules property with the CCM_Policy_Rule class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 9f7a4dc9-5b6e-2559-9873-8e90229e3b31
document_version_independent_id: c5608226-ea77-bab1-f4b9-f5da7417b984
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6b35ec51-337b-0ced-60b8-eee729c33c6e
---

# CCM_Policy_Rule Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Rule` class is a client Windows Management Instrumentation (WMI) class that defines a policy object rule. Objects of this class are only used in the `PolicyRules` property in [CCM_Policy_Policy Client WMI Class](ccm_policy_policy-client-wmi-class).

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class  CCM_Policy_Rule : CCM_Policy_Config
{
      String RuleID;
      String RuleCondition;
      Object RuleActions[];
};
```

## Properties

`RuleID` Data type: `String`

Access type: Read-only

Qualifiers: [key]

Unique ID of the rule within the policy object.

`RuleCondition` Data type: `String`

Access type: Read-only

Qualifiers: None

Optional. Rule condition. If the condition is not NULL, set this property to the unique ID of a [CCM_Policy_Condition Client WMI Class](ccm_policy_condition-client-wmi-class) object. The rule is only applied if the policy is active and the rule condition evaluates to TRUE.

`RuleActions` Data type: `Object` Array

Access type: Read-only

Qualifiers: None

Array of [CCM_Policy_Action Client WMI Class](ccm_policy_action-client-wmi-class) objects specifying the actions to perform when the rule is applied.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).