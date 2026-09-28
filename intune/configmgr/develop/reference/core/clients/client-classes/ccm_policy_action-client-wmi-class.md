---
layout: Conceptual
title: CCM_Policy_Action Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class
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
description: In Configuration Manager, the CCM_Policy_Action class is a client Windows Management Instrumentation class that represents settings for a policy action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3871356b-5cbb-42f6-659f-ea7afd2b8d60
document_version_independent_id: 1412d329-f8b8-4685-e3e9-59fc5b13de9d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8bc5501c-6c7d-d110-5ac7-cf661ca99662
---

# CCM_Policy_Action Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Action` class is a client Windows Management Instrumentation (WMI) class that represents settings for a policy action.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Action : CCM_Policy_Config
{
      String ActionData;
      String ActionType;
};
```

## Methods

The `CCM_Policy_Action` class does not define any methods.

## Properties

`ActionData` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Handler-specific data and policy settings defined in MOF to be compiled directly into the appropriate `RequestedConfig` namespace. The MOF text should only contain object definitions and should not include any class definitions or #pragma statements.

`ActionType` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

The type of the action, which must map to a registered action handler. The default value is WMI-MOF.

## Remarks

This class is only used to support objects reflected in the `RuleActions` property in [CCM_Policy_Rule Client WMI Class](ccm_policy_rule-client-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).