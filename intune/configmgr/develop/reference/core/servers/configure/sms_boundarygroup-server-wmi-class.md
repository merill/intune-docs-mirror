---
layout: Conceptual
title: SMS_BoundaryGroup Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class
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
description: The SMS_BoundaryGroup WMI class is an SMS Provider server class that represents a boundary group defined in the site hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 7e4446d4-3707-8d4b-171c-dcfcda601614
document_version_independent_id: 03bf742d-9c77-8106-aec5-ca647e9977f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9647c38d-f722-79b8-59f0-3fac912a1c94
---

# SMS_BoundaryGroup Class - Configuration Manager | Microsoft Learn

The `SMS_BoundaryGroup` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a boundary group defined in the site hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroup : SMS_BaseClass
{
    String CreatedBy;
    DateTime CreatedOn;
    String DefaultSiteCode;
    String Description;
    UInt64 Flags;
    UInt32 GroupID;
    UInt32 MemberCount;
    String ModifiedBy;
    DateTime ModifiedOn;
    String Name;
    Boolean Shared;
    UInt32 SiteSystemCount;
};
```

## Methods

The following table lists the methods in the `SMS_BoundaryGroup` class.

| Method | Description |
| --- | --- |
| [AddBoundary Method in Class SMS_BoundaryGroup](addboundary-method-in-class-sms_boundarygroup) | Adds boundaries to this boundary group. |
| [AddSiteSystem Method in Class SMS_BoundaryGroup](addsitesystem-method-in-class-sms_boundarygroup) | Adds a site system to this boundary group. |
| [RemoveBoundary Method in Class SMS_BoundaryGroup](removeboundary-method-in-class-sms_boundarygroup) | Removes boundaries from this boundary group. |
| [RemoveSiteSystem Method in Class SMS_BoundaryGroup](removesitesystem-method-in-class-sms_boundarygroup) | Removes site systems from this boundary group. |

## Properties

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User that created the boundary group.

`CreatedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the boundary group was created.

`DefaultSiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [sizelimit("3")]

Site code new clients will be auto assigned to.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for the boundary group.

`Flags` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Boundary group property flags.

| Value | Execution context |
| --- | --- |
| 0 | Allow peer downloads in this boundary group |
| 1 | Allow peer downloads in this boundary group **is not enabled** |
| 2 | During peer downloads, only use peers within the same subnet |
| 4 | Prefer distribution points over peers within the same subnet |
| 8 | Prefer cloud based sources over on-premises sources |

Note

These are binary flags. So multiple can be set at once. E.g. if a value of 6 is shown, then the first 3 are enabled.

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Auto-generated unique identifier for the boundary group.

`MemberCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Count of boundaries in the boundary group.

`ModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User that last modified the boundary group.

`ModifiedOn` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date the boundary group was last modified.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null, unique]

Name of the boundary group.

`Shared` Data type: `Boolean`

Access type: Read-only

Qualifiers: [read]

`true` if this boundary group was created by migration manager for a shared distribution point.

`SiteSystemCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

Site system count.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).