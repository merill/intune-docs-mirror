---
layout: Conceptual
title: SMS_Collection class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class
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
description: WMI class for collection objects.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 35f83c02-cec7-7475-ddf0-154a3ab0ceeb
document_version_independent_id: b5807287-108c-9852-b6b5-fc55353c80fd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 70232517-d112-f7b1-689d-ddc653011afa
---

# SMS_Collection class - Configuration Manager | Microsoft Learn

The `SMS_Collection` WMI class is an SMS Provider server class in Configuration Manager. It represents a collection of resources related logically by rules along with collection information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_Collection : SMS_BaseClass
{
   String CollectionID;
   SMS_CollectionRule CollectionRules[];
   UInt32 CollectionType;
   SInt32 CollectionVariablesCount;
   String Comment;
   UInt32 CurrentStatus;
   Uint32 FullEvaluationRunTime;
   Uint32 FullEvaluationMemberChanges;
   DateTime FullEvaluationMemberChangeTime;
   DateTime FullEvaluationLastRefreshTime;
   DateTime FullEvaluationNextRefreshTime;
   Boolean HasProvisionedMember;
   SInt32 IncludeExcludeCollectionsCount;
   Uint32 IncrementalEvaluationRunTime;
   Uint32 IncrementalEvaluationMemberChanges;
   DateTime IncrementalEvaluationMemberChangeTime;
   DateTime IncrementalEvaluationLastRefreshTime;
   Boolean IsBuiltIn;
   Boolean IsReferenceCollection;
   UInt8 ISVData[];
   UInt32 ISVDataSize;
   String ISVString;
   DateTime LastChangeTime;
   DateTime LastMemberChangeTime;
   DateTime LastRefreshTime;
   String LimitToCollectionID;
   String LimitToCollectionName;
   SInt32 LocalMemberCount;
   String MemberClassName;
   SInt32 MemberCount;
   UInt32 MonitoringFlags;
   String Name;
   Boolean OwnedByThisSite;
   SInt32 PowerConfigsCount;
   SMS_ScheduleToken RefreshSchedule[];
   UInt32 RefreshType;
   Boolean ReplicateToSubSites;
   SInt32 ServiceWindowsCount;
   Boolean UseCluster;
};
```

## Methods

The following methods are available in the `SMS_Collection` class:

- [AddMembershipRule method](addmembershiprule-method-in-class-sms_collection): Adds one new rule to the `CollectionRules` property of `SMS_Collection`.
- [AddMembershipRules method](addmembershiprules-method-in-class-sms_collection): Adds multiple new rules to the `CollectionRules` property of `SMS_Collection`.
- [ApproveClients method](approveclients-method-in-class-sms_collection): Approves specified client computers to join the site.
- [BlockClients method](blockclients-method-in-class-sms_collection): Blocks specified client computers from communicating with the site.
- [ChangeOwnership method](changeownership-method-in-class-sms_collection): Changes ownership of machines to a device owner.
- [ClearDeploymentLocksForCollection method](cleardeploymentlocksforcollection-method-in-class-sms_collection): Clears deployment locks for a selected collection.
- [ClearDeviceCategory method](cleardevicecategory-method-in-class-sms_collection): Clears a category from a set of devices.
- [ClearLastNBSAdvForCollection method](clearlastnbsadvforcollection-method-in-class-sms_collection): Clears the last PXE deployment for a selected collection.
- [ClearLastNBSAdvForMachines method](clearlastnbsadvformachines-method-in-class-sms_collection): Clears the last PXE deployment for selected client computers.
- [ClientEditions method](clienteditions-method-in-class-sms_collection): Retrieves a list of client editions.
- [CreateCCR method](createccr-method-in-class-sms_collection): Creates a client configuration request (CCR) for a particular resource.
- [CreateCCRs method](createccrs-method-in-class-sms_collection): Generates client configuration requests (CCRs) for the computers in the collection.
- [DeleteAllMembers method](deleteallmembers-method-in-class-sms_collection): Deletes all members, that is, resources and discovery data, for the collection.
- [DeleteMembershipRule method](deletemembershiprule-method-in-class-sms_collection): Deletes a membership rule from the collection.
- [DeleteMembershipRules method](deletemembershiprules-method-in-class-sms_collection): Deletes multiple membership rules from the collection.
- [FindResourceSite method](findresourcesite-method-in-class-sms_collection): Gets site code information for a computer from the site database.
- [FindMachineSite method](findmachinesite-method-in-class-sms_collection): Gets site code information for resources from the site database.
- [GetDependency method](getdependency-method-in-class-sms_collection): Starting in version 2010, get the collection relationship info which the input collection depends on.
- [GetDependent method](getdependent-method-in-class-sms_collection): Starting in version 2010, get the collection relationship info which depends on the input collection.
- [GetNumResults method](getnumresults-method-in-class-sms_collection): Gets a count of all members in a collection, excluding subcollections.
- [GenerateCCRByName method](generateccrbyname-method-in-class-sms_collecton): Generates a client configuration request by computer name.
- [GetTotalNumResults method](gettotalnumresults-method-in-class-sms_collection): Gets a count of all members in a collection, including subcollections.
- [ReassignClientsToSite method](reassignclientstosite-method-in-class-sms_collection): Reassigns the site for the clients in the list.
- [RequestRefresh method](requestrefresh-method-in-class-sms_collection): Triggers a re-evaluation of collection membership by the Configuration Manager collection evaluator component.
- [SetDeviceCategory method](setdevicecategory-method-in-class-sms_collection): Assigns a category to a set of devices.
- [SetMemberOrder method](setmemberorder-method-in-class-sms_collection): Sets the order of the members of a collection.
- [UpdateVisibilityInEPDashBoard method](updatevisibilityinepdashboard-in-class-sms_collection): Show this collection in the endpoint protection dashboard.
- [VerifyNoCircularDependencies method](verifynocirculardependencies-method-in-class-sms_collection): Verifies that no circular dependencies are formed if one collection is the parent of another.

## Properties

### `CollectionID`

Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

The unique autogenerated ID for this collection that contains eight characters.

The format of the collection ID is the site code that created the collection followed by a five-digit hexadecimal serial number, for example, `JAX0002C`. The default Configuration Manager collections use the prefix **SMS**, for example, `SMS00001`.

### `CollectionRules`

Data type: `SMS_CollectionRule` array

Access type: Read/Write

Qualifiers: [lazy]

SMS\_CollectionRule server WMI class objects defining the membership criteria for the collection.

### `CollectionType`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

The type of the collection. When creating or modifying collections, the collection type must be the same for all included, excluded, and limited collections. Mismatched collection types aren't allowed. 

| Value | Collection type |
| --- | --- |
| `0` | Other |
| `1` | User |
| `2` | Device |

### `CollectionVariablesCount`

Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Count of collection variables.

### `Comment`

Data type: `String`

Access type: Read/Write

Qualifiers: None

General comment or note that documents the collection.

### `CurrentStatus`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read, enumeration]

Current status of the collection. Possible values are:

| Value | Current status |
| --- | --- |
| `0` | None |
| `1` | Ready |
| `2` | Refreshing |
| `3` | Saving |
| `4` | Evaluating |
| `5` | Awaiting refresh |
| `6` | Deleting |
| `7` | Appending member |
| `8` | Querying |

### `FullEvaluationRunTime`

Data type: `Uint32`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the full evaluation run time in seconds.

### `FullEvaluationMemberChanges`

Data type: `Uint32`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the number of member changes from full evaluation.

### `FullEvaluationMemberChangeTime`

Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the last time that membership changed from full evaluation.

### `FullEvaluationLastRefreshTime`

Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the full evaluation last refresh time.

### `FullEvaluationNextRefreshTime`

Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the full evaluation next refresh time.

### `HasProvisionedMember`

Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this collection has provisioned members.

### `IncludeExcludeCollectionsCount`

Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Count of collections that are included and excluded with this one.

### `IncrementalEvaluationRunTime`

Data type: `Uint32`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the incremental evaluation run time in seconds.

### `IncrementalEvaluationMemberChanges`

Data type: `Uint32`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the number of member changes from incremental evaluation.

### `IncrementalEvaluationMemberChangeTime`

Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the last time that membership changed from incremental evaluation.

### `IncrementalEvaluationLastRefreshTime`

Data type: `Datetime`

Access type: Read-only

Qualifiers: [read]

Starting in version 2010, the incremental evaluation last refresh time.

### `IsBuiltIn`

Data type: `Boolean`

Access type: Read-Only

Qualifiers: [read]

When this value is `true`, the collection is built in. For example, **All Systems**.

### `IsReferenceCollection`

Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

When this value is `true`, the collection isn't limited by another collection.

### `ISVData`

Data type: `UInt8[]`

Access type: Read/Write

Qualifiers: [large, lazy]

A data space for partner extensibility.

### `ISVDataSize`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy]

The ISVData size.

### `ISVString`

Data type: `String`

Access type: Read/Write

Qualifiers: none

A string for partner extensibility.

### `LastChangeTime`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time of when the collection was last altered in any way.

### `LastMemberChangeTime`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time of when the collection membership was last altered.

### `LastRefreshTime`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time of when the collection membership was last refreshed.

### `LimitToCollectionID`

Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the limiting collection.

### `LimitToCollectionName`

Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The name of the limiting collection.

### `LocalMemberCount`

Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Count of members visible at the local site.

### `MemberClassName`

Data type: `String`

Access type: Read-only

Qualifiers: [read]

The name of the class that contains the members of this collection. Configuration Manager doesn't store collection members in **SMS\_Collection**. The site dynamically generates the member class name, and is derived from [SMS_CM_RES_COLL_CollectionID server WMI class](sms_cm_res_coll_collectionid-server-wmi-class).

### `MemberCount`

Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

The count of the collection members.

### `MonitoringFlags`

Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Enables the collection for certain kinds of monitoring.

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: [Not\_null]

The name of the collection. This value represents the collection in the Configuration Manager console and should be unique.

### `OwnedByThisSite`

Data type: `Boolean`

Access type: Read/Write

Qualifier: None

`true` if the collection originated at the local Configuration Manager site. The default value is `false`.

### `PowerConfigsCount`

Data type: `SInt32`

Access type: Read-only

Qualifier: [read]

A count of the power configurations.

### `RefreshSchedule`

Data type: `SMS_ScheduleToken` array

Access type: Read/Write

Qualifiers: [max(15), lazy]

[SMS_ScheduleToken server WMI class](../../servers/configure/sms_scheduletoken-server-wmi-class) objects indicating an update or refresh schedule for the collection. The site only updates collection membership if your application specifies a schedule or calls the [RequestRefresh method](requestrefresh-method-in-class-sms_collection) in the **SMS\_Collection** class. For the collection evaluator to use the schedule, set the `RefreshType` property to periodic (`2`).

### `RefreshType`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: [lazy, enumeration]

This value indicates how Configuration Manager refreshes the collection. The default value is manual (`1`). Possible values:

| Value | Refresh type |
| --- | --- |
| `1` | Manual |
| `2` | Periodic |
| `4` | Constant update |

To base the refresh on the schedule specified in `RefreshSchedule`, set this property to periodic (`2`). If you set this property to manual (`1`), manually update the collection with the [RequestRefresh method](requestrefresh-method-in-class-sms_collection).

### `ReplicateToSubSites`

This property isn't implemented.

### `ServiceWindowsCount`

Data type: `SInt32`

Access type: Read-only

Qualifiers: [read]

Count of maintenance windows for this collection.

### `UseCluster`

Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Specifies that this collection is a server group.

## Remarks

Class qualifiers for this class include:

- Secured

For more information about both the class qualifiers and the property qualifiers included in the properties section, see [Configuration Manager class and property qualifiers](../../../misc/class-and-property-qualifiers).

Collection information represented by this class includes the refresh schedule and the members, represented by [SMS_CM_RES_COLL_CollectionID server WMI class](sms_cm_res_coll_collectionid-server-wmi-class) objects. Your application can use a collection to target resources for software distribution.

When you run a query against a dynamic collection represented by `SMS_Collection`, make sure that the SMS Provider is loaded or that another method or query has already run.

The application should use the `SMS_Collection` methods to add, update, or delete membership rules defined by the `CollectionRules` property. This property isn't retrieved when your application enumerates `SMS_Collection`. To obtain the collection rules for a collection, your application must use `IWbemServices::GetObject` or `SWbemServices::Get`. For more information, see [Configuration Manager context qualifiers](../../../../core/understand/context-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).