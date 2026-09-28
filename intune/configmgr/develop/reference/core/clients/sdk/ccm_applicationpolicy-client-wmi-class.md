---
layout: Conceptual
title: CCM_ApplicationPolicy Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_applicationpolicy-client-wmi-class
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
description: Learn how to represent application policy in Configuration Manager using the CCM_ApplicationPolicy class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 51c1788c-bcbe-320c-5b5d-2046d76b20a9
document_version_independent_id: 7819b2a8-5468-e7a3-b900-3fbf102452ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_applicationpolicy-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_applicationpolicy-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_applicationpolicy-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cab42812-0da3-9f43-cab1-ea7330452e63
---

# CCM_ApplicationPolicy Class - Configuration Manager | Microsoft Learn

The `CCM_ApplicationPolicy` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents application policy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_ApplicationPolicy : CCM_SoftwareBase
{
    String ApplicabilityState;
    CCM_Application Apps[];
    String ConfigureState;
    UInt32 ContentSize;
    String CurrentState;
    DateTime Deadline;
    String DeploymentReport;
    String Description;
    UInt32 ErrorCode;
    UInt32 EstimatedInstallTime;
    UInt32 EvaluationState;
    String FullName;
    String Id;
    Boolean IsMachineTarget;
    Boolean IsPreflightOnly;
    DateTime LastEvalTime;
    String Name;
    DateTime NextUserScheduledTime;
    UInt32 PercentComplete;
    String ProgressState;
    String Publisher;
    String ResolvedState;
    String Revision;
    DateTime StartTime;
    UInt32 Type;
};
```

## Methods

The following table lists the methods in the `CCM_ApplicationPolicy` class.

- [EvaluateAllPolicies Method in Class CCM_ApplicationPolicy](evaluateallpolicies-method-in-class-ccm_applicationpolicy)
- [EvaluateAppPolicy Method in Class CCM_ApplicationPolicy](evaluateapppolicy-method-in-class-ccm_applicationpolicy)
- [GetEvaluationState Method in Class CCM_ApplicationPolicy](getevaluationstate-method-in-class-ccm_applicationpolicy)

## Properties

`ApplicabilityState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Applicability state. Possible values are:

| Value |
| --- |
| Unknown |
| Applicable |
| Not Applicable |

`Apps` Data type: `CCM_Application` Array

Access type: Read/Write

Qualifiers: [lazy]

Applications.

`ConfigureState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Configure state. Possible values are:

| Value |
| --- |
| NotNeeded |
| NotConfigured |
| Configured |

`ContentSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Content size.

`CurrentState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Current state. Possible values are:

| Value |
| --- |
| NotInstalled |
| Unknown |
| Error |
| Installed |
| NotEvaluated |
| NotUpdated |
| NotConfigured |

`Deadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Deadline.

`DeploymentReport` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Deployment report.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description.

`ErrorCode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Error code.

`EstimatedInstallTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Estimated installation time.

`EvaluationState` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

EvaluationState

`FullName` Data type: `String`

Access type: Read/Write

Qualifiers: none

FullName

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier.

`IsMachineTarget` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [key]

`true` if this is a client targeted application.

`IsPreflightOnly` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a simulated deployment.

`LastEvalTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last evaluation time.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name.

`NextUserScheduledTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next user scheduled time.

`PercentComplete` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Percent complete.

`ProgressState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Progress state. Possible values are:

| Value |
| --- |
| Idle |
| EvaluationStarted |
| DownloadingDocuments |
| Evaluating |
| EvaluationFailure |
| Reporting |

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: none

Publisher.

`ResolvedState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Resolved state. Possible values are:

| Value |
| --- |
| None |
| NotInstalled |
| Installed |
| Unknown |

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Revision.

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Start time.

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