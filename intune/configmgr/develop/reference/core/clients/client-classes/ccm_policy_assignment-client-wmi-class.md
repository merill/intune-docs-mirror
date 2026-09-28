---
layout: Conceptual
title: CCM_Policy_Assignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class
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
description: The CCM_Policy_Assignment class is a client Windows Management Instrumentation (WMI) class that represents a policy assignment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a4d077e1-2360-08ae-5f29-f384447082a8
document_version_independent_id: 470c18df-e556-c0f8-c308-1fa64db448b3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2b19b9d8-d0e0-7d5c-7aa7-cc26b1570466
---

# CCM_Policy_Assignment Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Assignment` class is a client Windows Management Instrumentation (WMI) class that represents a policy assignment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Assignment : CCM_Policy_Config
{
      String AssignmentCondition;
      String AssignmentCookie;
      String AssignmentID;
      ref:CCM_Policy_Policy AssignmentPolicy;
      String AssignmentSource;
};
```

## Methods

The `CCM_Policy_Assignment` class does not define any methods.

## Properties

`AssignmentCondition` Data type: `String`

Access type: Read/Write

Qualifiers: None

Assignment condition that determines if the policy should be applied to the assignment. Set this property to NULL if the policy always applies, or to the ID of a particular policy condition, represented by [CCM_Policy_Condition Client WMI Class](ccm_policy_condition-client-wmi-class).

`AssignmentCookie` Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance]

Arbitrary data used by the source authority.

`AssignmentID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the assignment.

`AssignmentPolicy` Data type: `ref:CCM_Policy_Policy`

Access type: Read-only

Qualifiers: [read, Not\_Null:ToInstance]

Reference to the policy object to which the assignment applies.

`AssignmentSource` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_Null:ToInstance]

Source authority of the assignment.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).