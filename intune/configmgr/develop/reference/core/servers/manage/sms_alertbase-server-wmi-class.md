---
layout: Conceptual
title: SMS_AlertBase Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alertbase-server-wmi-class
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
description: Learn how to represent the base class for SMS_Alert, SMS_EPAlert, and SMS_SCHALert using SMS_AlertBase class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 84869069-c45f-4f2c-82f9-fe1441d10b8c
document_version_independent_id: 20a297df-3db5-3b95-c84b-6e185c50759a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_alertbase-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_alertbase-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_alertbase-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: ee9f43b7-eebf-63a6-1c70-eae76a5d16cd
---

# SMS_AlertBase Class - Configuration Manager | Microsoft Learn

The `SMS_AlertBase` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the base class for `SMS_Alert`, `SMS_EPAlert`, and `SMS_SCHAlert` classes.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_AlertBase : SMS_BaseClass
{
    UInt32 AlertState;
    String ClosedBy;
    String Comments;
    DateTime DateAlertStateModified;
    DateTime DateCreated;
    DateTime DateFirstActivated;
    DateTime DateLastModified;
    Boolean Deletable;
    Boolean Enabled;
    UInt32 FeatureArea;
    UInt32 FeatureGroup;
    UInt32 ID;
    String InstanceNameParam1;
    String InstanceNameParam2;
    String InstanceNameParam3;
    boolean IsIgnored;
    String LastModifiedBy;
    Boolean MonitoredByScom;
    String Name;
    UInt32 NumberOfSubscription;
    UInt32 ObjectTypeID;
    UInt32 OccurrenceCount;
    String ParameterValues;
    String RootCauseMessage;
    SInt32 RuleState;
    UInt32 Severity;
    DateTime SkipUntil;
    String SourceSiteCode;
    UInt32 TypeID;
    String TypeInstanceID;
};
```

## Methods

The `SMS_AlertBase` class doesn't define any methods.

## Properties

`AlertState` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

Current state of this alert.

| Value | Alert state |
| --- | --- |
| 0 | Active |
| 1 | Postponed |
| 2 | Canceled |
| 3 | Unknown |
| 4 | Disabled |
| 5 | Never Triggered |

`ClosedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Person who last closed alert, or 'SYSTEM' if canceled.

`Comments` Data type: `String`

Access type: Read/Write

Qualifiers: none

Administrator-supplied comments for this alert.

`DateAlertStateModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the alert state was last changed.

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the instance was created.

`DateFirstActivated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the alert was first activated.

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the alert was last changed.

`Deletable` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this alert can be deleted.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this alert is enabled. When the alert isn't enabled, the condition isn't evaluated.

`FeatureArea` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The related feature area.

`FeatureGroup` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

A feature group is a set of one or more feature areas.

| Value | Feature group |
| --- | --- |
| 1 | Administration |
| 2 | Resources |
| 3 | Deployment |
| 4 | Monitoring |
| 5 | Reporting |

`ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key, read]

Unique identifier for this instance.

`InstanceNameParam1` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The 1st parameter of the linked instance name.

`InstanceNameParam2` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The 2nd parameter of the linked instance name.

`InstanceNameParam3` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The 3rd parameter of the linked instance name.

`IsIgnored` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Whether this alert is ignored by the current user.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Person who last modified the alert.

`MonitoredByScom` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

Whether this alert is monitored by Operations Manager.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the alert.

`NumberOfSubscription` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of subscriptions to this alert.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The secured object type identifier.

`OccurrenceCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The number of times this alert has been activated.

`ParameterValues` Data type: `String`

Access type: Read/Write

Qualifiers: none

The values of administrator-defined parameters, such as thresholds. These values are stored in XML format.

`RootCauseMessage` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The root cause of the alert.

`RuleState` Data type: `SInt32`

Access type: Read-only

Qualifiers: [read, valuemap, values]

State of the underlying condition.

| Value | Rule state |
| --- | --- |
| 0 | Bad |
| 1 | Good |
| 2 | Unknown |

`Severity` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [valuemap, values]

The impact of this alert.

| Value | Severity |
| --- | --- |
| 1 | Error |
| 2 | Warning |
| 3 | Informational |

`SkipUntil` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Don't start the evaluation until the specified time.

`SourceSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

The site code of the source site. For some non-SLA alerts, NULL means it's a global SLA alert.

`TypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [not\_null]

Identifier for this type of alert.

`TypeInstanceID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User-defined identifier. The combination of `TypeID` and `TypeInstanceID` must be unique.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).