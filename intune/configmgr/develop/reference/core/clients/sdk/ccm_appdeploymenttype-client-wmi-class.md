---
layout: Conceptual
title: CCM_AppDeploymentType Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_appdeploymenttype-client-wmi-class
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
description: An SMS Provider server class that represents an application deployment type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b98fa3a2-cbfc-09bc-d668-d30cc7631fc4
document_version_independent_id: b5b429ef-b3f3-29df-a383-bea1a90ab534
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_appdeploymenttype-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_appdeploymenttype-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_appdeploymenttype-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e7faf9e3-244a-e3b9-ac2f-dfa0e1697934
---

# CCM_AppDeploymentType Class - Configuration Manager | Microsoft Learn

The `CCM_AppDeploymentType` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application deployment type.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_AppDeploymentType : CCM_SoftwareBase
{
    String AllowedActions[];
    String ApplicabilityState;
    String ConfigureState;
    UInt32 ContentSize;
    DateTime Deadline;
    Object Dependencies[];
    String DeploymentReport;
    String Description;
    UInt32 ErrorCode;
    UInt32 EstimatedInstallTime;
    UInt32 EvaluationState;
    String FullName;
    String Id;
    String InstallState;
    DateTime LastEvalTime;
    UInt32 MaxExecuteTime;
    String Name;
    DateTime NextUserScheduledTime;
    UInt32 PercentComplete;
    String PostInstallAction;
    String Publisher;
    Boolean RequiresUserInteraction;
    String ResolvedState;
    UInt32 RetriesRemaining;
    String Revision;
    String SupersessionState;
    UInt32 Type;
};
```

## Methods

The following table lists the methods in the `CCM_AppDeploymentType` class.

- [GetDeploymentTypeForUser Method in Class CCM_AppDeploymentType](getdeploymenttypeforuser-method-in-class-ccm_appdeploymenttype)
- [GetProperty Method in Class CCM_AppDeploymentType](getproperty-method-in-class-ccm_appdeploymenttype)
- [GetTargetedUsers Method in Class CCM_AppDeploymentType](gettargetedusers-method-in-class-ccm_appdeploymenttype)

## Properties

`AllowedActions` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

Allowed actions.

`ApplicabilityState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Applicability state. Possible values are:

| Value |
| --- |
| Unknown |
| Applicable |
| NotApplicable |

`ConfigureState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Configure state.

`ContentSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Content size.

`Deadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Deadline.

`Dependencies` Data type: `Object Array`

Access type: Read/Write

Qualifiers: none

Dependencies.

`DeploymentReport` Data type: `String`

Access type: Read/Write

Qualifiers: [lazy]

Deployment report.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Deployment type description.

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

Evaluation state.

`FullName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Full name.

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Identifier.

`InstallState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Installation state. Possible values are:

| Value |
| --- |
| NotInstalled |
| Unknown |
| Error |
| Installed |
| NotEvaluated |
| NotUpdated |

`LastEvalTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last evaluation time.

`MaxExecuteTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Maximum execution time.

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

`PostInstallAction` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Post installation action. Possible values are:

| Value |
| --- |
| NoAction |
| BasedOnExitCode |
| ProgramReboot |
| ForceReboot |
| ForceLogOff |

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: none

Publisher.

`RequiresUserInteraction` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Requires user interaction.

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

`RetriesRemaining` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Retries remaining.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Revision.

`SupersessionState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Supersession state. Possible values are:

| Value |
| --- |
| Unknown |
| None |
| Superseded |
| Superseding |

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