---
layout: Conceptual
title: CCM_Policy_AuthorityData Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: In Configuration Manager, the CCM_Policy_AuthorityData class is a client WMI class that stores information about policy from a particular authority.
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f2e6bf89-f06a-9450-6672-48e8d919ac72
document_version_independent_id: ac548be0-a751-b7d6-2009-4c3047a33826
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8714e72f-647a-0f06-7505-66d49746791e
---

# CCM_Policy_AuthorityData Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_Policy_AuthorityData` class is a client Windows Management Instrumentation (WMI) class that stores information about policy from a particular authority.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_AuthorityData : CCM_Policy_Config
{
      DateTime LastReplyTime;
      String Name;
      String ServerCookie;
};
```

## Methods

The `CCM_Policy_AuthorityData` class does not define any methods.

## Properties

`LastReplyTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The last date and time when the authority replied to a request for policy assignments. If this value is older than the value of `PolicyTimeUntilAck` in the authority's [CCM_PolicyAgent_Configuration Client WMI Class](ccm_policyagent_configuration-client-wmi-class) object, the policy requests an acknowledgment. If the value is older than the value of `PolicyTimeUntilExpire`, the policy is expired.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Name of the authority to which the data applies.

`ServerCookie` Data type: `String`

Access type: Read/Write

Qualifiers: None

The last `ServerCookie` value received from the authority in a `ReplyAssignments` message.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).