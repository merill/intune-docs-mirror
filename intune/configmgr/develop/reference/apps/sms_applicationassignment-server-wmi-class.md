---
layout: Conceptual
title: SMS_ApplicationAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_applicationassignment-server-wmi-class
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
description: The SMS_ApplicationAssignment WMI class represents the assignment of an application to a collection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0204f4e1-45aa-425d-6f0c-cddb33834517
document_version_independent_id: 74acedc1-a3bb-57dd-f6fa-a124188adfb1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_applicationassignment-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_applicationassignment-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_applicationassignment-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b1e6dbc9-bbf0-43be-8d08-caa27fab7d54
---

# SMS_ApplicationAssignment Class - Configuration Manager | Microsoft Learn

The `SMS_ApplicationAssignment` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the assignment of an application to a collection.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ApplicationAssignment : SMS_CIAssignmentBaseClass
{
    String ApplicationName;
    Boolean ApplyToSubTargets;
    UInt32 AppModelID;
    String AssignedCI_UniqueID;
    SInt32 AssignedCIs[];
    SInt32 AssignmentAction;
    String AssignmentDescription;
    SInt32 AssignmentID;
    String AssignmentName;
    SInt32 AssignmentType;
    String AssignmentUniqueID;
    String CollectionName;
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
    UInt32 OfferFlags;
    SInt32 OfferTypeID;
    Boolean OverrideServiceWindows;
    SMS_ApplicationPolicyTemplateBinding PolicyBinding[];
    SInt32 Priority;
    Boolean RaiseMomAlertsOnFailure;
    Boolean RebootOutsideOfServiceWindows;
    Boolean RequireApproval;
    Boolean SendDetailedNonComplianceStatus;
    String SourceSite;
    DateTime StartTime;
    UInt32 StateMessagePriority;
    UInt32 SuppressReboot;
    String TargetCollectionID;
    DateTime UpdateDeadline;
    Boolean UpdateSupersedence;
    Boolean UseGMTTimes;
    Boolean UserUIExperience;
    Boolean WoLEnabled;
};
```

## Methods

The `SMS_ApplicationAssignment` class does not define any methods.

## Properties

`ApplicationName` Data type: `String`

Access type: Read-only

Qualifiers: [readonly]

Name of the application.

`ApplyToSubTargets` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [deprecated]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AppModelID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [readonly]

AppModelID description.

`AssignedCI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`AssignedCIs` Data type: `SInt32 Array`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

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

`CollectionName` Data type: `String`

Access type: Read-only

Qualifiers: [readonly]

Name of the collection to which the deployment was deployed.

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

Qualifiers: [bits, not\_null]

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

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

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

`OfferFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits, not\_null]

Offer flags. Possible values are:

| Value | Offer flag |
| --- | --- |
| 1 | PREDEPLOY |
| 2 | ONDEMAND |
| 4 | ENABLEPROCESSTERMINATION |
| 8 | ALLOWUSERSTOREPAIRAPP |
| 16 | RELATIVESCHEDULE |
| 32 | HIGHIMPACTDEPLOYMENT |

`OfferTypeID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null]

Type of offer. Possible values are:

| Value | Offer type |
| --- | --- |
| 0 | REQUIRED |
| 2 | AVAILABLE |

`OverrideServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`PolicyBinding` Data type: `SMS_ApplicationPolicyTemplateBinding Array`

Access type: Read/Write

Qualifiers: none

The dynamic binding of an application policy to a deployment type.

`Priority` Data type: `SInt32`

Access type: Read/Write

Qualifiers: [enumeration, not\_null]

Priority for installation of the application. Possible values are:

| Value | Installation priority |
| --- | --- |
| 0 | LOW |
| 1 | MEDIUM |
| 2 | HIGH |

`RaiseMomAlertsOnFailure` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RebootOutsideOfServiceWindows` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`RequireApproval` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if the request for this user-available assignment requires approval from the administrator.

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

`SuppressReboot` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [bits, not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`TargetCollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UpdateDeadline` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Deadline for updates.

`UpdateSupersedence` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if you should update the supersedence; otherwise, `false`.

`UseGMTTimes` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

See [SMS_CIAssignmentBaseClass Server WMI Class](../compliance/sms_ciassignmentbaseclass-server-wmi-class).

`UserUIExperience` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` if user notification is displayed; otherwise, `false`.

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