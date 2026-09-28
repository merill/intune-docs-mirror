---
layout: Conceptual
title: SMS_BaselineAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class
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
description: In Configuration Manager, the SMS_BaselineAssignment Windows Management Instrumentation class is an SMS Provider server class that contains information about how a baseline is targeted.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7d6e99fd-3027-5cae-1089-8164428d9133
document_version_independent_id: f954f55b-dd5f-f911-3f3b-2a4c61f60463
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aa6efd0a-bb13-943b-8520-89d8c75588f3
---

# SMS_BaselineAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_BaselineAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains information about how a baseline is targeted.

## Syntax

```
Class SMS_BaselineAssignment : SMS_CIAssignmentBaseClass
{
      Boolean ApplyToSubTargets;
      String AssignedCI_UniqueID;
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
      Boolean EnforcementEnabled;
      String EvaluationSchedule;
      DateTime ExpirationTime;
      DateTime LastModificationTime;
      String LastModifiedBy;
      UInt32 LocaleID;
      Boolean LogComplianceToWinEvent;
      SInt32 NonComplianceCriticality;
      Boolean NotifyUser;
      Boolean OverrideServiceWindows;
      SInt32 ParentAssignmentID;
      Boolean RaiseMomAlertsOnFailure;
      UInt32 RandomizationMinutes;
      Boolean RebootOutsideOfServiceWindows;
      Boolean SendDetailedNonComplianceStatus;
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

The `SMS_BaselineAssignment` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignedCI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

Unique identifier of the assigned baseline configuration item.

`AssignedCIs` Data type: `SInt32` Array

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null, bits]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if enforcement is enabled.

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`ParentAssignmentID` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

ParentAssignmentID

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`RandomizationMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Random time in minutes that is used when evaluating an assignment automatically once it arrives at the client. The random evaluation interval distributes the processing load when multiple assignments arrive at the client at same time.

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null, bits]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class is used to define an assignment for a configuration baseline, which is a configuration item that contains other configuration items with associated rules. The baseline is assigned to computers through collections, together with a compliance evaluation schedule.

    Your application can create a baseline as an [SMS_ConfigurationBaselineInfo Server WMI Class](sms_configurationbaselineinfo-server-wmi-class) object with the `CIType_ID` property set to Baseline (2). The types of configuration items that can be included in the baseline are:
- OperatingSystem (3)
- BusinessPolicy (4)
- Application (5)
- OtherConfigurationItem (7)

    The baseline can reference configuration items of type SoftwareUpdate (1) and SoftwareUpdateBundle (2).

    The [SMS_ConfigurationBaselineInfo Server WMI Class](sms_configurationbaselineinfo-server-wmi-class) object defines an `IsBundle` property. When building a baseline, this property of each contained configuration item is set to `true` to indicate that the configuration item is part of a bundle.

    For information on the use of this class, see [How to List Configuration Assignments](../../compliance/how-to-list-configuration-assignments) and [How to Assign Configuration Baselines](../../compliance/how-to-assign-configuration-baselines).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).