---
layout: Conceptual
title: CCM_Policy_Assignment2 Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment2-client-wmi-class
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
description: Learn how to use the CCM_Policy_Assignment2 class to represent a policy assignment in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 724d2fa3-aa7c-9820-4a60-86df06d0a35d
document_version_independent_id: 3f16df3b-6f61-5fbf-9310-a893b215cc81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment2-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment2-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment2-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4db42144-dd92-6299-6231-67934cf756f2
---

# CCM_Policy_Assignment2 Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_Assignment2` class is a client Windows Management Instrumentation (WMI) class that represents a policy assignment.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Assignment2 : CCM_Policy_Config
{
      String AssignmentCondition;
      String AssignmentCookie;
      String AssignmentID;
      ref:CCM_Policy_Policy AssignmentPolicy;
      String AssignmentSource;
      String AssignmentVersion;
};
```

## Methods

The `CCM_Policy_Assignment2` class does not define any methods.

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

`AssignmentVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_Null:ToInstance ToSubClass]

Version of the assignment.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).