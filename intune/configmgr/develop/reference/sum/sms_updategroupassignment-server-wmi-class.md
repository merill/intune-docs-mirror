---
layout: Conceptual
title: SMS_UpdateGroupAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updategroupassignment-server-wmi-class
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
description: Learn how to  represent a deployment of an update group in Configuration Manager using SMS_UpdateGroupAssignment.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: e348485c-8be8-8a8b-3ac2-4a0a4385139c
document_version_independent_id: e27ac4cf-134b-725f-f942-872dfae7d1ab
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_updategroupassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_updategroupassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_updategroupassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e4548116-c8b1-4830-af51-0593016909db
---

# SMS_UpdateGroupAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_UpdateGroupAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a deployment of an update group.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_UpdateGroupAssignment : SMS_CIAssignmentBaseClass  
{  
    Boolean ApplyToSubTargets;  
    SInt32 AssignedCIs[];  
    SInt32 AssignedUpdateGroup;  
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

The `SMS_UpdateGroupAssignment` class does not define any methods.

## Properties

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [deprecated]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignedCIs` Data type: `SInt32 Array`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignedUpdateGroup` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [not\_null]

The ID of the update group that is assigned.

`AssignmentAction` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null, enumeration, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [key, key]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentName` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignmentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`ContainsExpiredUpdates` Data type: `Boolean`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`CreationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DesiredConfigType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null, enumeration, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DisableMomAlerts` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`DPLocality` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits, not\_null, bits, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EnforcementDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`EvaluationSchedule` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`ExpirationTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

See the SMS\_CIAssignmentBaseClass Server WMI Class.

`LimitStateMessageVerbosity` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`LimitStateMessageVerbosity` is deprecated in SP1. However, the value must still remain synchronized with `StateMessageVerbosity`. For `StateMessageVerbosity` values &lt; 10, `LimitStateMessageVerbosity` must be set to `true`, otherwise `LimitStateMessageVerbosity` must be set to `false`.

This method/property has been removed or deprecated in Configuration Manager SP1.

`LocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`LogComplianceToWinEvent` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NonComplianceCriticality` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`NotifyUser` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RandomizationEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

RandomizationEnabled.

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SendDetailedNonComplianceStatus` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`StateMessagePriority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

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

Qualifiers: [bits, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UseBranchCache` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

Whether to enable the deployment to use Windows BranchCache peer technology.

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

Allow the user to interact with the deployment.

`WoLEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).