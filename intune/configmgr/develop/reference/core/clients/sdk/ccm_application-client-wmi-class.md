---
layout: Conceptual
title: CCM_Application Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_application-client-wmi-class
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
description: In Configuration Manager, the CCM_Application Windows Management Instrumentation class is an SMS Provider server class that represents an application.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf673e20-ec66-c920-e246-bbacb0d3ccb2
document_version_independent_id: 9c23345e-ab51-4beb-0d7f-3c4d5287872d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/sdk/ccm_application-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/sdk/ccm_application-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/sdk/ccm_application-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a352c08-6f58-202b-12ed-47155c015947
---

# CCM_Application Class - Configuration Manager | Microsoft Learn

The `CCM_Application` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents an application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class CCM_Application : CCM_SoftwareBase
{
    String AllowedActions[];
    Object AppDTs[];
    String ApplicabilityState;
    String ConfigureState;
    UInt32 ContentSize;
    DateTime Deadline;
    String DeploymentReport;
    String Description;
    UInt32 EnforcePreference;
    UInt32 ErrorCode;
    UInt32 EstimatedInstallTime;
    UInt32 EvaluationState;
    String FileTypes;
    String FullName;
    String Icon;
    String Id;
    String InformativeUrl;
    String InProgressActions[];
    String InstallState;
    Boolean IsMachineTarget;
    Boolean IsPreflightOnly;
    DateTime LastEvalTime;
    DateTime LastInstallTime;
    String Name;
    DateTime NextUserScheduledTime;
    Boolean NotifyUser;
    Boolean OverrideServiceWindow;
    UInt32 PercentComplete;
    String Publisher;
    Boolean RebootOutsideServiceWindow;
    DateTime ReleaseDate;
    String ResolvedState;
    String Revision;
    String SoftwareVersion;
    DateTime StartTime;
    String SupersessionState;
    UInt32 Type;
    Boolean UserUIExperience;
};
```

## Methods

The following table lists the methods in the `CCM_Application` class.

- [Cancel Method in Class CCM_Application](cancel-method-in-class-ccm_application)
- [DownloadContents Method in Class CCM_Application](downloadcontents-method-in-class-ccm_application)
- [GetPendingComponentList Method in Class CCM_Application](getpendingcomponentlist-method-in-class-ccm_application)
- [GetProperty Method in Class CCM_Application](getproperty-method-in-class-ccm_application)
- [Install Method in Class CCM_Application](install-method-in-class-ccm_application)
- [Repair Method in Class CCM_Application](repair-method-in-class-ccm_application)
- [Uninstall Method in Class CCM_Application](uninstall-method-in-class-ccm_application)

## Properties

`AllowedActions` Data type: `String` Array

Access type: Read/Write

Qualifiers: none

Allowed actions.

`AppDTs` Data type: `CCM_AppDeploymentType` Array

Access type: Read/Write

Qualifiers: [lazy]

Application deployment types.

`ApplicabilityState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Applicability state. Possible values are:

| Value |
| --- |
| Unknown |
| Applicable |
| Not Applicable |

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

Application description.

`EnforcePreference` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [values]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | NonBusinessHours |
| 2 | AdminSchedule |

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

Evaluation state. Possible values are:

| Evaluation State Value | Description |
| --- | --- |
| 0 | No state information is available. |
| 1 | Application is enforced to desired/resolved state. |
| 2 | Application is not required on the client. |
| 3 | Application is available for enforcement (install or uninstall based on resolved state). Content may/may not have been downloaded. |
| 4 | Application last failed to enforce (install/uninstall). |
| 5 | Application is currently waiting for content download to complete. |
| 6 | Application is currently waiting for content download to complete. |
| 7 | Application is currently waiting for its dependencies to download. |
| 8 | Application is currently waiting for a service (maintenance) window. |
| 9 | Application is currently waiting for a previously pending reboot. |
| 10 | Application is currently waiting for serialized enforcement. |
| 11 | Application is currently enforcing dependencies. |
| 12 | Application is currently enforcing. |
| 13 | Application install/uninstall enforced and soft reboot is pending. |
| 14 | Application installed/uninstalled and hard reboot are pending. |
| 15 | Update is available but pending installation. |
| 16 | Application failed to evaluate. |
| 17 | Application is currently waiting for an active user session to enforce. |
| 18 | Application is currently waiting for all users to sign out. |
| 19 | Application is currently waiting for a user sign-in. |
| 20 | Application in progress, waiting for retry. |
| 21 | Application is waiting for presentation mode to be switched off. |
| 22 | Application is predownloading content (downloading outside of install job). |
| 23 | Application is predownloading dependent content (downloading outside of install job). |
| 24 | Application download failed (downloading during install job). |
| 25 | Application predownloading failed (downloading outside of install job). |
| 26 | Download success (downloading during install job). |
| 27 | Post-enforce evaluation. |
| 28 | Waiting for network connectivity. |

`FileTypes` Data type: `String`

Access type: Read/Write

Qualifiers: none

File types.

`FullName` Data type: `String`

Access type: Read/Write

Qualifiers: none

FullName

`Icon` Data type: `String`

Access type: Read/Write

Qualifiers: none

Icon.

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Application identifier.

`InformativeUrl` Data type: `String`

Access type: Read/Write

Qualifiers: none

Informative url.

`InProgressActions` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

In progress actions.

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
| NotConfigured |

`IsMachineTarget` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [key]

`true` if the application deployment is device targeted.

`IsPreflightOnly` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a simulated deployment.

`LastEvalTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last evaluation time.

`LastInstallTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last install time.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of application.

`NextUserScheduledTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next user scheduled time.

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Notify user.

`OverrideServiceWindow` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if service windows should be overridden.

`PercentComplete` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Percent complete.

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: none

Publisher.

`RebootOutsideServiceWindow` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

True if application should reboot outside service windows.

`ReleaseDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Release date.

`ResolvedState` Data type: `String`

Access type: Read/Write

Qualifiers: [values]

Resolved state.

| Value |
| --- |
| None |
| NotInstalled |
| Installed |
| Unknown |
| Any |

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Revision

`SoftwareVersion` Data type: `String`

Access type: Read/Write

Qualifiers: none

Software version.

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Start time.

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

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to show a reboot notification. When set to `false`, no reboot notification will be shown.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).