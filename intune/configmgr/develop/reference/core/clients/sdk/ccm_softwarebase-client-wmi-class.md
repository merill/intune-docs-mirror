---
layout: Conceptual
title: CCM_SoftwareBase Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarebase-client-wmi-class
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
description: Learn how to use the CCM_SoftwareBase class to represent the base class for management entities like software updates.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c07e536f-c59f-f0e4-d467-6101d267a6b5
document_version_independent_id: 5a2f5e2a-365f-da90-498b-b07fc8b42521
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarebase-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_softwarebase-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_softwarebase-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 999374db-2a74-7296-3364-ff3124080518
---

# CCM_SoftwareBase Class - Configuration Manager | Microsoft Learn

The `CCM_SoftwareBase` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the base class for management entities like software updates. applications and so on. This class contains the common properties across these management entities. This class is listed here for completeness and to show the base class properties which derived classes would inherit. Client SDK users will always use the specific derived classes of interest to achieve the functionality.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_SoftwareBase :
{
    UInt32 ContentSize;
    DateTime Deadline;
    String Description;
    UInt32 ErrorCode;
    UInt32 EstimatedInstallTime;
    UInt32 EvaluationState;
    String FullName;
    String Name;
    DateTime NextUserScheduledTime;
    UInt32 PercentComplete;
    String Publisher;
    UInt32 Type;
};
```

## Methods

The `CCM_SoftwareBase` class doesn't define any methods.

## Properties

`ContentSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Represents the content size. Populated only if the managed entity has binary content associated with it.

`Deadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The deadline specified by the administrator to deploy this managed entity on a client computer.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

The description of the managed entity.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Error code.

`EstimatedInstallTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

EstimatedInstallTime

`EvaluationState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Software enforcement state, such as downloading content, waiting servicewindow, and so on.

| Value | Software enforcement state | State description |
| --- | --- | --- |
| 0 | Unknown | No state information is available. |
| 1 | Enforced | Application is enforced to desired/resolved state. |
| 2 | NotRequired | Application isn't required on the client. |
| 3 | ApplicationForEnforcement | Application is available for enforcement (install or uninstall based on resolved state). Content may or may not have been downloaded. |
| 4 | EnforcementFailed | Application last failed to enforce (install/uninstall). |
| 5 | Evaluating | Application is currently waiting for content download to complete. |
| 6 | DownloadingContent | Application is currently waiting for content download to complete. |
| 7 | WaitingforDependenciesDownload | Application is currently waiting for its dependencies to download. |
| 8 | WaitingforServiceWindow | Application is currently waiting for a service window. |
| 9 | WaitingforReboot | Application is currently waiting for a previously pending reboot. |
| 10 | WaitingToEnforce | Application is currently waiting for serialized enforcement. |
| 11 | EnforcingDependencies | Application is currently enforcing dependencies. |
| 12 | Enforcing | Application is currently enforcing. |
| 13 | SoftRebootPending | Application install/uninstall enforced and a soft reboot is pending. |
| 14 | HardRebootPending | Application installed/uninstalled and a hard reboot is pending. |
| 15 | PendingUpdate | Update is available but pending installation. |
| 16 | EvaluationFailed | Application failed to evaluate. |
| 17 | WaitingUserReconnect | Application is currently waiting for an active user session to enforce. |
| 18 | WaitingforUserLogoff | Application is currently waiting for all users to sign out. |
| 19 | WaitingforUserLogon | Application is currently waiting for a user sign in. |
| 20 | InProgressWaitingRetry | Application is in progress awaiting retry. |
| 21 | WaitingforPresModeOff | Application is waiting for presentation mode to be switched off. |
| 22 | AdvanceDownloadingContent | Application is pre-downloading content (downloading outside of the install job). |
| 23 | AdvanceDependenciesDownload | Application is pre-downloading dependent content (downloading outside of the install job). |
| 24 | DownloadFailed | Application is download failed (downloading during the install job). |
| 25 | AdvanceDownloadFailed | Application is pre-downloading failed (downloading outside of the install job). |
| 26 | DownloadSuccess | Download success (downloading during the install job). |
| 27 | PostEnforceEvaluation | Post enforce evaluation. |

`FullName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The complete name of the managed entity, such as software update, application and so on.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the actual managed entity like software update, application and so on.

`NextUserScheduledTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next scheduled time when end user would like to deploy this managed entity.

`PercentComplete` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Percent complete.

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: none

The publisher that published the managed entity, such as Microsoft for software updates coming from Windows Updates.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Type.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).