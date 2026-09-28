---
layout: Conceptual
title: SMS_PolicyAgentConfig class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_policyagentconfig-server-wmi-class
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
description: Details of the SMS_PolicyAgentConfig server WMI class
ms.date: 2019-07-26T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0541ef1a-eb1f-c048-fb09-4cc5de9f0cab
document_version_independent_id: 2a55eb70-a48c-98a3-ddc9-8a77fea16112
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/config/sms_policyagentconfig-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/config/sms_policyagentconfig-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/config/sms_policyagentconfig-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: 257f1210-89bb-db96-61e3-e6c62e60d1e5
---

# SMS_PolicyAgentConfig class - Configuration Manager | Microsoft Learn

The `SMS_PolicyAgentConfig` WMI class is an SMS Provider server class in Configuration Manager. It represents how the client policy system is configured. These settings affect which policies are retrieved, when and how often they're retrieved, and how the client policy processing component takes action on policy updates.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_PolicyAgentConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    String PolicyDownloadMethod;
    Boolean PolicyEnableUserAuthForAllUserPolicies;
    Boolean PolicyEnableUserGroupSupport;
    Boolean PolicyEnableUserPolicyOnInternet;
    Boolean PolicyEnableUserPolicyOnTS;
    Boolean PolicyEnableUserPolicyPolling;
    UInt32 PolicyRequestAssignmentTimeout;
    UInt32 PolicyTimeDelayBeforeUserPolicyRefreshAtLogonOrUnlock;
    UInt32 PolicyTimeUntilAck;
    UInt32 PolicyTimeUntilExpire;
    UInt32 PolicyTimeUntilUpdateActualConfig;
};
```

## Methods

The `SMS_PolicyAgentConfig` class doesn't define any methods.

## Properties

### `AgentID`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Identifies the client agent component. The policy agent ID is 13.

### `PolicyDownloadMethod`

Data type: `String`

Access type: Read/Write

Qualifiers: none

Method used by the policy agent to download policy files. Possible values are listed below. This value can only be NULL if PolicyRequestTarget is NULL. This value shouldn't be changed.

| Value | Policy download method |
| --- | --- |
| FILECOPY | Copy policy files using standard file copy operations. Policy paths must be local or Universal Naming Convention (UNC) file paths. This value is intended for testing only. |
| HTTP | Download policy files synchronously by using direct HTTP. Policy paths must be HTTP URLs. |
| BITS | Drizzle policy files asynchronously by using the Data Transfer Service. Policy paths must be HTTP URLs. |

### `PolicyEnableUserAuthForAllUserPolicies`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` when the policy agent requests policies specific for users on the computer and enforces user authentication with the management point.

### `PolicyEnableUserGroupSupport`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the Policy Agent sends user group information when requesting a user policy.

### `PolicyEnableUserPolicyOnInternet`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable user policy requests from internet clients.

### `PolicyEnableUserPolicyOnTS`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Set to `true` to enable user policy on a terminal server, such as Azure Virtual Desktop. User policy is disabled by default on these devices to help client performance. If you enable this property, you accept any potential performance impact to these devices.

If PolicyEnableUserPolicyPolling is false, this property is ignored.

### `PolicyEnableUserPolicyPolling`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable user policy polling.

### `PolicyRequestAssignmentTimeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Timeout for the policy request assignment.

### `PolicyTimeDelayBeforeUserPolicyRefreshAtLogonOrUnlock`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The amount of time in milliseconds before the policy agent automatically retrieves new user policies after the user signs in or unlocks the desktop.

### `PolicyTimeUntilAck`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time that must elapse before the policy is acknowledged.

### `PolicyTimeUntilExpire`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The number of days that the policy agent should wait since it last received a ReplyAssignments message from the authority before removing its policy. At half this time, the policy agent begins requesting acknowledgments. If this value is NULL, the policy never expires.

### `PolicyTimeUntilUpdateActualConfig`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The time that must elapse before the actual configuration is updated.

## Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

## Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).