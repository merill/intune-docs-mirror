---
layout: Conceptual
title: SMS_UpdatesAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatesassignment-server-wmi-class
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
description: In Configuration Manager, the SMS_UpdatesAssignment WMI class is an SMS Provider server class that represents a deployment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 442690e1-5c0d-33e3-f47e-32fb3553109a
document_version_independent_id: 128a9db9-598a-1d11-2a3b-ebd172171962
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_updatesassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_updatesassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_updatesassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: e81354d9-8903-138d-842c-ba9d2b02f9ba
---

# SMS_UpdatesAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_UpdatesAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a deployment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UpdatesAssignment : SMS_CIAssignmentBaseClass  
{  
      Boolean ApplyToSubTargets;  
      SInt32 AssignedCIs[];  
      SInt32 AssignmentAction;  
      String AssignmentDescription;  
      SInt32 AssignmentID;  
      String AssignmentName;  
      SInt32 AssignmentType;  
      String AssignmentUniqueID;  
      Boolean ContainsExpiredUpdates;  
      DateTime CreationTime;  
      SInt32 DesiredConfigType;  
      Boolean DisableMomAlerts;  
      UInt32 DPLocality;  
      Boolean Enabled;  
      DateTime EnforcementDeadline;  
      String EvaluationSchedule;  
      DateTime ExpirationTime;  
      DateTime LastModificationTime;  
      String LastModifiedBy;  
      Boolean LimitStateMessageVerbosity; (obsolete in SP1)  
      UInt32 LocaleID;  
      Boolean LogComplianceToWinEvent;  
      SInt32 NonComplianceCriticality;  
      Boolean NotifyUser;  
      Boolean OverrideServiceWindows;  
      Boolean RaiseMomAlertsOnFailure;  
      Boolean RandomizationEnabled;  
      Boolean RebootOutsideOfServiceWindows;  
      Boolean SendDetailedNonComplianceStatus;  
      String SourceSite;  
      DateTime StartTime;  
      UInt32 StateMessagePriority;  
      UInt32 StateMessageVerbosity;  
      UInt32 SuppressReboot;  
      String TargetCollectionID;  
      Boolean UseBranchCache;  
      Boolean UseGMTTimes;  
      Boolean UserUIExperience;  
      Boolean WoLEnabled;  
};  
```

## Methods

The `SMS_UpdatesAssignment` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignedCIs` Data type: `SInt32` Array

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

For this class, the default value is APPLY (2).

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentType` Data type: `SInt32`

Access type: Read

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

For this class, the default value is REQUIRED (1).

| Value | Type |
| --- | --- |
| 1 | REQUIRED |
| 2 | NOT\_ALLOWED |

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

For this class, the `DPLocality` property defaults to the flag combination DP\_DOWNLOAD\_FROM\_LOCAL | DP\_DOWNLOAD\_FROM\_REMOTE (0x50).

`Enabled` Data type: `Boolean`

Access type: Read

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time to automatically install the software update. Set this property to zero if the update is optional. It must not be set to a null pointer.

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LimitStateMessageVerbosity` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`LimitStateMessageVerbosity` is deprecated in SP1. However, the value must still remain synchronized with `StateMessageVerbosity`. For `StateMessageVerbosity` values &lt; 10, `LimitStateMessageVerbosity` must be set to `true`, otherwise `LimitStateMessageVerbosity` must be set to `false`.

This method/property has been removed or deprecated in Configuration Manager SP1.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RandomizationEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

The post-deadline randomization delay was introduced in System Center 2012 Configuration Manager to better support virtual desktop infrastructure (VDI) environments and large-scale client deployments. The default post-deadline randomization delay is 120 minutes. Setting RandomizationEnabled to false disables the randomization delay.

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StateMessageVerbosity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Verbosity of state messages sent for this deployment.

| Value | Message verbosity |
| --- | --- |
| 0 | NONE |
| 1 | ERRORS |
| 5 | SUCCESSES |
| 10 | ALL |

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UseBranchCache` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

Use branch cache. The default value is `true`.

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` to show a reboot notification. When set to `false`, no reboot notification will be shown. The default value is `true`.

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    After preparing the software updates to deploy, your application can use this class as described in How to Configure and Deploy Updates. After the application creates the deployment, Configuration Manager creates the corresponding policy in the database. The client polls the management point for new and changed properties and the download occurs when a request is detected.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).