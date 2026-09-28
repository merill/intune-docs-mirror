---
layout: Conceptual
title: CCM_Policy_ActionHandlerRegistration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class
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
description: A class that supports the Configuration Manager 2007 infrastructure and isn't intended to be used directly from your code.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 80d6b0eb-43e4-38cd-b106-0836de6fce39
document_version_independent_id: 45f8bcbc-082a-b37d-f434-f1ac0bc8c173
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 454c9eb9-270c-700d-6614-8e2a8bd226ef
---

# CCM_Policy_ActionHandlerRegistration Class - Configuration Manager | Microsoft Learn

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Policy_ActionHandlerRegistration` class is a client Windows Management Instrumentation (WMI) class that represents an action handler registration for a policy. An action handler is a COM object that applies a particular type of policy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_ActionHandlerRegistration : CCM_Policy_Config
{
      String Clsid;
      String Name;
      String Type;
};
```

## Methods

The `CCM_Policy_ActionHandlerRegistration` class does not define any methods.

## Properties

`Clsid` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Class ID of the action handler COM object in registry format.

`Name` Data type`: String`

Access type: Read/Write

Qualifiers: [key]

Name of the action handler. This name is the same as the value of the `ActionType` property in [CCM_Policy_Action Client WMI Class](ccm_policy_action-client-wmi-class).

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

The type of the action handler, which defaults to WMI. The handler implements the `ICcmPolicyWmiActionHandler` interface for creating WMI objects in the `RequestConfig` namespace.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).