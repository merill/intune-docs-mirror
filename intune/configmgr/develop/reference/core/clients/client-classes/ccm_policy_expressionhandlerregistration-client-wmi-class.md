---
layout: Conceptual
title: CCM_Policy_ExpressionHandlerRegistration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class
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
description: Learn how to describe a registered expression handler for a policy with CCM_Policy_ExpressionHandlerRegistration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 68282818-6f88-91e8-91de-958347a1504e
document_version_independent_id: 8768f95c-da71-8399-dcfc-6260d0c80609
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: d0bd8908-0529-facd-2b48-8dd6971a7efa
---

# CCM_Policy_ExpressionHandlerRegistration Class - Configuration Manager | Microsoft Learn

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Policy_ExpressionHandlerRegistration` class is a client Windows Management Instrumentation (WMI) class that describes a registered expression handler for a policy. An expression handler is a COM object that implements the `ICcmPolicyExpressionHandler` interface.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_ExpressionHandlerRegistration : CCM_Policy_Config
{
      String Clsid;
      String Name;
};
```

## Methods

The `CCM_Policy_ExpressionHandlerRegistration` class does not define any methods.

## Properties

`Clsid` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Class ID of the expression handler COM object, in registry format.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the expression handler. The name is the same as the value of the `ExpressionType` property in [CCM_Policy_Expression Client WMI Class](ccm_policy_expression-client-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).