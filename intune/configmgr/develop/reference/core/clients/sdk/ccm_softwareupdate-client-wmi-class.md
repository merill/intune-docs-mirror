---
layout: Conceptual
title: CCM_SoftwareUpdate Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdate-client-wmi-class
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
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
description: Learn how enumerating the CCM_SoftwareUpdate Client WMI Class gives all the updates that are applicable and need to be installed.
locale: en-us
document_id: 5010728b-bc78-1516-58a1-b2480fc3d1c3
document_version_independent_id: c73b01dc-f2f6-fd11-cfda-c8fa7c21fc88
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdate-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_softwareupdate-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdate-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 591977c8-475b-ab9c-150c-7d9ebb41c74a
---

# CCM_SoftwareUpdate Class - Configuration Manager | Microsoft Learn

The `CCM_SoftwareUpdate` WMI class is a client class, in Configuration Manager, that represents a software update.

Enumerating this class gives all the updates that are applicable and need to be installed. You can use `GetObject` to query for an individual update based on the `UpdateID` property. Each update object has properties equivalent to the old COM interface `ICCMTargetedUpdate`. For more details on individual properties you can refer to Configuration Manager 2007 ICCMTargetedUpdate interface. We have listed here only the differences between `ICCMTargetedUpdate` and `CCM_SoftwareUpdate` classes.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from the Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
class CCM_SoftwareUpdate : CCM_SoftwareBase
{
     String ArticleID;
     String BulletinID;
     UInt32 ComplianceState;
     UInt32 ContentSize;
     Datetime Deadline
     String Description;
     UInt32 ErrorCode;
     UInt32 EvaluationState;
     Boolean ExclusiveUpdate;
     String FullName;
     Boolean IsUpgrade;
     UInt32 MaxExecutionTime;
     String Name;
     Datetime NextUserScheduledTime;
     Boolean NotifyUser;
     Boolean OverrideServiceWindows;
     UInt32 PercentComplete;
     String Publisher;
     Boolean RebootOutsideServiceWindows;
     Datetime RestartDeadline;
     Datetime StartTime;
     String UpdateID;
     String URL;
     Boolean UserUIExperience;
};
```

## Methods

The `CCM_SoftwareUpdate` class does not define any methods.

## Properties

`ArticleID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Identifier of the knowledge base article for the software update. The maximum length for this value is 64 characters.

`BulletinID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Identifier of the bulletin for security updates released by Microsoft. The maximum length for this value is 64 characters. The default value is `None`.

`ComplianceState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Compliance state of the software update that indicates if the software update is missing and needs to be installed. The `ciNotPresent` state indicates missing updates. The following table shows other possible values for the **ComplianceState** property for software updates. Only values 0, 1, and 2 are used by software update management.

| Value | State |
| --- | --- |
| 0 | ciNotPresent |
| 1 | ciPresent |
| 2 | ciPresenceUnknown (also used for not applicable) |
| 3 | ciEvaluationError |
| 4 | ciNotEvaluated |
| 5 | ciNotUpdated |
| 6 | ciNotConfigured |

`ContentSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Size of the software update content.

Note

This property is only available after the software update is downloaded into Configuration Manager cache, not before.

`Deadline` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time when the software update is installed.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Description of the software update.

`ErrorCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Error code, if any, associated with the software update.

`EvaluationState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Evaluation state of the software update. Once the **InstallUpdates** method in the `CCM_SoftwareUpdatesManager` class is called to trigger installation of software updates, the **EvaluationState**, **PercentComplete** and **ErrorCode** properties can be used to monitor update progress.

Note

The **EvaluationState** property is only meant to evaluate progress, not to find the compliance state of a software update. When a software update is not in a progress state, the value of **EvaluationState** is `none` or `available`, depending on whether there was any progress at any point in the past. This is not related to compliance state. Also, if a software update was downloaded at activation time, the value of **EvaluationState** is `none`. This value only changes once an install is attempted on the software update.

The following table shows the values for the **EvaluationState** property for software updates.

| Value | State |
| --- | --- |
| 0 | ciJobStateNone |
| 1 | ciJobStateAvailable |
| 2 | ciJobStateSubmitted |
| 3 | ciJobStateDetecting |
| 4 | ciJobStatePreDownload |
| 5 | ciJobStateDownloading |
| 6 | ciJobStateWaitInstall |
| 7 | ciJobStateInstalling |
| 8 | ciJobStatePendingSoftReboot |
| 9 | ciJobStatePendingHardReboot |
| 10 | ciJobStateWaitReboot |
| 11 | ciJobStateVerifying |
| 12 | ciJobStateInstallComplete |
| 13 | ciJobStateError |
| 14 | ciJobStateWaitServiceWindow |
| 15 | ciJobStateWaitUserLogon |
| 16 | ciJobStateWaitUserLogoff |
| 17 | ciJobStateWaitJobUserLogon |
| 18 | ciJobStateWaitUserReconnect |
| 19 | ciJobStatePendingUserLogoff |
| 20 | ciJobStatePendingUpdate |
| 21 | ciJobStateWaitingRetry |
| 22 | ciJobStateWaitPresModeOff |
| 23 | ciJobStateWaitForOrchestration |

`ExclusiveUpdate` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if software update is EXCLUSIVE; otherwise, `false`. An exclusive update cannot be installed at the same time as other updates.

`FullName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

This property is not used.

`IsUpgrade` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Indicates whether the software update is an upgrade.

`MaxExecutionTime` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Maximum time required for the software update to run.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the software update.

`NextUserScheduledTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time when a user postpones specific software updates to non-business hours (NBH). This property shows the next NBH to be used.

`NotifyUser` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if notifications for the software update are shown to the user; otherwise, `false`.

Note

If `UserUIExperience` is set to `false`, `NotifyUser` is ignored.

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the software update can be installed outside of maintenance windows; otherwise, `false`.

`PercentComplete` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Percentage of completion of the installation of the software update.

`Publisher` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Publisher of the software update.

`RebootOutsideServiceWindows` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the software update can restart outside maintenance windows; otherwise, `false`.

`RestartDeadline` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time when a computer is restarted after the installation of the software update.

`StartTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Date and time when the software update is made available to the user.

`UpdateID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Identifier of the software update.

`URL` Data type: `String`

Access type: Read-only

Qualifiers: [read]

URL for a software update.

`UserUIExperience` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if the software update is visible in software center; otherwise, `false`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).