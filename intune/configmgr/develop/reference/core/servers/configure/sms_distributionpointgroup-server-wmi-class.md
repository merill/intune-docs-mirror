---
layout: Conceptual
title: SMS_DistributionPointGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointgroup-server-wmi-class
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
description: An SMS Provider server class that represents a group of distribution points rendered in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 41a2e2e5-4699-371c-f548-2089e609fdfd
document_version_independent_id: 7970c6aa-1f08-01cd-7587-e600ff487608
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointgroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_distributionpointgroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointgroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fec2ead6-0b33-54a7-2708-3eb660c98e7d
---

# SMS_DistributionPointGroup Class - Configuration Manager | Microsoft Learn

The `SMS_DistributionPointGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a group of distribution points rendered in the Configuration Manager console.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionPointGroup : SMS_BaseClass
{
    UInt32 CollectionCount;
    UInt32 ContentCount;
    Boolean ContentInSync;
    String CreatedBy;
    DateTime CreatedOn;
    String Description;
    String GroupID;
    Boolean HasMember;
    Boolean HasRelationship;
    UInt32 MemberCount;
    String ModifiedBy;
    DateTime ModifiedOn;
    String Name;
    UInt32 OutOfSyncContentCount;
    String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_DistributionPointGroup` class.

| Method | Description |
| --- | --- |
| [AddDistributionPoints Method in Class SMS_DistributionPointGroup](adddistributionpoints-method-in-class-sms_distributionpointgroup) | Adds distribution points to this distribution point group. |
| [AddPackages Method in Class SMS_DistributionPointGroup](addpackages-method-in-class-sms_distributionpointgroup) | Assigns a set of packages to the distribution point group. |
| [AssociateCollections Method in Class SMS_DistributionPointGroup](associatecollections-method-in-class-sms_distributionpointgroup) | Associates a set of collections to this distribution point group. |
| [DisassociateCollections Method in Class SMS_DistributionPointGroup](disassociatecollections-method-in-class-sms_distributionpointgroup) | Removes a set of associated collections from this distribution point group. |
| [ReDistributePackage Method in Class SMS_DistributionPointGroup](redistributepackage-method-in-class-sms_distributionpointgroup) | Redistributes a package to all of the member distribution points. |
| [RefreshDPGroup Method in Class SMS_DistributionPointGroup](refreshdpgroup-method-in-class-sms_distributionpointgroup) | Refreshes all of the member distribution points with the latest version of the targeted packages. |
| [RemoveDistributionPoints Method in Class SMS_DistributionPointGroup](removedistributionpoints-method-in-class-sms_distributionpointgroup) | Removes distribution points from this distribution point group. |
| [RemovePackages Method in Class SMS_DistributionPointGroup](removepackages-method-in-class-sms_distributionpointgroup) | Removes a set of packages from this distribution point group. |

## Properties

`CollectionCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Associated collection count.

`ContentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Associated content count.

`ContentInSync` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

Whether or not all the contents synchronized.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who created the distribution point group.

`CreatedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the distribution point group was created.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for the distribution point group.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Auto-generated unique identifier.

`HasMember` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if there is distribution point in this distribution point group.

`HasRelationship` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if there is collection associated with this distribution point group.

`MemberCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of members of this distribution point group.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the user who modified the distribution point group.

`ModifiedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the distribution point group was last modified.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, unique]

Name of this distribution point group.

`OutOfSyncContentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of out of sync content.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: [read, sizelimit("3")]

Source site for the distribution point group.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).