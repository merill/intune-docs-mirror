---
layout: Conceptual
title: CCM_PolicyAgent_Configuration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class
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
description: A Windows Management Instrumentation class that represents the Policy Agent configuration for a given authority.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fab4772c-9e0d-bf2d-ae1e-1621ff88f38b
document_version_independent_id: 63919f92-e4af-b8c4-8d26-cce06736dbcd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5a015143-6f4c-e4b1-7118-107841181948
---

# CCM_PolicyAgent_Configuration Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CCM_PolicyAgent_Configuration` class is a client Windows Management Instrumentation (WMI) class that represents the Policy Agent configuration for a given authority.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_PolicyAgent_Configuration : CCM_Policy
{
      String AuthorityName;
      Boolean PolicyDownloadByBatch;
      String PolicyDownloadMethod;
      UInt32 PolicyDownloadsPerBatch;
      Boolean PolicyDownloadUsePeerCache;
      Boolean PolicyEnableUserAuthForAllUserPolicies;
      Boolean PolicyEnableUserGroupSupport; (Removed in SP1)
      Boolean PolicyEnableUserPolicyOnInternet;
      Boolean PolicyEnableUserPolicyPolling;
      UInt32 PolicyExpirationTimeForDefaultPerUserRequestedConfig;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      UInt32 PolicyRequestAssignmentTimeout;
      String PolicyRuleID;
      String PolicySource;
      UInt32 PolicyTimeDelayBeforeUserPolicyRefreshAtLogonOrUnlock;
      UInt32 PolicyTimeUntilAck;
      UInt32 PolicyTimeUntilExpire;
      UInt32 PolicyTimeUntilUpdateActualConfig;
      String PolicyVersion;
};
```

## Methods

The `CCM_PolicyAgent_Configuration` class does not define any methods.

## Properties

`AuthorityName` Data type: `String`

Access type: Read/Write

Qualifiers: [RealKey]

Name of the authority.

`PolicyDownloadsByBatch` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if . The default value is `true`.

`PolicyDownloadMethod` Data type: `String`

Access type: Read/Write

Qualifiers: [ToInstance ToSubClass]

Method used by the Policy Agent to download policy files. Possible values are listed below. This value can only be NULL if `PolicyRequestTarget` is NULL. This value should not be changed.

| Value | Description |
| --- | --- |
| FILECOPY | Copy policy files using standard file copy operations. Policy paths must be local or Universal Naming Convention (UNC) file paths. This value is intended for testing only. |
| HTTP | Download policy files synchronously by using direct HTTP. Policy paths must be HTTP URLs. |
| BITS | Drizzle policy files asynchronously by using the Data Transfer Service. Policy paths must be HTTP URLs. |

`PolicyDownloadsPerBatch` Data type: `UInt32`

Access type: Read/Write

Qualifiers: []

For batch policy download. The default value is 150.

`PolicyDownloadUsePeerCache` Data type: `Boolean`

Access type: Read/Write

Qualifiers: []

`true` to use peer cache.

`PolicyEnableUserAuthForAllUserPolicies` Data type: `Boolean`

Access type: Read/Write

Qualifiers: []

`true` to enable user policy polling.

`PolicyEnableUserGroupSupport` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [Not\_Null:ToInstance ToSubClass]

`true` if the Policy Agent sends user group information when requesting a user policy.

This method/property has been removed or deprecated in Configuration Manager SP1.

`PolicyEnableUserPolicyOnInternet` Data type: `Boolean`

Access type: Read/Write

Qualifiers: []

`true` to

`PolicyEnableUserPolicyPolling` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` to enable user policy polling.

`PolicyExpirationTimeForDefaultPerUserRequestedConfig` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyRequestAssignmentTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Timeout for the policy request assignment.

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

`PolicyTimeDelayBeforeUserPolicyRefreshAtLogonOrUnlock` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

PolicyTimeDelayBeforeUserPolicyRefreshAtLogonOrUnlock.

`PolicyTimeUntilAck` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The time that must elapse before the policy is acknowledged.

`PolicyTimeUntilExpire` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The number of days that the Policy Agent should wait since it last received a `ReplyAssignments` message from the authority before removing its policy. At half this time, the Policy Agent begins requesting acknowledgments. If this value is NULL, the policy never expires.

`PolicyTimeUntilUpdateActualConfig` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The time that must elapse before the actual configuration is updated.

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

See [CCM_Policy Client WMI Class](ccm_policy-client-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).