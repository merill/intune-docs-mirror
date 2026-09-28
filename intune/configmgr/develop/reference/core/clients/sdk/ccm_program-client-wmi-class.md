---
layout: Conceptual
title: CCM_Program Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_program-client-wmi-class
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
description: A client class, in Configuration Manager, that represents a legacy software distribution program on the client.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e70a3345-4e93-8052-8ceb-f6109c85de95
document_version_independent_id: 61fa074d-a4a0-2997-716f-c9087bdfd6d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_program-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_program-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_program-client-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 40150afe-d65c-c122-17e3-dbf775559d54
---

# CCM_Program Class - Configuration Manager | Microsoft Learn

The `CCM_Program` WMI class is a client class, in Configuration Manager, that represents a legacy software distribution program on the client.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_Program : CCM_SoftwareBase
{
     Datetime ActivationTime;
     Boolean AdvertisedDirectly;
     String Categories[];
     UInt32 CompletionAction;
     CCM_Program Dependencies[];
     String DependentPackageID;
     String DependentProgramID;
     String DiskSpaceRequired;
     UInt32 Duration;
     Datetime ExpirationTime;
     Boolean ForceDependencyToRun;
     Boolean HighImpact;
     UInt32 LastExitCode;
     String LastRunStatus;
     Datetime LastRunTime;
     UInt32 Level;
     Boolean NotifyUser;
     String PackageID;
     String PackageLanguage;
     String PackageName;
     Boolean Published;
     String ProgramID;
     String RepeatRunBehavior;
     Boolean RequiresUserInput;
     Boolean RunAtLogoff;
     Boolean RunAtLogon;
     Boolean RunDependent;
     Boolean TaskSequence;
     String Version;
};
```

## Methods

The `CCM_Program` class does not define any methods.

## Properties

`ActivationTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date and time the specified software distribution program is activated.

`AdvertisedDirectly` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program is advertised directly, otherwise, `false`.

`Categories[]` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Array of categories associated with the software distribution program.

`CompletionAction` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Controls the action Configuration Manager takes after a successful installation. The following table shows the list of possible values.

| Value | Action |
| --- | --- |
| 0 | Reboot |
| 1 | LogOff |
| 2 | ProgramReboot |
| 3 | No action |

`Dependencies[]` Data type: `CCM_Program`

Access type: Read-only

Qualifiers: [not\_null, read]

Array of software distribution program dependencies.

`DependentPackageID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the package on which the software distribution program depends.

`DependentProgramID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the program on which the specified software distribution program depends.

`DiskSpaceRequired` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Amount of disk space required.

`Duration` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Duration time of the software distribution program.

`ExpirationTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date and time the specified software distribution program expires.

`ForceDependencyToRun` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the dependent program is forced to run; otherwise, `false.`

`HighImpact` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program has a high impact, otherwise, `false`.

`LastExitCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Code value of last exit.

`LastRunStatus` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Status of the last run software distribution program.

`LastRunTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date and time that the software distribution program was last run.

`Level` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

Level of the specified software distribution program.

`NotifyUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if notifications for the software distribution program are shown to the user; otherwise, `false`.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the software distribution package.

`PackageLanguage` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Language specified in the software distribution package.

`PackageName` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Name of the software distribution package.

`Published` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program is published, otherwise, `false`.

`ProgramID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Identifier of the software distribution program.

`RepeatRunBehavior` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Response of the client when a software distribution program is run more than once on a computer. The following table shows the list of possible values.

| Value | Description |
| --- | --- |
| RerunAlways | Rerun the program regardless of previous execution condition. |
| RerunIfFail | Rerun the program if the previous attempt to run failed. If there was no previous attempt, do not run. |
| RerunIfSuccess | Rerun the program if the previous attempt to run succeeded. If there was no previous attempt, do not run. |
| RerunNever | Do not rerun the program. |

`RequiresUserInput` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if user input is required; otherwise, `false`.

`RunAtLogoff` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program runs when user logs off, otherwise, `false`.

`RunAtLogon` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program runs when user logs on, otherwise, `false`.

`RunDependent` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if software distribution program is dependent on another program, otherwise, `false`.

`TaskSequence` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

`true` if the specified software distribution program uses a task sequence, otherwise, `false`.

`Version` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Version of the software distribution program.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).