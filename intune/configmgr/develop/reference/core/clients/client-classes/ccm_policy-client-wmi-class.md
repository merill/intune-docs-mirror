---
layout: Conceptual
title: CCM_Policy Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class
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
description: Learn how to use CCM_Policy Client Windows Management Instrumentation class in Configuration Manager to represent a client policy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 16e71781-230f-ed2a-9cac-999273b57b30
document_version_independent_id: effafefd-c0f5-b52e-aa5d-5a1ba1252bd2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a114efae-6ab3-0fc3-232a-684761997e77
---

# CCM_Policy Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy` class is a client Windows Management Instrumentation (WMI) class that represents a client policy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy
{
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Policy` class does not define any methods.

## Properties

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy.

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the policy instance.

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Precedence is used to resolve conflicts between policies from the same policy authority. For example, this occurs in Configuration Manager when using collection variables to override site-wide policy, or setting a value for a collection variable on multiple collections of which the same client is a member.

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the rule used to create the policy.

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Source of the policy.

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Version of the policy.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).