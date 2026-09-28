---
layout: Conceptual
title: SMS_CIAssignmentBaseClass Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class
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
description: The SMS_CIAssignmentBaseClass WMI class is an SMS Provider server class that serves as an abstract base class for the SMS_BaselineAssignment Server WMI Class and SMS_UpdatesAssignment Server WMI Class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a57a0fa9-1142-4797-190f-cc4f43506e12
document_version_independent_id: b71c4d38-47e9-46cd-3bc6-02be187b7422
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_ciassignmentbaseclass-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: a3d6dd15-1d0b-a561-6854-84e2494cc558
---

# SMS_CIAssignmentBaseClass Class - Configuration Manager | Microsoft Learn

The `SMS_CIAssignmentBaseClass` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that serves as an abstract base class for the [SMS_BaselineAssignment Server WMI Class](sms_baselineassignment-server-wmi-class) and [SMS_UpdatesAssignment Server WMI Class](../sum/sms_updatesassignment-server-wmi-class).

## Syntax

```
Class SMS_CIAssignmentBaseClass : SMS_BaseClass
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
      UInt32 LocaleID;
      Boolean LogComplianceToWinEvent;
      SInt32 NonComplianceCriticality;
      Boolean NotifyUser;
      Boolean OverrideServiceWindows;
      Boolean PersistOnWriteFilterDevices;
      Boolean RaiseMomAlertsOnFailure;
      Boolean RebootOutsideOfServiceWindows;
      Boolean SendDetailedNonComplianceStatus;
      Boolean SoftDeadlineEnabled;
      String SourceSite;
      DateTime StartTime;
      UInt32 StateMessagePriority;
      UInt32 SuppressReboot;
      String TargetCollectionID;
      Boolean UseGMTTimes;
      Boolean WoLEnabled;
};
```

## Methods

The `SMS_CIAssignmentBaseClass` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to apply the configuration item assignment to a subcollection.

This property is deprecated.

`AssignedCIs` Data type: `SInt32` Array

Access type: Read/Write

Qualifiers: [not\_null]

Array of IDs for the configuration items targeted by the assignment.

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Action associated with the configuration item assignment. Possible values are:

| Value | Assignment action |
| --- | --- |
| 1 | DETECT |
| 2 | APPLY |

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

The description of the configuration item assignment.

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

The ID of the configuration item assignment. This ID is unique only for the site.

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The local assignment name.

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Type of assignment. Possible values are:

| Value | Assignment type |
| --- | --- |
| 0 | CIA\_TYPE\_DCM\_BASELINE |
| 1 | CIA\_TYPE\_UPDATES |
| 2 | CIA\_TYPE\_APPLICATION |
| 5 | CIA\_TYPE\_UPDATE\_GROUP |
| 8 | CIA\_TYPE\_POLICY |

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The unique ID of the configuration item assignment. This ID is unique across sites.

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

`true` if the deployment contains one or more expired updates.

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

The date and time when the configuration item assignment is created.

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The type of the configuration item. Possible values are:

| Value | Configuration item type |
| --- | --- |
| 1 | REQUIRED |
| 2 | NOT\_ALLOWED |

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the client is configured to raise MOM alerts when a configuration item is applied. The default is `false`.

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

Flags that determine how the client obtains distribution points, according to distribution point locality. Possible values are:

4 DP\_DOWNLOAD\_FROM\_LOCAL

6 DP\_DOWNLOAD\_FROM\_REMOTE

17 DP\_NO\_FALLBACK\_UNPROTECTED

18 DP\_ALLOW\_WUMU

19 DP\_ALLOW\_METERED\_NETWORK

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if the configuration item assignment is enabled.

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time when the configuration item assignment will be enforced.

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: None

The assignment evaluation schedule.

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The date and time when the configuration item assignment expires.

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

Date and time when the configuration item assignment was last modified.

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

User who last modified the configuration item.

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

ID for the locale of the assignment name and assignment description properties.

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to log compliance status to Windows event logs. The default value is `false`.

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

The configuration item non-compliance criticality for the assignment.

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to notify the user when a configuration item is available.

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the client ignores maintenance windows when a configuration item is applied.

`PersistOnWriteFilterDevices` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if write filters on devices should be persisted. The default value is `false`.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the client raises MOM alerts if it fails to apply a configuration item. The default is `false.`

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the client reboots outside a maintenance window if a reboot is pending after applying a configuration item targeted by the assignment.

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to send a detailed non-compliance status message. The default is `false`.

`SoftDeadlineEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` to enable a soft deadline.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

The site code of the site where the assignment was created.

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

Priority of state message to be reported from client. The default value is 5.

| Value | State message priority |
| --- | --- |
| 0 | URGENT |
| 1 | HIGH |
| 5 | NORMAL |
| 10 | LOW |

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null]

The date and time when the configuration item assignment was initially offered.

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

Value indicating whether the client should not reboot the computer, if there is a reboot pending after the configuration item is applied. Possible values are:

| Value | Suppress reboot |
| --- | --- |
| 0 | SUPPRESS\_REBOOT\_WORKSTATIONS |
| 1 | SUPPRESS\_REBOOT\_SERVERS |

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

The ID of the collection to which the assignment is targeted.

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if the times and schedules are in Universal Coordinated Time (UTC).

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` to send a Wake On Lan (WoL) transmission to the client when the deadline is reached for the assignment.

## Remarks

Class qualifiers for this class include:

- Abstract

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).