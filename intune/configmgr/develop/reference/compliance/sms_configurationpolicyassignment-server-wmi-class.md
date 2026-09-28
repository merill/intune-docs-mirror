---
layout: Conceptual
title: SMS_ConfigurationPolicyAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationpolicyassignment-server-wmi-class
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
description: Learn how to use the  SMS_ConfigurationPolicyAssignment to represent the deployment of an instance of SMS_ConfigurationPolicy in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 089d3f59-cc20-7035-643f-3d02d771cb2a
document_version_independent_id: 32d4a6d7-94f8-d381-b111-d78c824fded5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/sms_configurationpolicyassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/sms_configurationpolicyassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/sms_configurationpolicyassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 430e9106-14f5-74c7-461b-125528f08b64
---

# SMS_ConfigurationPolicyAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_ConfigurationPolicyAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the deployment of an instance of `SMS_ConfigurationPolicy`. It is similar to `SMS_BaselineAssignment`, except that `SMS_ConfigurationPolicy` is deployed directly, instead of being collected into a baseline first.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationPolicyAssignment : SMS_CIAssignmentBaseClass
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
    Boolean LimitStateMessageVerbosity;
    UInt32 LocaleID;
    Boolean LogComplianceToWinEvent;
    SInt32 NonComplianceCriticality;
    Boolean NotifyUser;
    Boolean OverrideServiceWindows;
    Boolean PersistOnWriteFilterDevices;
    Boolean RaiseMomAlertsOnFailure;
    UInt32 RandomizationMinutes;
    Boolean RebootOutsideOfServiceWindows;
    Boolean SendDetailedNonComplianceStatus;
    String SourceSite;
    DateTime StartTime;
    UInt32 StateMessagePriority;
    UInt32 StateMessageVerbosity;
    UInt32 SuppressReboot;
    String TargetCollectionID;
    Boolean UseGMTTimes;
    Boolean UserUIExperience;
    Boolean WoLEnabled;
};
```

## Methods

The `SMS_ConfigurationPolicyAssignment` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [deprecated]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignedCI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

Unique identifier of the assigned baseline configuration item.

`AssignedCIs` Data type: `SInt32 Array`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, key]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`EnforcementEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_BaselineAssignment Server WMI Class](sms_baselineassignment-server-wmi-class).

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`LimitStateMessageVerbosity` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null, obsoleted]

This method/property has been removed or deprecated in Configuration Manager SP1.

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`PersistOnWriteFilterDevices` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`RandomizationMinutes` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Random time in minutes that is used when evaluating an assignment automatically once it arrives at the client. The random evaluation interval distributes the processing load when multiple assignments arrive at the client at same time.

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`StateMessageVerbosity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [enumeration]

See [SMS_UpdateGroupAssignment Server WMI Class](../sum/sms_updategroupassignment-server-wmi-class).

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if user notification is displayed; otherwise, `false`.

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](sms_ciassignmentbaseclass-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).